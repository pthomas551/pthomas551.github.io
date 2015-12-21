---
layout: post
title: "Ruby: The Sort Method"
date: 2015-11-21T00:00:00-06:00
---
Ruby contains many powerful tools for the manipulation of data. Many of these tools are available through the Enumerable module, which is available for arrays, hashes, and other objects where an enumerator is defined.

An especially powerful enumerable method is the <em>sort</em> method. This method allows for the efficient sorting of data within a data structure. For example, let us suppose we have an array as follows:
{% highlight ruby %}
irb(main):001:0> arsenal_players = ['Per Mertesacker', 'Mesut Ozil', 'Petr Cech', 'Theo Walcott']
=> ["Per Mertesacker", "Mesut Ozil", "Petr Cech", "Theo Walcott"]
{% endhighlight %}

Calling <em>sort</em> on this array without an argument will default to returning a new array of the previous array sorted by alphabetical order (or numeric order in the case of an array of numbers):
{% highlight ruby %}
irb(main):002:0> arsenal_players.sort<br/>
=> ["Mesut Ozil", "Per Mertesacker", "Petr Cech", "Theo Walcott"]
{% endhighlight %}

Of course <em>sort</em> also has a destructive method, accessible by <em>sort</em>!:
{% highlight ruby %}
irb(main):004:0> arsenal_players.sort!<br/>
=> ["Mesut Ozil", "Per Mertesacker", "Petr Cech", "Theo Walcott"]<br/>
irb(main):005:0> arsenal_players<br/>
=> ["Mesut Ozil", "Per Mertesacker", "Petr Cech", "Theo Walcott"]
{% endhighlight %}
The great thing about <em>sort</em> is that you can change the sort logic. You can do this using the <em>combined comparison operator</em> which is <code><=></code>, also known as the "spaceship operator." Let's see the spaceship in action:
{% highlight ruby %}
irb(main):006:0> arsenal_players.sort { |a,b| b <=> a }<br/>
=> ["Theo Walcott", "Petr Cech", "Per Mertesacker", "Mesut Ozil"]
{% endhighlight %}
The <code>{ |a,b| b <=> a }</code> argument told <em>sort</em> to re-sort arsenal_players in reverse alphabetical order; <code>b <=> a</code> told <em>sort</em> to iterate through the array using its usual logic but instead of putting item a before item b as it usually would, instead put b before a.

You can find much more information about customizing the <em>sort</em> method at <a href="http://www.evc-cit.info/cit020/beginning-programming/chp_07/custom_sort.html">this link.</a>


