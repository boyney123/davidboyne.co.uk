---
layout: post

title: How to build and host a React application faster than making yourself a hot drink...

subtitle: "Build and host your application within seconds"

excerpt: "Turn on the kettle, and make and host your React application. Your application will be up and hosted before your hot drink is ready..."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---

__It will take you longer to make a hot drink that it will to create a new React application and host it in the cloud...__

...OK. Well maybe thats asking for abit too much, but once you get passed the setup required, you can create and host your React application within seconds!

Before you run and put the kettle on lets take a look at some ground work you will need to setup first.

## Getting prepared

We will be using [create-react-app](https://github.com/facebookincubator/create-react-app) to create our new application and [now](https://zeit.co/now) to deploy it.

Run the following to get both installed on your machine.

{% highlight js %}

npm install -g create-react-app now

{% endhighlight %}

_NOTE: This command will install `now` cli globally as npm package. Another (or suggested) approach is to install [Now Desktop](https://zeit.co/download) to ensure automatic updates of now cli._

Once your install has completed its time to create our new React application.

__Go turn on the kettle.__ 

Hopefully by the time its boiled our website will be ready and hosted in the cloud.

## Setting up your project

First thing we do is create our new application.

{% highlight js %}

create-react-app my-app

{% endhighlight %}

Great. We have setup our new project and got the basics in place.

Time to host our application somewhere...

## Authenticate & Host your application

Next thing we want to do is use `now` to host our application. Run these commands inside your `my-app` directory.

{% highlight js %}

cd my-app
npm build
cd build/
now

{% endhighlight %}

_You might need to sign in with your email to deploy your application using now._

Now will run and host your application. 

Once you are authenticated (you may need to provide and authenticate your email) your application has successfully deployed you will be given a url in the command prompt which might look something like this [https://build-lrgvixfeev.now.sh](https://build-lrgvixfeev.now.sh).

Click on your url, and you can now view your application running in the cloud.

## Thats a wrap - Time for a hot drink

Thats it we are done. 

We have created a new React application and hosted it using now's real time and immutable deployments. 

Hopefully your kettle has now boiled and you can make yourself that refreshing hot drink.
