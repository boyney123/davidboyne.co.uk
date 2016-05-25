---
layout: post

title: Creating React templates in WebStorm

subtitle: "Speeding up your workflow using WebStorm and React"

excerpt: "I recently came across some WebStorm templates and thought I would share my React templates with you..."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---

When working with React you will often find yourself creating a number of components. If you’re like me then you might write a component and copy and paste that component to make your next component.

This is fine... but it can get boring.
 
I recently came across some WebStorm templates and thought I would share my React templates with you.

Firstly we need to be able to add templates.

So lets dive in.

## Creating templates in Webstorm

Templates can help us define the base foundations of any file we create. So lets utilise this feature and create some templates for React.

Creating templates in WebStorm is very straightforward. So how do we do create them?

First open <code>Webstorm/Preferences</code>

<img src="../../../images/webstorm/webstorm-perf.png" width="50%"/>

Then go to <code>Editor/File and Code Templates</code>

<img src="../../../images/webstorm/file-code-templates.png" width="50%"/>

Then click the plus icon <code>+</code> to add a new template

<img src="../../../images/webstorm/add.png" width="80%"/>

Now your setup and ready to go. Next lets add our templates.

## Class extends React.Component – Template

This is a basic template that will create a component using <code>Class extends React.Component</code>. 

As you can see using <code>$NAME</code> will take our filename and populate our Component.


#### Template

*Copy and paste the following into your new template*

##### React Component Template

{% highlight js %}

import React, {PropTypes} from 'react';

class $NAME extends React.Component {

    render() {
    
    }
    
}

$NAME .propTypes = {};

$NAME .defaultProps = {};

export default $NAME;

{% endhighlight %}

#### Template Output Example

So if we now create a new file called <code>Button</code> using our template will we get the following output.

<img src="../../../images/webstorm/new-component.png" width="50%"/>

<img src="../../../images/webstorm/create-component.png" width="50%"/>

{% highlight js %}

import React, {PropTypes} from 'react';

class Button extends React.Component {

    render() {

    }

}

Button.propTypes = {};

Button.defaultProps = {};

export default Button;


{% endhighlight %}

## React Stateless Component – Template

This is a basic template that will create us a stateless React component.

#### Template

*Copy and paste the following into your new template*

##### React Stateless Component Template

{% highlight js %}

import React, { PropTypes } from 'react'

const $NAME = (props) => {
	return (
		
	);
}

$NAME .PropTypes = {}

export default $NAME

{% endhighlight %}

#### Template Output Example

Lets create a <code>Button</code> component again with the <code>stateless component template</code>.

<img src="../../../images/webstorm/new-component2.png" width="50%"/>

<img src="../../../images/webstorm/create-component.png" width="50%"/>

{% highlight js %}

import React, { PropTypes } from 'react'

const Button = (props) => {
    return (

    );
}

Button.PropTypes = {}

export default Button

{% endhighlight %}

## Workflow

Automating the boring and repetitive tasks is key. It allows us to spend more time being creative. 

I know this could form a small part of your React workflow, but everything counts.

If you have any questions just [tweet me](https://twitter.com/boyney123), or leave a comment.
 




