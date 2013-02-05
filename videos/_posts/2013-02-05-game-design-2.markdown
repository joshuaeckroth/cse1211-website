---
layout: post
title: "Video: Game design 2"
---

# Video: Game design 2

Notes for this video are found below.

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/58991039?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="600" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Code for the game: Touch blinky

{% highlight java %}
// This game requires the player to click one of three
// blinking squares; each correct click gives the player
// a point; an incorrect click causes the player to lose

int blinking = int(random(3));
int blinkFrames = 40;
int score = 0;
boolean lost = false;
int difficulty = 1;

void setup()
{
  size(600, 200);
}

void draw()
{
  background(0);

  noStroke();

  if (lost)
  {
    textSize(30);
    fill(255);
    text("Congratulations, you lost.", 100, 100);
  }
  else
  {
    // red
    if (blinking == 0 && frameCount % 2 == 0)
    {
      fill(255, 0, 0);
    }
    else
    {
      fill(150, 0, 0);
    }
    rect(0, 0, 200, 200);

    // green
    if (blinking == 1 && frameCount % 2 == 0)
    {
      fill(0, 255, 0);
    }
    else
    {
      fill(0, 150, 0);
    }
    rect(200, 0, 200, 200);

    // blue
    if (blinking == 2 && frameCount % 2 == 0)
    {
      fill(0, 0, 255);
    }
    else
    {
      fill(0, 0, 150);
    }
    rect(400, 0, 200, 200);

    blinkFrames--;
    if (blinkFrames == 0)
    {
      blinking = int(random(3));
      blinkFrames = (40 / difficulty);
    }
  }

  fill(255);
  textSize(22);
  text("Score: " + score, 25, 175);
}

void mouseClicked()
{
  // you clicked the red square
  if (mouseX < 200)
  {
    if (blinking == 0)
    {
      score++;
      if(score % 5 == 0)
      {
        difficulty++;
      }
    }
    else
    {
      lost = true;
    }
  }
  // you clicked the green square
  else if (mouseX < 400)
  {
    if (blinking == 1)
    {
      score++;
      if(score % 5 == 0)
      {
        difficulty++;
      }
    }
    else
    {
      lost = true;
    }
  }
  // you clicked the blue square
  else
  {
    if (blinking == 2)
    {
      score++;
      if(score % 5 == 0)
      {
        difficulty++;
      }
    }
    else
    {
      lost = true;
    }
  }
}
{% endhighlight %}



