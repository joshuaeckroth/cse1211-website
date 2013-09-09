---
layout: post
title: Test 1 Guide Solutions
---

# Test 1 Guide Solutions

## Coordinate system and shapes

{% highlight java %}
// code to draw a 4x4 square in the middle of a 50x50 window
rect(22, 22, 4, 4);

// code to draw a 4x4 square in the middle of a window of any size
rect(width/2 - 2, height/2 - 2, 4, 4);

// code to draw an ellipse that touches the four edges of a window of any size
ellipse(width/2, height/2, width, height);

// code to draw a rectangle that covers the entire window (and no more)
rect(0, 0, width, height);
{% endhighlight %}

## Color

{% highlight java %}
// code to set the fill color to white or black or very-light-gray
fill(255); // white
fill(0); // black
fill(220); // light gray

// code to set the fill color to 50% transparent dark red
fill(150, 0, 0, 128);

// code to set the background color to bright yellow or purple or cyan
background(255, 255, 0); // yellow
background(255, 0, 255); // purple (magenta)
background(0, 255, 255); // cyan
{% endhighlight %}

## Variables and types

- what type should be used to hold the value 55 (not 55.0)? **int**
- what type should be used to hold the value 55.5? **float** (or **double**)
- what type should be used to hold the value "foo bar" **String** (capitalization matters)
- what type should be used to hold the value of a single symbol that can be typed on the keyboard? **char**
- what type should be used to hold the value true or false? **boolean**

What is the result of each of the following computations?

{% highlight java %}
55 % 10       // 5
55 / 10       // 5
2.4 / 2.0     // 1.2
pow(2.0, 2.0) // 4.0
{% endhighlight %}

If we have `int x = 5`, what is the value of `x` after each of these commands:

{% highlight java %}
x--;     // now x == 4
x--;     // now x == 3
x *= 2;  // now x == 6
x++;     // now x == 7
{% endhighlight %}

If we have `boolean q = true`, what is the value of `q` after each of these commands:

{% highlight java %}
q = false;      // now q == false
q = true || q;  // now q == true
q = !q;         // now q == false
{% endhighlight %}

## Animation

The right chunk of code properly moves the triangle left-to-right, since it increases `x`. The left chunk decreases `x`, so it moves right-to-left, which is wrong.

{% highlight java %}
int bigness = 200;  // I can choose a different name and initial value

void setup()
{
    size(400, 400);
}

void draw()
{
    background(255);
    ellipse(50, 100, bigness, bigness + 100); // I can make it a circle or whatever
    
    bigness = bigness - 50;  // just has to decrease somehow
}
{% endhighlight %}