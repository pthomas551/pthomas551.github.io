---
layout: post
title: "Configuring Mocha/Enzyme With Webpack"
date: 2016-08-24T14:02:08-05:00
---

We at [YuVue](http://yuvue.com "YuVue") have decided to use [Mocha](http://mochajs.com "Mocha") in combination with [Enzyme](https://github.com/airbnb/enzyme "Enzyme") to test our React applications. Enzyme was chosen because of its great documentation and helpful features like [shallow rendering](https://github.com/airbnb/enzyme/blob/master/docs/api/shallow.md "shallow rendering") for unit testing of React components. It also is compatible with [Jest](http://facebook.github.io/jest/ "Jest"), Facebook's JS unit test library, should we choose to use that in the future.

Since we use [Webpack](https://webpack.github.io/ "Webpack") to bundle our code, extra configuration was needed to get our test suites up and running. While there's a lot of great information out there on getting Mocha working with Webpack (like [Randy Coulman's post]("http://randycoulman.com/blog/2016/03/22/testing-with-mocha-and-webpack/")), the addition of React and its JSX syntax, along with component stylesheets, leads to added complexities that don't seem to be well summarized elsewhere. I'm going to give a quick overview of what we did.

NB. Before starting you'll want to make sure you have all the needed dependencies installed: `npm install --save-dev mocha chai enzyme mocha-webpack null-loader`.

First of all, we used the [mocha-webpack](https://github.com/zinserjan/mocha-webpack "mocha-webpack") package to precompile a Webpack bundle to feed to Mocha - although you could certainly choose to roll your own solution here. As suggested in the docs, we also set up a test runner script in `package.json` to tell mocha-webpack to refer to a special `webpack.config-test.js` file. See below; note that you'll want to change the directory/regex target based on your own test filenaming conventions.

{% highlight json %}
{
  "scripts": {
      "test": "mocha-webpack --webpack-config webpack.config-test.js \"src/**/*.test.js\""
    }
}
{% endhighlight %}

We then set up a separate `webpack.config-test.js` file as some special  configuration of our webpack loaders was needed. Note two things here: `null-loader` (a separate dependency) is needed for S/CSS because [Webpack's `style-loader` does not work in non-browser environments](https://github.com/zinserjan/mocha-webpack/issues/5), and some externals must be added to the config per the [Enzyme docs](https://github.com/airbnb/enzyme/blob/master/docs/guides/webpack.md "Enzyme docs").

{% highlight javascript %}
const config = {
  module: {
    loaders: [
      {
        test: /\.(js|jsx)$/,
        loader: 'babel',
        exclude: /node_modules/,
        query: {
          presets: [
            "es2015",
            "react",
            "stage-0"
          ]
        }
      },
      {
        test: /\.css$/,
        loader: 'null'
      },
      {
        test: /\.scss$/,
        loader: 'null'
      },
      {
        test: /\.json$/,
        loader: 'json'
      },
      {
        test: /\.(jpe?g|png|gif|svg)$/i,
        loader: 'url'
      },
      {
        test: /\.(mp4|webm)$/i,
        loader: 'url'
      },
      {
        test: /\.woff2?(\?v=[0-9]\.[0-9]\.[0-9])?$/,
        loader: 'url'
      },
      {
        test: /\.(ttf|eot|svg)(\?[\s\S]+)?$/,
        loader: 'file'
      }],
  },
  externals:
  {
    'react/addons': true,
    'react/lib/ExecutionEnvironment': true,
    'react/lib/ReactContext': true
  },
}

config.target = 'node'

module.exports = config
{% endhighlight %}

You can make sure this setup works by writing a basic Enzyme test and running `npm run test`; if it works without errors, you're good to go!
