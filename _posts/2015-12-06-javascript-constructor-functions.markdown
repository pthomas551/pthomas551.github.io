---
layout: post
title: "JavaScript Constructor Functions"
date: 2015-12-06T00:00:00-06:00
---
<em>This post builds on my previous <a href="{% post_url 2015-11-29-classes-in-ruby %}">post on Ruby classes</a></em>.

As I mentioned in my [post on Ruby classes]({% post_url 2015-11-29-classes-in-ruby %}), in object-oriented programming, <strong>classes</strong> are essentially templates for creating new objects. One way in which classes are very useful is that they allow you to create easily understandable representations of real-world objects in code.

Ruby has the built-in <strong>class</strong> object for creating classes. JavaScript also has classes in newer versions but it often uses a special type of function called a <strong>constructor function</strong>, which replicates many of the function and features of a class (and is also used in building out JS classes.) In practice constructors are frequently preferred instead of classes because older codebases use them and browser support for newer versions of JS can be inconsistent.

In this post we will do a quick review of Ruby class creation syntax, and then take a look at how we can replicate this using a JavaScript constructor function.

Let's review the Ruby class declaration syntax first for comparison purposes. This is some possible syntax for a <em>Car</em> object in Ruby. You can go to the <a href="{% post_url 2015-11-29-classes-in-ruby %}">previous post</a> for an overview of how this syntax works.

{% highlight javascript %}
class Car
attr_reader :make
attr_reader :model
attr_reader :year
def initialize(make, model, year)
@make = make
@model = model
@year = year
end
end
{% endhighlight %}

Now let's look at how we would create a slightly different object, say a US state object, using a JS constructor function:

{% highlight javascript %}
function State(name, population, foundedYear) {
this.name = name;
this.population = population;
this.foundedYear = foundedYear;
}
{% endhighlight %}

This constructor created a State object with three instance variables; name, population, and year of foundation. As you can see, we did not define instance methods to access these variables; this is not necessary in JS, as we will demonstrate below. First, though, let's go over how to create a new object from this constructor template:

{% highlight javascript %}
var illinois = new State('Illinois', 12880580, 1818);
{% endhighlight %}

This code created a new State object called illinois with the three attributes of the constructor function contained in order within the parentheses. As you can see the syntax is very similar to creating new instances of a class in Ruby. The syntax for calling these instance attributes is very similar as well:

{% highlight javascript %}
> illinois.name;
'Illinois'
> illinois.population;
12880580
> illinois.foundedYear;
1818
{% endhighlight %}

The main difference between this example and our Ruby example in the previous post is that we did not need to create methods for accessing these variables as we had to in Ruby.

Let's put this all together by creating a class in JS:

{% highlight javascript %}
class State {
  constructor(name, population, foundedYear) {
    this.name = name;
    this.population = population;
    this.foundedYear = foundedYear;
  }
// class instance methods as desired
}
{% endhighlight %}

There is not much functional difference between this and simply defining a constructor function; in fact, classes in JS are simply *syntactic sugar* for JS's pre-existing inheritance model - ie. they are put in to make life easier for those coming from languages that use classes, but in the background they translate to constructor functions and prototypes. (Prototypes are beyond the scope of this article but are similar to class instance methods in class-based languages.)

As you can see, there is not a great deal of difference between Ruby class declarations and JavaScript constructor functions. Perhaps the most important difference as laid out in this example is that in JS, instance attributes have read/write methods endowed on them by default; they do not need to be separately defined in the constructor function.

In short, even if the syntax is not quite as intuitive, JS constructors offer similar capabilities to Ruby in the area of class definitions; in fact, they are even more efficient when it comes to creating methods for accessing instance variables.


