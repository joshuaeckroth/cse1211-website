---
layout: post
title: "Test 3 Guide Solutions"
---

# Test 3 Guide Solutions

## 2D transformations

First:

{% highlight java %}
pushMatrix();
translate(450, 450);
rotate(PI/4);
rect(0, 0, 20, 100);
popMatrix();
{% endhighlight %}

Second:

{% highlight java %}
pushMatrix();
translate(270, 150);
scale(2.0);
rect(0, 0, 20, 100);
popMatrix();
{% endhighlight %}

Third:

{% highlight java %}
pushMatrix();
translate(150, 150);
for (int i = 0; i < 5; i++)
{
  pushMatrix();
  rotate(i * TWO_PI/5);
  translate(100, 0);
  rect(0, 0, 20, 100);
  popMatrix();
}
popMatrix();
{% endhighlight %}

Fourth:

{% highlight java %}
pushMatrix();
translate(150, 150);
for (int i = 0; i < 100; i++)
{
  pushMatrix();
  rotate(i * PI/8);
  translate(i * 5, 0);
  rotate(-i * PI/8);
  scale(0.2);
  rect(0, 0, 20, 100);
  popMatrix();
}
popMatrix();
{% endhighlight %}

## Object-oriented programming

> If you see this code, `Xyz abc;` you can safely assume (in this
> class) that we are using object-oriented programming. Which of `Xyz`
> and `abc` is the class? Which is the object? What's a good synonym
> for "class" (in our usage)? What's a good synonym for "object"?

`Xyz` is the class, because it is used in the position of a type (such
as `int`).

`abc` is the object.

Synonyms for classes include: type, category, classification,
template.

Synonyms for objects include: variable, instance, realization.

Referring to the class shown in the guide:

> Which message, if any, is printed when we do this: `Foo myfoo;` And
> what about this: `myfoo = new Foo();` And finally, what about this:
> `myfoo.f2();`

`Foo myfoo;` does nothing really, it just says the variable `myfoo`
has type `Foo`.

`myfoo = new Foo();` actually calls the constructor of the class,
resulting in `"A"` being printed.

`myfoo.f2();` calls the `f2()` method in the class, resulting in `"C"`
being printed.

> Which function is the constructor? Which message does the constructor
> print?

The constructor is always the function with the same name of the
class. The constructor prints `"A"` when it is called.

> Write the code necessary to declare and initialize an array of 200
> `Foo` objects (instances).

{% highlight java %}
Foo[] myfoos = new Foo[200];  // note, no objects exist yet!
for(int i = 0; i < 200; i++)
{
  myfoos[i] = new Foo();  // create one object at a time
}
{% endhighlight %}

> Write a class that enables the code above to work as described. You
> must define this class with exactly seven lines of code, the minimum
> possible (as far as I know). We count lines of code by ignoring
> blank lines and lines with only `{` or `}`, and using the normal
> coding style we have seen in this class.

{% highlight java %}
class Baz
{
  String s;
  
  Baz(String s_)
  {
    s = s_;
  }
  
  void printMany(int times)
  {
    for(int i = 0; i < times; i++)
    {
      println(s);
    }
  }
}
{% endhighlight %}

> When we are using objects, what is the most common cause of a
> "NullPointerException"?

The most common cause for us is forgetting to make an object variable
equal to a "new" instance of the class. E.g., you have:

{% highlight java %}
Foo myfoo;
{% endhighlight %}

but you forgot:

{% highlight java %}
myfoo = new Foo();
{% endhighlight %}

The program crashes (with NullPointerException error) when you attempt
to do this:

{% highlight java %}
myfoo.doSomething();
{% endhighlight %}




{% highlight %}
class Baz
{
  String name;

  Baz(String name_)
  {
    name = name_;
  }
  
  void printMany(int count)
  {
    for(int i = 0; i < count; i++)
    {
      println(name);
    }
  }
}
{% endhighlight %}

