---
layout: post
title: "Video: 2D Transformations"
---

# Video: 2D Transformations

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/78667474?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="600" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

{% highlight java %}
float r = 0.0;
float r2 = 0.0;
int d = 1;
int d2 = 1;
float zoom = 1.0;

void setup()
{
  colorMode(HSB, 360, 100, 100);
  size(800, 600); // make this bigger for more fun
  rectMode(CENTER);
}

void draw()
{
  background(0);
  noStroke();

  translate(width/2, height/2);
  scale(zoom);
  rotate(r);
  for (int i = 0; i < 100; i++)
  {
    pushMatrix();
    rotate(r*i*0.5);
    translate(i*10, 0);
    scale(i*0.05);

    for (int j = 0; j < 20; j++)
    {
      pushMatrix();
      fill(i*3.6, 100, j/2.0+50);
      rotate(i*j*0.5*r2);
      translate(j*1.5+i*0.2, 0);
      ellipse(0, 0, j*0.5, j*0.5);
      popMatrix();
    }
    r2 += d2*0.000001;

    popMatrix();
  }

  r += d*0.001;
}

void keyPressed()
{
  if(key == ' ')  // change overall rotation direction
  {
    d *= -1;
  }
  if(key == 'x')  // change each spiral rotation direction
  {
    d2 *= -1;
  }
  
  if(key == '+')
  {
    zoom = zoom * 1.1;
  }
  if(key == '-')
  {
    zoom = zoom * 0.9;
  }
}
{% endhighlight %}
