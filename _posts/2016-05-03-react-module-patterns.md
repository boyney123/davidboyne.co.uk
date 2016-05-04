---
layout: post

title: JavaScript module patterns in React

subtitle: "Exploring different patterns to use import & export with ES6 and React"

excerpt: "Yup with redux-form is pretty cool. Using schemas to validate our forms is very powerful...."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---


I’ve recently been exploring and using different patterns in React to import modules recently and I thought id share 
what patterns I came across with some examples of why you might use them.

Lets dive in.

### import * as 

*Use case : Import an entire module's contents*

This import pattern allows us to import the entire module content and cast it into another variable to use within our scope.

##### Example - Importing all components from a directory
<code>import * as myComponents from “../components/”</code>

In this example this import pattern allows use to export multiple things from within our component directory. Lets take a look at what that looks like.


{% highlight js %}
src/
├── components/
   ├── input/
   │  └── index.js
   ├── date-picker/
   │  └── index.js
   ├── dropdown/
   │  └── index.js
   ├── index.js

{% endhighlight %}

index.js would import all the components and export them individually in this example. Allowing us to import the index file and get access to everything.	


If you have any questions just [tweet me](https://twitter.com/boyney123), or leave a comment.
 




