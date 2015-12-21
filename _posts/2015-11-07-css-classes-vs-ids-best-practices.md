---
layout: post
title: "CSS Classes vs. ID's: Best Practices"
date: 2015-11-07T00:00:00-06:00
---
CSS offers a number of options for designating web page sections that will receive formatting from a CSS stylesheet. These options are known as "selectors" in the parlance of CSS. Two popular selector options are classes and ID's. These allow the user to apply formatting to specific sections of the page that differ from the default settings that may exist elsewhere in the stylesheet. This blog post will review some best practices for using class and ID selectors.

An ID selector designates one section of an HTML document that will receive formatting from the CSS stylesheet. ID's must be unique to that section of the document; they cannot be reused elsewhere in the file. An ID can be designated in HTML as follows:

    {% highlight html %}
<span id="id-name"> ID content </span>
    {% endhighlight %}
The ID is then selected in the CSS stylesheet as follows:
{% highlight css %}
#id-name {
insert formatting here
}
{% endhighlight %}
ID's may seem unappealing compared to classes, which can be reused across multiple sections of the page. Classes are designated very similarly to ID's:
{% highlight html %}
<span class="class-name"> Class content </span>
{% endhighlight %}

The class is then selected in the CSS stylesheet as follows:
{% highlight css %}
.class-name {
insert formatting here
}
{% endhighlight %}

Because classes can be reused, it is tempting to utilize them wherever possible, as they make code much more efficient. There are several cases, however, where ID's might be preferred. ID's are useful when you know that only one section of the page will receive certain formatting - for example, a title heading. ID's also trump classes when a browser decides how to render conflicting CSS, so they are  useful in very complex CSS stylesheets when you want to be certain particular formatting will be applied. In fact, you can even combine an ID with a class to utilize most of the formatting rules from a class while overriding some with an ID. ID's can also improve accessiblity in some cases.

So what is best practice for using a class versus an ID? If there is even a chance that one might want to reuse a particular set of formatting, a class is likely the best choice since it will provide for reuse. Thus, a class is likely the best choice in most cases. If, however, you want to make certain that a particular section will receive a certain set of formatting, and you don't plan on reusing it, then an ID is likely the best option.
 