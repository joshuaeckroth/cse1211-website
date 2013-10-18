---
layout: post
title: Test 2 Solutions
---

# Test 2 Solutions

Write a `keyPressed` function that sets `x` and `y` to 0 whenver any key except w/a/s/d is pressed.

{% highlight java %}
void keyPressed()
{
  if(key != 'w' && key != 'a' && key != 's' && key != 'w')
  {
    x = 0;
    y = 0;
  }
}
{% endhighlight %}

Write a part of the `draw` function that draws a circle centered on the mouse (diameter 10) whenever the mouse button is pressed (held down). Note that an "if" is required.

{% highlight java %}
if(mousePressed)
{
  ellipse(mouseX, mouseY, 10, 10);
}
{% endhighlight %}

What is the first and last position of this array: `int[] xyz = new int[37];` Answer: 0, 36.

Write code to define an array containing 1000 copies of the phrase "cse1211".

{% highlight java %}
String[] phrases = new String[1000];
for(int i = 0; i < 1000; i++)
{
  phrases[i] = "cse1211";
}
{% endhighlight %}

Print out each value (using the `println` function) of an integer array called `xs`. Do not create the array; assume it already exists. Use a `for` loop. Recall that you can figure out the size of the array by writing `xs.length`

{% highlight java %}
for(int i = 0; i < xs.length; i++)
{
  println(xs[i]);
}
{% endhighlight %}

Fill in the following blanks so that the `for` loop sets an integer `k` to the values 100, 99, ..., -99, -100.

{% highlight java %}
for(int k = 100; k >= -100; k--)
{% endhighlight %}

Assume we have:

- `char q;`
- `int w;`
- `int[] ws;`
- `String phrases`;
- `boolean[] rs;`
- `float x;`

What type of values are the following?

- `w` -- `int`
- `q` -- `char`
- `rs` -- `boolean` array
- `rs[0]` -- `boolean`
- `ws[w]` -- `int`
- `x` -- `float`
- `rs[ws[w]]` -- `boolean`

Write a `for` loop that computes the produce 500*495*490*...*10*5. Save the product into a variable called "prod".

{% highlight java %}
int prod = 1;
for(int x = 500; x > 0; x -= 5)
{
  prod *= x;
}

// this also works
int prod = 1;
for(int x = 500; x > 0; x--)
{
  prod *= x;
  x = x - 4;
}
{% endhighlight %}

Finish this code so that it finds the largest value in the array.

{% highlight java %}
int[] xs = new int[200];
int largest = xs[0];
for(int i = 0; i < xs.length; i++)
{
  if(xs[i] > largest)
  {
    largest = xs[i];
  }
}
{% endhighlight %}
