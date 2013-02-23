---
layout: post
title: "Video: Array utilities"
---

# Video: Array utilities

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/60322037?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="450" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Code for last example

{% highlight java %}
int[] xs;
int[] ys;

void setup()
{
  size(500, 500);

  xs = new int[20];
  ys = new int[20];

  for (int i = 0; i < 20; i++)
  {
    xs[i] = int(random(0, 500));
    ys[i] = int(random(0, 500));
  }
}

void draw()
{
  background(0);
  for (int i = 0; i < xs.length; i++)
  {
    fill(255);
    rect(xs[i], ys[i], 10, 10);
  }
}

void keyPressed()
{
  if (key == CODED)
  {
    if (keyCode == UP)
    {
      xs = expand(xs, xs.length + 1);
      ys = expand(ys, ys.length + 1);
      xs[xs.length - 1] = int(random(0, 500));
      ys[ys.length - 1] = int(random(0, 500));
    }
    if (keyCode == DOWN)
    {
      if(xs.length > 0) {
        xs = shorten(xs);
        ys = shorten(ys);
      }
    }
  }
}
{% endhighlight %}
