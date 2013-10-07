---
layout: post
title: Test 2 Guide Solutions
---

# Test 2 Guide Solutions

## Keyboard input

Write code that you would put in place of the `...` to make the following `if` work (i.e., so the message is printed at the right times):

{% highlight java %}
void keyPressed()
{
  if(...)
  {
    println("You pressed the 'w' key!");
  }
}
{% endhighlight %}

**Answer:**


{% highlight java %}
void keyPressed()
{
  if(key == 'w')
  {
    println("You pressed the 'w' key!");
  }
}
{% endhighlight %}

Write a `keyPressed()` function that prints the message "Invalid key", using `println()` as above, whenever a key other than `w`, `a`, `s`, or `d` is pressed.

**Answer:**

{% highlight java %}
void keyPressed()
{
  if(key != 'w' && key != 'a' && key != 's' && key != 'd')
  {
    println("Invalid key");
  }
}
{% endhighlight %}

You should be able to see that this will not work correctly:

{% highlight java %}
if(key != 'w' || key != 'a' || key != 's' || key != 'd')
{% endhighlight %}

## Mouse input

Write code for the `...` that draws a circle (diameter 10) centered on the mouse pointer (so that the circle follows the mouse):

{% highlight java %}
void draw()
{
  ellipse(...);
}
{% endhighlight %}

**Answer:**

{% highlight java %}
void draw()
{
  ellipse(mouseX, mouseY, 10, 10);
}
{% endhighlight %}

Finish this code so that the integer variables `x` and `y` are both set to `0` when a mouse button is clicked anywhere inside the top-left quarter (quadrant) of the screen:

{% highlight java %}
void mouseClicked()
{
  ...
}
{% endhighlight %}

**Answer:**

{% highlight java %}
void mouseClicked()
{
  if(mouseX < width/2 && mouseY < height/2)
  {
    x = 0;
    y = 0;
  }
}
{% endhighlight %}

## Arrays

Suppose we have an array with 97 values. What is the first array "position" or "index"? What is the last index?

**Answer:** first is `0`, last is `96`

Know how types (`int`, `float`, `String`, etc.) work with arrays. Specifically, suppose we have this code:

{% highlight java %}
int j;
String s;
float[] ww;
String[] t;
float r;
int[] z;
{% endhighlight %}

You might see questions like the following. Note that we can answer these questions even though we don't know which *values* any of these variables contain or how many values are in the arrays.

- What type is `s`? **Answer:** `String`
- What type is `t`? **Answer:** `String` array
- What type is `r`? **Answer:** `float`
- What type is `t[0]`? **Answer:** `String`
- What type is `t[j]`? **Answer:** `String`
- What type is `ww[3]`? **Answer:** `float`
- What type is `ww`? **Answer:** `float` array
- What type is `ww[j]`? **Answer:** `float`
- What type is `z`? **Answer:** `int` array
- What type is `ww[z[0]]`? **Answer**: `float`
- What type is `ww[z[j]]`? **Answer**: `float`

Suppose I want to create an array of 1000 `float` values. Write the necessary code to define such an array with the name `myvals` and set all the values in the array to `12.55`.

**Answer:**

{% highlight java %}
float[] myvals = new float[1000];
for(int i = 0; i < 1000; i++)
{
  myvals[i] = 12.55;
}
{% endhighlight %}

Write code that creates an array of 2000 integers, called `oddeven`, and sets the values in "even" array positions (0, 2, ...) to `1` and "odd" array positions (1, 3, ...) to `0`. For example, `oddeven[18]` is `1` and `oddeven[19]` is `0`. (Note that you can determine if a number is even by checking if its remainder, after dividing by 2, is equal to 0.)

**Answer:**

{% highlight java %}
int[] oddeven = new int[2000];
for(int i = 0; i < 2000; i++)
{
  if(i % 2 == 0) // even
  {
    oddeven[i] = 1;
  }
  else // odd
  {
    oddeven[i] = 0;
  }
}
{% endhighlight %}

## Loops

Write a `for` loop that draws 100 ellipses (I don't care about the dimensions or locations of the ellipses).

**Answer:**

{% highlight java %}
for(int q = 100; q < 200; q++) // just to be cute
{
  ellipse(0, 0, 1, 1); // again, just to be cute
}
{% endhighlight %}

What is the value of `sum` after this loop is finished?

{% highlight java %}
int sum = 0;
for(int q = -5; q < 10; q--)
{
  sum += q;
  q = q + 3;
}
{% endhighlight %}

**Answer:**

I'm going to show each value of `sum`. But only the final value is the answer.

    First, sum == 0.
    Now q == -5. It is less than 10. The loop starts.
    sum changes to -5.
    q changes to -2.
    q-- happens, so now q is -3.
    q is still less than 10. The loop continues.
    sum changes to -8.
    q changes to 0.
    q-- happens, so now q is -1.
    q is still less than 10. The loop continues.
    sum changes to -9.
    q changes to 2.
    q-- happens, so now q is 1.
    q is still less than 10. The loop continues.
    sum changes to -8.
    q changes to 4.
    q-- happens, so now q is 3.
    q is still less than 10. The loop continues.
    sum changes to -5.
    q changes to 6.
    q-- happens, so now q is 5.
    q is still less than 10. The loop continues.
    sum changes to 0.
    q changes to 8.
    q-- happens, so now q is 7.
    q is still less than 10. The loop continues.
    sum changes to 7.
    q changes to 10.
    q-- happens, so now q is 9.
    q is still less than 10. The loop continues.
    sum changes to 16.
    q changes to 12.
    q-- happens, so now q is 11.
    q is not less than 10, so the loop stops.

    The final value of sum is 16.
