---
layout: post
title: "Arrays and Hashes"
date: 2015-11-15T00:00:00-06:00
---
Arrays are a critically important concept in programming. An array can be defined as a collection of data. Much of programming involves manipulating arrays in various ways and programming languages provide a wide variety of tools for doing so.

There are many different types of arrays. Perhaps the simplest to understand is the one dimensional array which is a simple series of values. The values can be numbers or strings. Such an array can be defined in Ruby as follows: 
{% highlight ruby %}
arr = [1, 2, 3]
{% endhighlight %}   
or 
{% highlight ruby %}
arr = ["This", "is", "a", "string."]
{% endhighlight %} 
A multidimensional array is an array of arrays. This is useful for storing more complex types of data. For example: 
{% highlight ruby %}
cities = [["Chicago", "Illinois"],["New York", "New York"],["Los Angeles", California"]]
{% endhighlight %} 
One critically important variety of array is the <strong>hash</strong>. A hash or "associative array" is an array that contains unique key-value pairs. Hashes allow for programs to quickly and efficiently locate data by looking up the key for a particular value. An example of a hash in Ruby would be as follows - note Ruby differentiates hashes from arrays by the use of curly braces: 
{% highlight ruby %}
prices = { 
milk: 2.75,
coffee: 1.25, 
orange_juice: 1.50 
}
{% endhighlight %}  

Why would hashes be used over other types of arrays? As mentioned previously, hashes help computers locate data faster than other types of data structures. They are therefore very helpful for storing large amounts of data. As the size of a data structure increases, the amount of computing resources required to retrieve the structure also goes up, so anything that increases the efficiency of searching for data is very welcome.

One drawback of hashes, though, is that they require every key be unique. This makes them more difficult to use if a data set is likely to have two keys in common. In such a case it might be easier to use an array (if the data set is not too large). Otherwise, it is often possible to figure out some other kind of unique identifier that can serve as the key for the hash.

