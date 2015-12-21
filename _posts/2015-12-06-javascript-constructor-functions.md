---
layout: post
title: "JavaScript Constructor Functions"
date: 2015-12-06T00:00:00-06:00
---
<em>This post builds on my previous <a href="{% post_url 2015-11-29-classes-in-ruby %}">post on Ruby classes</a></em>.

As I mentioned in my post on Ruby classes, in object-oriented programming, <strong>classes</strong> are essentially templates for creating new objects. One way in which classes are very useful is that they allow you to create easily understanable representations of real-world objects in code.

Ruby has the built-in <strong>class</strong> object for creating classes. JavaScript does not have a class object like Ruby, but it does have a special type of function called a <strong>constructor function</strong>, which replicates the function and features of the <strong>class</strong> object. In this post we will do a quick review of Ruby class creation syntax, and then take a look at how we can replicate this using a JavaScript constructor function.

Let's review the Ruby class syntax first for comparison purposes. This is some possible syntax for a <em>Car</em> object in Ruby. You can go to the <a href="{% post_url 2015-11-29-classes-in-ruby %}">previous post</a> for an overview of how this syntax works.
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

As you can see, there is not a great deal of difference between Ruby classes and JavaScript constructor functions. Perhaps the most important difference as laid out in this example is that in JS, instance attributes have read/write methods endowed on them by default; they do not need to be separately defined in the constructor function.

In short, even if the syntax is not quite as intuitive, JS constructors offer similar capabilities to Ruby in the area of class definitions; in fact, they are even more efficient when it comes to creating methods for accessing instance variables.


