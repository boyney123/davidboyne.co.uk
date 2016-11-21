---
layout: post

title: Test and share your localhost React applications for any device or person for fast feedback.

subtitle: "Get quick feedback from your localhost React application"

excerpt: "I come across a simple tool the other day that allows you to showcase or test your local apps anywhere and you can get setup less than a minute. In this post we will take a look."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---

Does any of this sound familiar?

* You have an app hosted locally and you want to test it on a physical device, but there is no easy way to do this without investing over 5 minutes?
* You want to show your boss or colleague some work you been working on, but getting it on their machine or device is a nightmare?
* You want fast feedback on something you are working on, you want to give somebody a url so they can view your application, but you have to deploy it first and wait...

If any of this sounds familiar then I might have a tool I have come across that could help out in **less than a 5 minutes of effort.**

In this post I will share with you the tool to solve these problems and ways it could help with not only your React applications but **any app hosted locally.**   

So lets not waste any time, lets dive in.

## The tool

### What is it?

The tool is called [ngrok](https://ngrok.com/).

<code>ngrok</code> is a secure tunnel to your localhost. This allows connections to applications running locally on our machines.

Heres some features from ngrok's website

* *Don’t constantly redeploy your in-progress work to get feedback from clients. ngrok creates a secure public URL (https://yourapp.ngrok.io) to a local webserver on your machine. Iterate quickly with immediate feedback without interrupting flow.*

* *Test mobile apps against a development backend running on your machine. Point ngrok at your local dev server and then configure your app to use the ngrok URL. It won't change, even when you change networks.*

So what this means for us is **we can host our React application locally and have anybody or device access it for fast feedback.**

Lets take a quick look at how to get setup.

### Getting setup

Getting setup is super easy. In fact its two basic steps.

1. Install <code>ngrok</code>
2. Run *ngrok http {port}*

Thats it.

You can configure <code>ngrok</code> to do more than this, so go check out their [ documentation](https://ngrok.com/docs) for more information.

#### Quick example

Lets say we have our React application running on [http://localhost:3000](http://localhost:3000) then all you have to do is run this command from your terminal.

{% highlight js %}

ngrok http 3000

{% endhighlight %}

<code>ngrok</code> will boot up and return you a hashed url. For example **http://92832de0.ngrok.io**

That’s it.

The url is the entry point to your application. **Share this with anybody or any device to get access to your localhost application.**

So lets quickly look at reasons how this might help you in your **development workflow**.

## How can ngrok help you?

Here are just some quick reasons why something like <code>ngrok</code> could be useful:

* Ability to quickly test your application on **any device**. Just go to the <code>ngrok</code> hashed url they
provide and your away.
* Share your application to **stakeholders**. Does your boss quickly need to see something? Just give them the url
* Share your application to any **tester** to get quick feedback
* Share your application for **customer testing**. Do you need fast feedback for a prototype idea?
* The list goes on…

I have only just started to use this tool, if you find it useful or have any recommendations or questions get in touch.

If you found it useful feel free to share with others in our community.

Hope it helps and can add value to your development workflow.
