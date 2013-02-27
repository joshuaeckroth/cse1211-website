---
layout: post
title: "Video: Test 2 Guide Solutions"
---

# Video: Test 2 Guide Solutions

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/60606717?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="450" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Keyboard input

- Write a `keyPressed()` function that prints the message "up" when
  the up arrow key is pressed.
  
{% highlight java %}
void keyPressed()
{
  if(key == CODED)
  {
    if(keyCode == UP)
    {
      println("up");
    }
  }
}
{% endhighlight %}
  
- Write a `keyPressed()` function that prints the message "x" when the
  "x" key is pressed.
  
{% highlight java %}
void keyPressed()
{
  if(key == 'x')
  {
    println("x");
  }
}
{% endhighlight %}

- Write a `keyPressed()` function that prints the message "left" when
  either the left arrow key or "a" key is pressed.
  
{% highlight java %}
void keyPressed()
{
  if(key == 'a' || (key == CODED && keyCode == LEFT))
  {
    println("left");
  }
}
{% endhighlight %}

## Mouse input

- Write a `mouseClicked()` function that prints the message "clicked"
  whenever the left-mouse button is clicked.
  
{% highlight java %}
void mouseClicked()
{
  if(mouseButton == LEFT)
  {
    println("clicked");
  }
}
{% endhighlight %}
  
- Write a `mouseClicked()` function that prints the message "hit!"
  whenever the user clicks the mouse (any button) within a 10x10
  rectangle with top-left coordinate 50,30.
  
{% highlight java %}
void mouseClicked()
{
  if(mouseX >= 50 && mouseX <= 60 && mouseY >= 30 && mouseY <= 40)
  {
    println("hit!");
  }
}
{% endhighlight %}
  
- Suppose you are writing a `mouseDragged()` function, and want to
  allow dragging a box with position "x" and "y" (variables). What is
  the correct way to update the x-coordinate? (The y-coordinate would
  require the same update.)
  
{% highlight java %}
x = x + (mouseX - pmouseX);
{% endhighlight %}
  
- What boolean variable allows you to determine in the `draw()`
  function if the mouse is being clicked?
  
{% highlight java %}
mousePressed
{% endhighlight %}
  
- Write an `if()` block that you could use in the `draw()` function
  that prints the message "clicked" whenever the left-mouse button is
  clicked.
  
{% highlight java %}
if(mousePressed && mouseButton == LEFT)
{
  println("clicked!");
}
{% endhighlight %}

## Arrays and loops

- Write a `for()` loop that prints the message "Yo" 100 times.

{% highlight java %}
for(int time = 1; time <= 100; time++)
{
  println("Yo");
}
{% endhighlight %}

- Write a `for()` loop that finds the product
  `20*19*18*...*3*2*1`. Print the product once found.
  
{% highlight java %}
int prod = 1;
for(int n = 20; n >= 2; n--)
{
  prod = prod * n;
}

println(prod);

// note: int runs out of space and loops back to negative numbers;
// should have used the 'long' variable type
{% endhighlight %}

- Create an integer array of size 5, put some values in it, then write
  a `for()` loop that finds the sum and prints it.
  
{% highlight java %}
int[] arr = new int[5];
arr[0] = -3;
arr[1] = -1;
arr[2] = 34;
arr[3] = 4;
arr[4] = -2;

int sum = 0;
for(int i = 0; i < arr.length; i++)
{
  sum += arr[i];
}
println(sum);
{% endhighlight %}
  
- Create a float array of size 5, put some values in it, then write
  a `for()` loop that finds the minimum value and prints it.
  
{% highlight java %}
float[] arr = new float[5];
arr[0] = -3.1e14;
arr[1] = 4.2e3;
arr[2] = -3.2;
arr[3] = 0.1;
arr[4] = 0.333;

float min = arr[0];
for(int i = 0; i < arr.length; i++)
{
  if(min > arr[i])
  {
    min = arr[i];
  }
}
println(min);
{% endhighlight %}

- Create an array of names of famous people, of size 5, put some
  values in it, and print its contents in reverse.
  
{% highlight java %}
String[] names = new String[5];
names[0] = "Newton";
names[1] = "Lovelace";
names[2] = "Einstein";
names[3] = "Feynman";
names[4] = "Descartes";

// one way
for(int i = names.length - 1; i >= 0; i--)
{
  println(names[i]);
}

// another way
println(reverse(names));
{% endhighlight %}
  
- Create an array of any type, of size 5, put some values in it, then
  expand the array by adding 3 more positions, and put values in those
  new positions. Use an array function provided by Processing to do
  this.
  
{% highlight java %}
boolean[] ps = new boolean[5];
ps[0] = true;
ps[1] = false;
ps[2] = true;
ps[3] = false;
ps[4] = false;

ps = expand(ps, ps.length + 3);

ps[5] = true;
ps[6] = true;
ps[7] = true;

println(ps);
{% endhighlight %}
  
- Create two arrays of size 100, of any type (but the same
  type). Don't bother putting values in them. Then, create a new array
  that is the "concatenation" of the two (the first array followed by
  the second array). Write a loop that prints the third array's
  contents. Use an array function provided by Processing to do this.
  
{% highlight java %}
int[] arr1 = new int[100];
int[] arr2 = new int[100];

int[] arr3 = concat(arr1, arr2);

for(int i = 0; i < arr3.length; i++)
{
  println(arr3[i]);
}
{% endhighlight %}
  
- Create an array of integers, any size, don't bother putting values
  in it, then sort the array. Use an array function provided by
  Processing to do this.

{% highlight java %}
int[] arr = new int[9283];

// presumably, the array is filled with values

arr = sort(arr);

println(arr);
{% endhighlight %}

