---
layout: post
title: "Rails 5 API Mode: The Basics"
date: 2016-05-13T15:04:32-05:00
---
This is a continuation of my series of posts on Rails 5. For more information see my [original post]({% post_url 2016-04-20-rails-5-whats-new %}) on Rails 5 and the new features coming and my [earlier post on Action Cable]({% post_url 2016-05-03-action-cable-the-basics %}).

API Mode is another of the key additions to Rails 5 and allows for the development of slimmed down Rails apps that communicate only in JSON. It's well suited for web applications that rely heavily on JavaScript, especially if they use a containerized infrastructure like Docker. By using API mode, you have access to the great Active Record ORM and all the ease of use Rails while avoiding the various pitfalls of using Rails for a complex Javascript application.

This functionality has existed since 2012 in the form of the [Rails API gem](https://wyeworks.com/blog/2012/4/20/rails-for-api-applications-rails-api-released/) but has now been merged into the main Rails project.

To create an API-only Rails 5 app, all that's needed is to add the `--api` parameter to the `rails new` command. API projects will have several major differences with standard Rails projects, especially the following:

* There are no views or templates since API mode projects do not have views
* Generators will not generate views or JS and generated controllers are set up to `render json` for all REST actions.
* Gemfile will not contain front end related gems like `jquery-rails` and `turbolinks`
* In addition, the `new` and `edit` actions are not included, since API mode projects would not be rendering HTML for these tasks. Nor is `respond_to` available since API mode projects would only be communicating in one format.

For more information and a basic tutorial, you can consult [this great post](https://wyeworks.com/blog/2015/6/11/how-to-build-a-rails-5-api-only-and-backbone-application) from the creators of Rails API.
