---
layout: post
title: Conditionals
---

# Conditionals

Sometimes, you'll want to execute some code only if a certain "test"
is true. The way we do this is with an "if" statement. For example,
this code will only print the message "I'm bigger than 5!" if the
variable `x` has a value bigger than 5:

{% highlight java %}
if(x > 5)
{
    println("I'm bigger than 5!");
}
{% endhighlight %}

You can also use an "else" which means "if the test is false," as
follows:

{% highlight java %}
if(x > 5)
{
    println("I'm bigger than 5!");
}
else
{
    println("Apparently I'm not bigger than 5...");
}
{% endhighlight %}

The "else" must appear immediately after the "if's" closing brace.

## Nested conditionals

{% highlight java %}
if(x < 5)
{
    if(x < 0)
    {
        println("x is less than 0!");
    }
    else
    {
        println("x is less than 5 but not less than 0!");
    }
}
else
{
    println("x is not less than 5!");
}
{% endhighlight %}

## Series of if/else's

It is common practice to check a series of conditions, where you only
expect one of them to be true:

{% highlight java %}
if(x == 0)
{
    // do stuff...
}
else if(x == 1)
{
    // do stuff...
}
else if(x == 2)
{
    // do stuff...
}
else
{
    // fallback...
}
{% endhighlight %}

## More examples of "tests"

More interesting conditionals may involve the following boolean
operators (assuming `p` and `q` are bool variables and `x` is an `int`
variable). Refer to the [variables and types
video](/videos/2013-09-06-variables-types-1.html).

- `!p` --- "not p" or "opposite of the value that p has"

- `p || q` --- "p or q"

- `p && q`  --- "p and q"

- `x == 5` --- "the value in the variable x is equal to 5"

- `x != 5` --- "the value in the variable x is not equal to 5"

- `x < 5`

- `x > 5`

- `x <= 5` --- "the value in the variable x is less than or equal to 5"

- `x >= 5`

- `(x >= 0) && (x <= 5)` --- "x is between 0 and 5" (x can be one of
  [0,1,2,3,4,5]); note that you cannot say (0 <= x <= 5) (wrong!)

