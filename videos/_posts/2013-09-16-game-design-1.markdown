---
layout: post
title: "Video: Game design 1"
---

# Video: Game design 1

Notes for this video are found below.

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/58988211?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="600" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Code for the game: Candy catch

{% highlight java %}
// your game should have:
// 1. a goal
// 2. a way to score points
// 3. increased difficulty
// 4. a way to lose

// This game is called "catch the candy."
// The idea is to move your basket left and right
// to catch falling candy.

int px = 200;
int candyy = 0;
int candyx = int(random(0, 500));
int score = 0;
int difficulty = 1;
boolean lost = false;

void setup()
{
  size(500, 500);
}

void draw()
{
  background(254, 191, 255);

  if (lost)
  {
    textSize(40);
    text("You lost.", 150, 240); 
  }
  else
  {
    // the basket
    fill(255);
    rect(px, 450, 100, 50);

    // candy falling
    if (candyy > 500)
    {
      lost = true;
    }
    candyx += int(random(-3, 3));
    ellipse(candyx, candyy, 15, 15);
    candyy += (2 * difficulty);

    if (candyx > px && candyx < (px + 100) && candyy > 450)
    {
      candyy = 0;
      candyx = int(random(0, 500));
      score++;
      if(score % 5 == 0)
      {
        difficulty++;
      }
    }
  }

  textSize(20);
  text("Score: " + score, 30, 30);
}

void keyPressed()
{
  if (key == CODED)
  {
    if (keyCode == LEFT)
    {
      px = constrain(px - 10, 0, 400);
    }
    if (keyCode == RIGHT)
    {
      px = constrain(px + 10, 0, 400);
    }
  }
}
{% endhighlight %}
