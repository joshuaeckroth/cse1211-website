---
layout: post
title: "Lecture: Object-oriented programming"
---

# Lecture: Object-oriented programming

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/62088255?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="450" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Relevant code

Here is some code that differs from that shown in the
[object-oriented programming 1](/videos/2013-03-17-oo-1.html) video.

### Main file

{% highlight java %}
void keyPressed()
{
  // tell each ghost to consider the keypress, and possibly react
  for(int i = 0; i < ghosts.length; i++)
  {
    ghosts[i].handleKey(key, keyCode);
  } 
}
{% endhighlight %}

### Ghost "tab"

{% highlight java %}
class Ghost
{
  // ...
  
  void handleKey(int key, int keyCode)
  {
    // ...
  }
}
{% endhighlight %}

