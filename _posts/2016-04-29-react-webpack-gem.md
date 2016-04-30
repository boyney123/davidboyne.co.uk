---
layout: post

title: Goodbye ../../../

subtitle: "Removing relative paths when importing"

excerpt: "I have recently been writing a React application and recently ran into a little webpack gem I thought I would share..."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---

I have recently been writing a [React](https://facebook.github.io/react/) application and ran into a little webpack gem I thought I would share. 

First lets look at the problem.

##### ContactUs.js

{% highlight js %}

import React, { Component, PropTypes } from 'react'

import Question from '../../components/question';
import Input from '../../components/input';


const ContactUs = ({ email, confirmEmail }) => (
    <section>

       <h2>Contact Us:</h2>

        <Question
            field={email}
            question="Email:">
            <Input type="text" className="textbox" placeholder="Email" {...email}/>
        </Question>

        <Question
            field={confirmEmail}
            question="Confirm Email:">
            <Input type="text" className="textbox" placeholder="Confirm Email" {...confirmEmail}/>
        </Question>

    </section>
)

ContactUs.propTypes = {};

export default ContactUs;

{% endhighlight %}

This is a simple high-level stateless component that could handle a contact us section for our application. 

As you can see we are importing other components to use inside this component and we are using the filepath to find the component. For example <code>../../component/question</code>

There are a couple of *(obvious)* problems with this approach.
  
#### Problem 1 – Hard time refactoring

If we want to refactor our folder structure we have to change the file path in this component and maybe others. 

Across the application this is tiresome and can take time.   

#### Problem 2 - Repetitive 

Writing <code>../../</code> or <code>../../../../</code> overtime can be boring and repetitive.  

*And lets be honest, it looks ugly!* 

#### Solution

Webpack's [modulesDirectories](https://webpack.github.io/docs/configuration.html#resolve-modulesdirectories) to the rescue. 

Using <code>modulesDirectories</code> we can use a similar pattern to what we see when we import from our <code>node_modules.</code>
 
First we need to setup <code>webpack.config.js</code>

##### webpack.config.js
{% highlight js %}
const path = require('path');

module.exports = {
    entry: [
        './src/index'
    ],
    module: {
        loaders: [
            {test: /\.js$/, loader: 'babel', exclude: /node_modules/}
        ]
    },
    resolve:{
        modulesDirectories: ['src', 'node_modules'],
    },
    output: {
        path: path.join(__dirname, 'dist'),
        filename: 'bundle.js'
    }

};

{% endhighlight %}

As you can see in this example we are mounting our ‘src’ directory *(you might want to mount something else)*. 

This now allows us to remove the file path pattern <code>../../</code>

Now lets look our component again using  <code>modulesDirectories</code>.

##### ContactUs.js
{% highlight js %}
import React, { Component, PropTypes } from 'react'

import Question from 'components/question';
import Input from 'components/input';

const ContactUs = ({ email, confirmEmail }) => (
    <section>

       <h2>Contact Us:</h2>

        <Question
            field={email}
            question="Email:">
            <Input type="text" className="textbox" placeholder="Email" {...email}/>
        </Question>

        <Question
            field={confirmEmail}
            question="Confirm Email:">
            <Input type="text" className="textbox" placeholder="Confirm Email" {...confirmEmail}/>
        </Question>

    </section>
)

ContactUs.propTypes = {};

export default ContactUs;

{% endhighlight %}

As you can see, we no longer have to import our components using <code>../../</code>, we can now directly use <code>/components/</code> which webpack will understand and mount to our src directory for us.

Give it ago. Hopefully this gem can help you like it has me.

If you have any questions just [tweet me](https://twitter.com/boyney123), or leave a comment.
 




