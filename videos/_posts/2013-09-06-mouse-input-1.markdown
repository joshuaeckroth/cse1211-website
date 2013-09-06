---
layout: post
title: "Video: Mouse input 1"
---

# Video: Mouse input 1

Notes for this video are found below.

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/58928068?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="600" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Code for demo 1: line drawing

{% highlight java %}
int linecolor = color(255, 255, 255);

void setup()
{
  size(500, 500);
  background(0);
}

void draw()
{
  stroke(linecolor);
  if(mousePressed && mouseButton == LEFT)
  {
    strokeWeight(10);
  }
  else if(mousePressed && mouseButton == RIGHT)
  {
    strokeWeight(2);
  }
  else
  {
    strokeWeight(5);
  }
  line(mouseX, mouseY, pmouseX, pmouseY);
}

void keyPressed()
{
  if(key == 'r')
  {
    linecolor = color(255, 0, 0);
  }
  if(key == 'g')
  {
    linecolor = color(0, 255, 0);
  }
  if(key == 'b')
  {
    linecolor = color(0, 0, 255);
  }
  if(key == 'w')
  {
    linecolor = color(255, 255, 255);
  }
}
{% endhighlight %}

## Code for demo 2: dragging/clicking inside a box

{% highlight java %}
int c = color(255, 0, 0);
int x = 100;
int y = 100;

void setup()
{
  size(500, 500);
}

void draw()
{
  background(0);
  fill(c);
  rect(x, y, 100, 100);  
}

void mouseClicked()
{
  if(mouseX >= x && mouseX <= (x+100) &&
     mouseY >= y && mouseY <= (y+100))
  {
    c = color(100, 0, 0);
  }
  else
  {
    c = color(255, 0, 0);
  }
}

void mouseDragged()
{
  if(mouseX >= x && mouseX <= (x+100) &&
     mouseY >= y && mouseY <= (y+100))
  {
    x = x + (mouseX - pmouseX);
    y = y + (mouseY - pmouseY);
  }
}
{% endhighlight %}



