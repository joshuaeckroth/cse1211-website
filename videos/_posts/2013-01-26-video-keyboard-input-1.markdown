---
layout: post
title: "Video: Keyboard input 1"
---

# Video: Keyboard input 1

Notes for this video are found below.

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/58255940?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="600" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Complete program

{% highlight java %}
int x = 200;
int y = 200;

void setup()
{
  size(400, 400);
}

void draw()
{
  background(255);
  fill(0);
  ellipse(x, y, 50, 50);
}

void keyPressed()
{
  println(key);
  if(key == 'w') // up
  {
    y = y - 10;
  }
  if(key == 's') // down
  {
    y = y + 10;
  }
  if(key == 'a') // left
  {
    x = x - 10;
  }
  if(key == 'd') // right
  {
    x = x + 10;
  }
  
  if(key == CODED)
  {
    if(keyCode == UP)
    {
      y = y - 10;
    }
    if(keyCode == DOWN)
    {
      y = y + 10;
    }
    if(keyCode == LEFT)
    {
      x = x - 10;
    }
    if(keyCode == RIGHT)
    {
      x = x + 10;
    }
  }
}
{% endhighlight %}

