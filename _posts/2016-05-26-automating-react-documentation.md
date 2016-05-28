---
layout: post

title: Automating documentation for your React components

subtitle: "Sharing with documentation"

excerpt: "I recently came across some WebStorm templates and thought I would share my React templates with you..."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---


Building and sharing <code>components</code> is one of the most powerful features of <code>React</code>, but what good are our components without any **documentation**?

I have recently been involved in a project creating components that will be adopted by a wide range of developers and have learnt a way to easily automate <code>component</code> documentation.

In this post we will cover why you might need to document your components and how you can easily achieve this with <code>React</code>.

## Why document components?

So firstly you might be thinking why do we need to document our components?

To be honest it really depends on what you are building and who will be consuming your components.
 
When building web applications in <code>React</code> our **tests** could be enough documentation for our components.

But if your writing a large scale application or large number of components that are used throughout your business or for a online community then documentation is **key**.

If we look at some examples like [React Bootstrap](https://react-bootstrap.github.io/) or [Material UI](http://www.material-ui.com/#/) their documentation **really helps developers** get setup and utilising their components within **minutes**.

Taking **inspiration** from these projects, I wanted to do something similar for my project and managed to do it with some awesome tools I found along the way.

So lets take a look at them.

## react-docgen

[react-docgen](https://github.com/reactjs/react-docgen) is a CLI and toolbox to help extract information from <code>React</code> components, and generate documentation from it.

The idea is simple. We pass our  <code>component</code> into <code>react-docgen</code> and it will return an <code>object</code>.

Lets take a look at the example on the <Code>react-docgen</Code> [GitHub page](https://github.com/reactjs/react-docgen).


##### Component Example

{% highlight js %}

var React = require('react');

/**
 * General component description.
 */
var Component = React.createClass({
  propTypes: {
    /**
     * Description of prop "foo".
     */
    foo: React.PropTypes.number,
    /**
     * Description of prop "bar" (a custom validation function).
     */
    bar: function(props, propName, componentName) {
      // ...
    },
    baz: React.PropTypes.oneOfType([
      React.PropTypes.number,
      React.PropTypes.string
    ]),
  },

  getDefaultProps: function() {
    return {
      foo: 42,
      bar: 21
    };
  },

  render: function() {
    // ...
  }
});

module.exports = Component;

{% endhighlight %}

##### JSON output

{% highlight js %}

{
  "props": {
    "foo": {
      "type": {
        "name": "number"
      },
      "required": false,
      "description": "Description of prop \"foo\".",
      "defaultValue": {
        "value": "42",
        "computed": false
      }
    },
    "bar": {
      "type": {
        "name": "custom"
      },
      "required": false,
      "description": "Description of prop \"bar\" (a custom validation function).",
      "defaultValue": {
        "value": "21",
        "computed": false
      }
    },
    "baz": {
      "type": {
        "name": "union",
        "value": [
          {
            "name": "number"
          },
          {
            "name": "string"
          }
        ]
      },
      "required": false,
      "description": ""
    }
  },
  "description": "General component description."
}

{% endhighlight %}

The <code>JSON object</code> we get back has extracted documentation from our <code>component</code>. 

The <code>Object</code> holds all the <code>props</code> we defined in the component.
 
 For each <code>prop</code> it returns the **type**, if it is **required**, the **description** and any 
**default values**.

So using the CLI is great, but how do we use this in a React application and automate the process? Its actually pretty straight forward so lets have a look.

## Using react-docgen inside our React application

First thing we should do is install <code>react-docgen</code>

{% highlight js %}
npm install --save react-docgen
{% endhighlight %}

Next lets  <code>import</code> it into our <code>React</code> application

{% highlight js %}
import {parse} from 'react-docgen';
{% endhighlight %}

Now we have the ability to <code>parse</code> any component and get its documentation back. But to use the <code>parse</code> function we need to <code>import</code>
our components as <code>strings</code>.

So lets import a component as a <code>string</code> using the [raw-loader](https://github.com/webpack/raw-loader).

## Using raw-loader

First we need to install raw-loader.

##### Installing raw-loader
{% highlight js %}
npm install raw-loader
{% endhighlight %}

After [setting up raw-loader](http://webpack.github.io/docs/using-loaders.html) with <code>webpack</code> we can import any file in its **raw format**.

##### Import file in its raw format
{% highlight js %}
import Component from '!raw!./Component';
{% endhighlight %}

*Note: Component will come back to us as a <code>string</code> and not a <code>React</code> component.*
 
With the component as a <code>string</code> we can pass it into our <code>parse</code> function from
<code>react-docgen</code> to get some documentation back.

{% highlight js %}
import {parse} from 'react-docgen';
import Component from '!raw!./Component';

const componentDocs = parse(Component);

{% endhighlight %}

In this example <code>componentDocs</code> will hold the components documentation as a <code>JSON object</code>. 

## What does this mean?

For large scale <code>React</code> applications being able to get **documentation** from our components might be a great idea.
 
Using <code>react-docgen</code> and <code>raw-loader</code> we could easily create a simple **user interface** to represent our library of components and their documentation for other developers to consume.

Using the information we could visually show our components in use, our component <code>props</code> details and our components description.

Here is an example of what I've been working on and what you can achieve with <code>react-docgen</code>.


##### Basic React application that renders component documentation
<img src="../../../images/docs.png"/>

The Button's <code>description</code> and <code>props</code> are automatically generated anytime the component changes making sure the documentation is always kept up to date for other developers.

This post was inspired by reading [material-ui project on GitHub](https://github.com/callemall/material-ui).

Checkout the [material-ui project on GitHub](https://github.com/callemall/material-ui) for some awesome examples on how they are using this technology to help drive their component documentation. 

If you have any questions just [tweet me](https://twitter.com/boyney123), or leave a comment.












