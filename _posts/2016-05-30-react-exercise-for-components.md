---
layout: post

title: Developing components as a team

subtitle: "Simple exercise to help component consistency between developers"

excerpt: "A problem with components is that they can be opinionated. What I class as a component might not be what you would class as a component and vice versa. 
Take a look at this simple exercise that can help you and your team define components and start working together."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---


Components are **awesome**. They can encapsulate our **HTML**, **JavaScript** and **CSS** into reusable, tested and packaged code.

A problem with components is that they can be **opinionated**.  What I class as a component might not be what you would class as a component and vice versa.

When working in a team, sharing **ideas** and **knowledge** is important. So how do we make sure we are on the same page when it comes to building components as a team?

In this post we will look into the thought process  when we break our applications down into components, and how we bridge the gap between our thoughts and the thoughts of other developers around us.

So lets get started.

## Breaking down applications


When building any type of application its common practice that we break down our application into smaller parts. This 
allows us to understand how our application will be built.

<code>React</code> gives us the ability to create components and components allow us to break down our applications very easily. 

Lets take a look at how we could break down my [Twitter profile page](https://twitter.com/boyney123) into components. 

<img src="../../../images/twitter/profile.png"/>

Take a minute to think, if you were to build this page out of components how would **you** do it? 

Here are some of my initial thoughts:

<img src="../../../images/twitter/profile-components.png"/>

Components: 

{% highlight html %}

<CoverPage />
<ProfileSideBar />
<Navigation />
<GlobalSearch />
<ProfileNav />
<TimeLine />
<Tweet />
<Trends />
<Button />
{% endhighlight %}



When looking at my components I can almost guarantee one of two thoughts might of crossed your mind:

* You agree with the components I have highlighted
* You disagree with the components I have highlighted

Regardless if you **agree** or **disagree** I think this highlights an interesting problem 
we can have when designing and creating components with other people. 

Components are **opinionated**.  

Its the same when we do almost any kind of work in teams, we are always in agreement or disagreeing. But the key is we work together to find a common ground and move forward together
as a team.

I have been working on a <code>React</code> training course and an exercise from the course can help you and your team start thinking of components
together and collaboratively.

Lets take a look at the simple exercise.

## Team exercise

1. Print out an existing web application or create some wireframes of a new application  *(like my Twitter example above)*.
 
	*The application could be a real example from your business or maybe a random website.* 

	*Either way you want to provide an example where your team can break down the given application into components.*

2. Gather your team together and hand everybody a print out of the example application and a pen or highlighter.

3. Give your team time and ask them to highlight or write down any components they might see on the page. 

4. Once they have completed the task, go around the room and ask them to individually talk through their 
components and their thought process.

Thats it.

*Told you it was simple ;)*

## Outcome

This exercise should provide you with a few outcomes:

* Insight into how the team define and build components
* Insight into the teams thought process
* Open up communication between the team
* Collaboration across the team

## Conclusion

When we look at **Art** we all see something **different**.

When we build **applications** we will all build them slightly **different**.

When we build **components** we will all build them slightly **different**.
 
Team collaboration is key for a successful team. When your team is collaborating and on the same page you will be able to move faster than ever.

As I mentioned earlier in this post. Components are **awesome**. But if we build components in isolation, without our team or
 without basic documentation then they can potentially become painful.

*Check out my post on [Automating documentation for your React Components](http://davidboyne.co.uk/2016/05/26/automating-react-documentation.html)*

The exercise I have shared in the post will not be enough, but its a good start.

Its up to you and your team to continue to build your **relationships** and work **together** to define your applications and your components.

I would love to hear how you are working with <code>React</code> in your team?

If you have any questions just [tweet me](https://twitter.com/boyney123), or leave a comment.








