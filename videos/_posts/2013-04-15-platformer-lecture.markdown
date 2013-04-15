---
layout: post
title: "Lecture: Platformer"
---

# Platformer

Here is a diagram of the classes. The top half of each class are
variables in the class, the bottom half are functions. The arrows from
Game to Level and Game to Player simply mean that the Game class
creates Level and Player objects and coordinates their activities.

<div style="text-align: center">
<img src="/images/platformer-diagram.png" title="Platformer class diagram" alt="Platformer class diagram" />
</div>

## Main file
{% highlight java %}
import fisica.*;

Game game;

void setup()
{
  size(1000, 500);
  Fisica.init(this);
  game = new Game();
  
  // restartLevel() creates a new level so let's just use that
  // to create the first level
  game.restartLevel();
}

void draw()
{
  background(255);
  game.update();
  game.display();
}

void keyPressed()
{
  game.handleKeyPress(key, keyCode);
}
{% endhighlight %}

## Game class
{% highlight java %}
class Game
{
  Level[] levels;
  int curLevel;
  Player player;
  
  Game()
  {
    levels = new Level[3];
    curLevel = 0;
    player = new Player();
  }
  
  void update()
  {
    // only need to update the current level
    levels[curLevel].update();
  }
  
  void display()
  {
    // spiffy window sliding effect: if player is to the right
    // of the center, shift the window to put the player in
    // the center
    
    pushMatrix();
    
    float px = player.getBody().getX();
    if(px > width/2)
    {
      translate(width/2 - px, 0);
    }
    
    // now tell the level to display itself 
    levels[curLevel].display();
    
    popMatrix();
  }
  
  /*
   Restarting a level is simple: recreate the level.
   
   Randomized levels will have new random platforms when restarted.
  */
  void restartLevel()
  {
    levels[curLevel] = new Level(curLevel);
    // tell the level to position the player in the level;
    // requires grabbing the player's "body" first, and
    // providing that to the level so it may add it to
    // the level's "world"
    levels[curLevel].setupPlayer(player.getBody());
  }
  
  /*
   The Game class handles the "r" key (restart level),
   otherwise it hands off the keypress to the Player class.
  */
  void handleKeyPress(int key, int keyCode)
  {
    if(key == 'r')
    {
      restartLevel();
    }
    else
    {
      player.handleKeyPress(key, keyCode);
    }
  }
}
{% endhighlight %}

## Level class
{% highlight java %}
class Level
{
  FWorld world;
  FBox[] platforms;
  float startingX;
  float startingY;

  Level(int num)
  {
    world = new FWorld();
    world.setGravity(0, 500);

    if (num == 0)
    {
      // The first level has four platforms
      
      platforms = new FBox[4];

      platforms[0] = new FBox(200, 50);
      platforms[0].setPosition(200, 300);
      platforms[0].setFill(0);
      platforms[0].setStatic(true);
      platforms[0].setGrabbable(false);
      world.add(platforms[0]);

      platforms[1] = new FBox(200, 50);
      platforms[1].setPosition(600, 200);
      platforms[1].setStatic(true);
      platforms[1].setGrabbable(false);
      platforms[1].setFill(0);
      world.add(platforms[1]);

      platforms[2] = new FBox(200, 50);
      platforms[2].setPosition(900, 400);
      platforms[2].setStatic(true);
      platforms[2].setGrabbable(false);
      platforms[2].setFill(0);
      world.add(platforms[2]);

      platforms[3] = new FBox(200, 50);
      platforms[3].setPosition(1100, 200);
      platforms[3].setStatic(true);
      platforms[3].setGrabbable(false);
      platforms[3].setFill(0);
      world.add(platforms[3]);

      // Start the player above the first platform (see function: setupPlayer())
      startingX = 250;
      startingY = 200;
    }
    else // num != 0, i.e., levels 2, 3, ...
    {
      // All the but first level are random. Create more platforms for later levels.
      
      // Decide how many platforms we're going to create.
      int count = int(random(3+num, 10*num));
      platforms = new FBox[count];
      for (int i = 0; i < count; i++)
      {
        platforms[i] = new FBox(200, 50);
        // Make sure we leave some space between platforms
        platforms[i].setPosition(300 * i + int(random(50)) + 150, int(random(150, 400)));
        platforms[i].setStatic(true);
        platforms[i].setGrabbable(false);
        platforms[i].setFill(0);
        world.add(platforms[i]);
      }

      // Since we have random platforms, we have to figure out where to position
      // the player so the player is above the center of the first platform.
      startingX = platforms[0].getX();
      startingY = platforms[0].getY() - 100;
    }
  }

  /*
   Just tell Fisica to do normal world updates.
  */
  void update()
  {
    world.step();
  }

  /*
   Displaying a level is as simple as drawing its world.
  */
  void display()
  {
    world.draw();
  } 

  /*
   Called by the Game class restartLevel() function.
   
   The FBody is grabbed from the player object and given to this function.
   We need the level to have access to the player "body" so that the body
   can be added to the level's world, and positioned in this world.
   */
  void setupPlayer(FBody player)
  {
    player.setPosition(startingX, startingY);
    player.setVelocity(0, 0);
    player.setForce(0, 0);
    world.add(player);
  }
}
{% endhighlight %}

## Player class
{% highlight java %}
class Player
{
  // Gotta have a Fisica "body" to put in a level's world.
  // Even though this is an FBody, any kind of FBody may
  // be used, e.g., FCircle, FBox, etc.
  FBody playerBody;

  Player()
  {
    // We'll make the player an FBox, which is a subtype of FBody;
    // other FBody subtypes can be used, e.g. FCircle
    playerBody = new FBox(50, 60);
    playerBody.setFill(255, 0, 0);
  }

  /*
   This function is used by the Game class in restartLevel().
   
   The idea is to provide the Game class the actual player body;
   the Game class naturally already has access to the Player class
   (the Game class created a Player object) but a Player object
   cannot be added to a Fisica world, only a body can.
   
   Notice this function is not "void" because it actually returns
   a value, which has type FBody. This is similar to, say, the sin()
   function, which returns a value having type float.
  */
  FBody getBody()
  {
    return playerBody;
  }

  /*
   Respond to player movement commands. For jumping (UP key),
   add an upward force under the player.
   
   Also require that the player is touching something (i.e.,
   a platform) in order to move or jump.
   
   Also require that the player is not sideways or upside down.
  */
  void handleKeyPress(int key, int keyCode)
  {
    if (playerBody.getTouching().size() > 0 && abs(playerBody.getRotation()) < PI/6)
    {
      if (key == CODED && keyCode == LEFT)
      {
        playerBody.setVelocity(-200, playerBody.getVelocityY());
      }
      if (key == CODED && keyCode == RIGHT)
      {
        playerBody.setVelocity(200, playerBody.getVelocityY());
      }
      if (key == CODED && keyCode == UP)
      {
        playerBody.addForce(0, -200000);
      }
    }
  }
}
{% endhighlight %}
