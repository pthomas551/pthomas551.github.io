---
layout: post
title: "Classes in Ruby"
date: 2015-11-29T00:00:00-06:00
---
In object-oriented programming, <strong>classes</strong> are essentially templates for creating new objects. They allow you to describe the basic attributes that members of a class should have, and enable you to establish modes of interaction for the class.

One way in which classes are very useful is that they allow you to create easily understandable representations of real-world objects in code. Let's take the example of a car. Here is how you would initialize a <em>Car</em> object in Ruby:

{% highlight ruby %}
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

What does this code do? It sets up a template for a car that we can then reuse. Our <strong>initialize</strong> method set up the required attributes for the car - make, model, and year. The <strong>attr_reader</strong> statement allows for quick and easy creation of methods for accessing these attributes of the car.

What was putting @ before the variable names all about, though? We were creating <strong>instance variables</strong> for the car object. Instance variables are stored in each individual instance of the object, so you can recall them every time you recall that object. If we kept them as <strong>local</strong> variables - without the @ - we would lose their values as soon as the initialize method finished, which wouldn't be very useful! Okay, let's see how we can interact with this <em>Car</em> object in practice after entering the code above:

{% highlight ruby %}
irb(main):011:0> my_miata = Car.new('Mazda', 'Miata', 2009)
=> #Car:0x007fcd531123a8 @make="Mazda", @model="Miata", @year=2009
{% endhighlight %}

What did this do? We created a new instance of the <em>Car</em> object and gave it a make (Mazda), model (Miata), and year (2009). Now we can use our attr_reader methods to look up these attributes of the car:

{% highlight ruby %}
irb(main):012:0> my_miata.make
=> "Mazda"
irb(main):013:0> my_miata.model
=> "Miata"
irb(main):014:0> my_miata.year
=> 2009
{% endhighlight %}

This kind of basic data initialization, storage, and retrieval is just scratching the surface of what you can do with objects. You can define methods for interaction with objects - think of things like turning the car on or off:

{% highlight ruby %}
class Car
  def turn_on
    @on = true
  end

  def turn_off
    @on = false
  end
end
{% endhighlight %}

or changing some kind of control on the car:

{% highlight ruby %}
class Car
attr_accessor :wipers_setting
end
{% endhighlight %}

As you can see, classes are an extremely powerful feature of Ruby and many other programming languages.