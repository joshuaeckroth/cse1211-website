---
layout: post
title: Group project 1
due: Feb 19, 11:59pm
---

# Group project 1

Watch the videos about
[game design 1](/videos/2013-02-05-game-design-1.html) and
[game design 2](/videos/2013-02-05-game-design-2.html).

You are required to work in a group of two people. If you already have
a partner in mind, that's fine, work with that person. On Monday
(02/11) we'll find partners for people who do not yet have one. You
will both receive the same grade. You are required to make a simple
game, with the following elements:

- a goal
- keyboard and/or mouse control
- score (shown on the screen)
- difficulty levels
- a way to lose
- at least somewhat visually appealing

You cannot copy the games developed in the videos or the Tron example
below. But, you can use them as inspiration.

Finally, when you turn in the code, either in a dropbox comment or
comment in the code, specify which person was responsible for which
features. Both people should contribute equally. If there is a big
disparity in contributions, your grades will not be equal.

Only one person needs to submit the code in the dropbox.

## Example game ideas

These ideas have been implemented and can only be used for inspiration:

- tron (see below)
- candy catch (from the [game design 1](/videos/2013-02-05-game-design-1.html) video)
- touch blinky (from the [game design 2](/videos/2013-02-05-game-design-2.html) video)

You can use any of these ideas:

- dodge ball
  - throws circles and you have to dodge them
  - stay on same y position, left-right keys
  - balls fall
- snake
  - eat things, and get longer only then
- pong
- missle command
  - lines aiming randomly from top to bottom
  - shoot at some angle
  - detect if it "hits" a line
- space invaders
  - move along bottom
  - shoot alien ships
- frogger
- minesweeper
- sudoku

## Tron example

Note, score is missing in this example. Also, it seems obvious to
include a second player, who uses WASD keys to control their
movements.

{% highlight java %}
int p1x = 250; // player's x location
int p1y = 250; // player's y location
int diff = 1; // difficulty; how far the player moves each frame
int p1xc = 1; // the direction of the player's movement
int p1yc = 0; // the direction of the player's movement
int p1sw = 5; // stroke weight

void setup()
{
  size(500, 500);
  background(0);
  strokeWeight(p1sw);
  stroke(255);
  frameRate(60);
}

void draw()
{
  // check if the player hits something not black, or goes out of bounds
  
  if(get(p1x + p1sw*p1xc, p1y + p1sw*p1yc) != color(0) ||
     (p1x + p1sw*p1xc) >= 500 || (p1x + p1sw*p1xc) < 0 ||
     (p1y + p1sw*p1yc) >= 500 || (py1 + p1sw*p1yc) < 0)
  {
    // here noLoop() stops the game; you can use loop() to continue the game
    // (maybe based on a keypress)
    
    noLoop(); // there seems to be a delay with this command
    textSize(28);
    fill(255);
    text("Congratulations, you died!", 100, 200);
  }
  
  line(p1x, p1y, p1x + p1xc, p1y + p1yc);
  p1x = p1x + p1xc;
  p1y = p1y + p1yc;
  
  if(frameCount % 120 == 0)
  {
    diff++;
  }
}

void keyPressed()
{
  if(key == CODED)
  {
    if(keyCode == UP)
    {
      p1xc = 0;
      p1yc = -diff;
    }
    else if(keyCode == DOWN)
    {
      p1xc = 0;
      p1yc = diff;
    }
    else if(keyCode == LEFT)
    {
      p1xc = -diff;
      p1yc = 0;
    }
    else if(keyCode == RIGHT)
    {
      p1xc = diff;
      p1yc = 0;
    }
  }
}
{% endhighlight %}
