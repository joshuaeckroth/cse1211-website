---
layout: post
title: Object-oriented programming
---

# Object-oriented programming

<!--
how we do things now

diagram with various "concerns" littered throughout the code

better design: isolation of concerns

aka separation of concerns

diagram that shows "we want to group stuff related to X here"

another aspect: common patterns, e.g., same data/actions for groups of entities

new approach: define data/actions for similar entities in just one place

then create "instances" of the template; each instance has its own values but otherwise they are all the same
-->

## Current code: no object-oriented design

![](/images/spaceships-code-pre-oo-diagram.png)

## First example: create a "Boss" class

![](/images/spaceships-code-oo-diagram-1.png)

## Anatomy of a class

![](/images/spaceships-code-oo-anatomy.png)

## Second example: add a "Player" class

![](/images/spaceships-code-oo-diagram-2.png)

## Final example: multiple enemies, all sharing the same code

![](/images/spaceships-final-oo-screenshot.png)

To run this code, download the [spaceships-data.zip](/zips/spaceships-data.zip) and unzip to your sketch folder.

{% highlight java %}
class Boss
{
  PImage img;
  int x;
  int y;

  Boss()
  {
    img = loadImage("boss1.png");
    x = 400;
    y = 100;
  }

  void drawBoss()
  {
    noSmooth();
    tint(255, 100, 100);
    image(img, x, y, 4*img.width, 4*img.height);
  }
}

class Enemy
{
  PImage img;
  int x;
  int y;
  color t;
  float sizeMult;

  Enemy(int id)
  {
    img = loadImage("enemy_" + id + ".png");
    x = int(random(0, width));
    y = int(random(0, height));
    
    // random tint for the enemy
    t = color(random(100, 256), random(100, 256), random(100, 256));
    
    // random size for the enemy
    sizeMult = random(2.0, 4.0);
  }

  void drawEnemy()
  {
    noSmooth();
    tint(t);
    image(img, x, y, sizeMult*img.width, sizeMult*img.height);
  }
  
  // our enemies are dumb; they just flutter about randomly
  void act()
  {
    x += int(random(-10, 10));
    y += int(random(-10, 10));
    
    x = constrain(x, 0, width);
    y = constrain(y, 0, height);
  }
}

class Player
{
  PImage img;
  int x;
  int y;

  Player()
  {
    img = loadImage("player_ship.png");
    x = 400;
    y = 500;
  }

  void drawPlayer()
  {
    noSmooth();
    tint(113, 100, 255);
    image(img, x, y, 3*img.width, 3*img.height);
  }

  void handleKeyPress()
  {
    if (key == CODED)
    {
      if (keyCode == UP)
      {
        y -= 5;
      }
      if (keyCode == DOWN)
      {
        y += 5;
      }
      if (keyCode == LEFT)
      {
        x -= 5;
      }
      if (keyCode == RIGHT)
      {
        x += 5;
      }
    }
  }
}

PImage bg;
Boss boss;
Enemy raphael;
Enemy donatello;
Enemy leonardo;
Enemy michelangelo;
Player player;

void setup()
{
  size(800, 600);
  imageMode(CENTER);

  bg = loadImage("moon.jpg");

  boss = new Boss();
  raphael = new Enemy(1);
  donatello = new Enemy(2);
  leonardo = new Enemy(3);
  michelangelo = new Enemy(1);
  player = new Player();
}

void draw()
{
  smooth();
  noTint();
  image(bg, width/2, height/2, 
    width, (float(width)/bg.width)*bg.height);

  boss.drawBoss();
  
  raphael.drawEnemy();
  donatello.drawEnemy();
  leonardo.drawEnemy();
  michelangelo.drawEnemy();
  
  player.drawPlayer();
  
  raphael.act();
  donatello.act();
  leonardo.act();
  michelangelo.act();
}

void keyPressed()
{
  player.handleKeyPress();
}
{% endhighlight %}
