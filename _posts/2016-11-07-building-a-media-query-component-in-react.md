---
layout: post

title: Build a simple component to handle media queries in ReactJS

subtitle: "Using media queries and a wrapper component to handle media queries in ReactJS"

excerpt: "I have been exploring a quick and easy way to add **Media queries** in **React** using styles and a simple wrapper component. Together we will quickly explore and create a simple to use MediaQuery component."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---


I have been exploring a quick and easy way to add **Media queries** in **React** using styles and a simple wrapper component.

I looked a solutions online, but did not want to implement a JavaScript solution. If your interested in pure JavaScript solutions check out these projects:

[https://github.com/contra/react-responsive](https://github.com/contra/react-responsive)
[https://www.npmjs.com/package/match-media](https://www.npmjs.com/package/match-media)
[https://github.com/viruschidai/react-match-media](https://github.com/viruschidai/react-match-media)
[http://d6u.github.io/react-container-query/](http://d6u.github.io/react-container-query/)

The problem I found with these solutions were the lack of browser support. So I explored using CSS and Wrapper Components to do something similar.

The solution is quite simple and might be helpful if you are exploring media queries and **React**.

So lets dive in, first we need to create a component.

## MediaQuery Component

<script src="https://gist.github.com/boyney123/1cd4adfbd3466704a4f63050f859fef9.js?file=MediaQuery.js"></script>

This component behaves as a **wrapper** component for child components.

When using this component you pass the **size** (defined by you, in our example mobile and desktop) you want your child components to render in. These are defined in your <code>propTypes</code>.

You can add any size you like on the <code>propTypes</code> as long as you write the matching class names in your css (we will see more of this later).

As you can see in our example we have two sizes defined <code>mobile</code> and <code>desktop</code>. When the component renders it will wrap our children with a class of <code>MediaQuery-mobile</code> or <code>MediaQuery-desktop</code> class name.

Now all we have to do is write some css to match the class names. So lets take a look at that.

## Adding media queries

<script src="https://gist.github.com/boyney123/1cd4adfbd3466704a4f63050f859fef9.js?file=styles.scss"></script>

This part is initially up to you.

This file just supports our examples we made in our <code>MediaQuery</code> component.

As you can see we have <code>mobile</code> and <code>desktop</code> media query support. You can add any media query you like, just make sure you match the class name up to your <code>propTypes</code> in your <code>MediaQuery</code> component.

Now lets use our component in action.

## Using the component

<script src="https://gist.github.com/boyney123/1cd4adfbd3466704a4f63050f859fef9.js?file=Example.js"></script>

That’s all have to do.

The header **'Mobile View'** will get rendered on mobile.

The header **'Desktop View'** will get rendered on desktop.

## Wrap up

This was just a quick experiment I come up with when exploring Media queries in React. I haven't created a demo as its super easy to copy this code and try it out for yourself.

You can checkout the whole gist below.

[https://gist.github.com/boyney123/1cd4adfbd3466704a4f63050f859fef9](https://gist.github.com/boyney123/1cd4adfbd3466704a4f63050f859fef9)

If you have any questions just [tweet me](https://twitter.com/boyney123), or leave a comment.
