---
layout: post
title: "Action Cable: The Basics"
date: 2016-05-03T22:08:58-05:00
---

This is a continuation of my [previous post]({% post_url 2016-04-20-rails-5-whats-new %}) on Rails 5 and the new features coming. 

In the coming weeks I'll be writing a few posts diving into specific aspects of Rails 5. These are intended for a technical audience but I'm focused on an executive summary approach rather than diving into technical details that are much more competently handled in the official docs and elsewhere.

[Action Cable](https://github.com/rails/rails/tree/master/actioncable) is perhaps the most technically interesting feature coming in Rails 5. At its core Action Cable is an integration of [WebSocket](https://en.wikipedia.org/wiki/WebSocket) with Rails. WebSocket is a relatively new protocol (established in 2011) that allows for web browsers to easily utilize full-duplex TCP communication channels. WebSocket's currently supported by all the major web browsers.

So what does this mean in practice? Your Rails 5 apps will be able to have real-time interactive features without the need to resort to JavaScript frameworks like Angular or React. Pretty neat, huh?

Action Cable uses a paradigm of "channels", where an application establishes one or multiple WebSocket channels that users subscribe to. A typical user visiting their Facebook homepage, for example, might be subscribed to a newsfeed and messaging channel. 

Channels then stream one or multiple broadcastings, which could be the same for all subscribers or tailored to a particular subset of subscribers. So taking the chat example, a broadcasting for a chat app might be a two-way chat or a chat room. Or on a Facebook newsfeed, a user would receive a specific broadcasting for their individual newsfeed.

On the client side, JavaScript event handlers are needed to deal with data I/O with the channel. At the very least channels will need handlers for connection/disconnection, along with receiving data from the channel and making changes to the view as needed.

Overall, Action Cable is a great addition to Rails that allows for easy setup of features that would otherwise require the use of complex JavaScript frameworks. It may not be the best choice for those interested in single page apps - such individuals will likely want to stick with Angular or React - but for those who want to include dynamic interactive features in a more conventional web app it will be a great addition. If you were thinking about using React for some features of your Rails app, it may be worth waiting to see how Action Cable would work for you. It could prove to be a more seamless and maintainable solution in the long run.

For a more comprehensive technical overview of Action Cable I strongly recommend the [GitHub readme](https://github.com/rails/rails/tree/master/actioncable). Tutorials are always a moving target with a technology this young but [DHH has a good demo video up on YouTube](https://www.youtube.com/watch?v=n0WUjGkDFS0) that goes into some of the practical details.
