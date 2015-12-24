---
layout: post
title: "Swift: An Introduction"
date: 2015-12-13T00:00:00-06:00
---
Swift is a new programming language introduced by Apple in 2014 and open-sourced in 2015. It's intended to replace Objective-C as the primary development language for Apple operating systems and is rapidly increasing in popularity. I intend on studying some Swift after finishing <a href="http://devbootcamp.com">Dev Bootcamp</a> so I thought it would be interesting to write a brief introduction to the language.

To introduce Swift it's first necessary to introduce Objective-C, its predecessor. Objective-C or Obj-C is a relatively old language; it was first introduced in 1983 and is based on the even older C programming language, which is one of the foundations of modern software engineering. Obj-C was initially popularized by Steve Jobs' company NeXT in the late 1980s and came to Apple with Apple's acquisition of NeXT in 1996. It still retains many vestiges of its earlier life; for example, many Obj-C object type names begin with NS (as in NeXTStep, the NeXT operating system.) It also shares in common with C the need to manually incorporate header files before compiling even very simple programs.

Swift seeks to be "Objective-C without the C" - that is, it seeks to retain the capabilities of Objective-C while incorporating recent developments in programming as epitomized by the rise of scripting languages like Ruby and Python.

Some interesting aspects of Swift include the following:

<ul>
<li>
Fewer legacy conventions than Objective-C (eg. removal of the NS prefix) allowing for more readable and beginner-friendly syntax
</li>
<li>
Automated memory management and improved performance, which removes much of the performance management burden from developers
</li>
<li>
Uses type inference so variable type declarations are unnecessary in many cases - allowing for behavior closer to Ruby/Python
</li>
<li>
Easy testing and feedback through the "Playgrounds" feature in XCode, which shows code output in real time
</li>
</ul>

The open-sourcing of Swift will only increase its adoption as it becomes available on platforms beyond OSX and iOS. It is likely to become one of the next decade's top programming languages and as such is a good element of any developer's arsenal. I look forward to experimenting with it soon!

For more information you can check out the <a href="https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/">Swift documentation</a> at Apple's developer site.
