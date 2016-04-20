---
layout: post
title: "Rails 5: What's New"
date: 2016-04-20T16:06:29-05:00
---

After reading up a bit on Rails 5 I find myself talking about it a lot, so I thought I'd put together a quick reference to the major changes. (Of course [DHH's post on the subject ](http://weblog.rubyonrails.org/2015/12/18/Rails-5-0-beta1/) is a much more comprehensive source of info.)

Here's my personal top three changes coming in Rails 5. These are in rough reverse order of importance - the first will be of interest to all developers while the following two are new features that are mainly relevant to new projects:

1. **Elimination of Rake tasks**: The use of bin/rails versus bin/rake for some commands was always a bit odd. Rails 5 will get rid of this - so it'll be all ```rails``` from now on for your database tasks!

2. **API Mode**: Generates a slimmed down Rails project that serves JSON and not HTML. Great for projects that rely on all those hot new client side JS frameworks.

3. **Action Cable**: Rails' response to the increasing popularity of client-side JS frameworks such as React and Angular. ActionCable uses [WebSocket](https://en.wikipedia.org/wiki/WebSocket) to update pages in real-time, allowing for similar functionality to a React/Flux setup while utilizing Ruby end-to-end.

As you can see there are a lot of exciting changes to Rails in the offing. If ActionCable delivers it will do wonders for bringing the Rails community up to speed with the most interesting work going on in the front-end JS community. API mode will also be great for organizations that have already fully bought into single-page JS frontends. But will Rails 5 put to bed the contention that Rails is past its peak? That remains to be seen.
