---
layout: post

title: React.createClass vs extends React.Component

subtitle: "Poll results from Twitter"

excerpt: "React.createComponent and extends React.Component give us the same results. The ability to create React components..."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---

**React.createComponent** and **extends React.Component** give us the same results. The ability to create React components.

I’m starting a new project, and wanted to set a standard in the way I create components. I was interested to see who uses 
**React.createComponent** or **extends React.Component**.  

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">How do you create your <a href="https://twitter.com/hashtag/react?src=hash">#react</a> components? <a href="https://twitter.com/reactjs">@reactjs</a> <a href="https://twitter.com/londonreact">@londonreact</a> <a href="https://twitter.com/React_Tutorial">@React_Tutorial</a></p>&mdash; David Boyne (@boyney123) <a href="https://twitter.com/boyney123/status/723084810990702592">April 21, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Looks like the majority of people that answered are using **extends React.Component**. 

I done some deeper diving into why and found some links that might help you decide: 

[Composing Components](https://reactjsnews.com/composing-components)

#### Choose extends React.Component

I decided to use extends React.Component due to the fact it looks like [Facebook might be dropping it at some point](https://facebook.github.io/react/blog/2015/03/10/react-v0.13.html) *(although that was over a year ago...)*. Thanks to [@Rhodesy](https://twitter.com/Rhodesy) for pointing this out. 




