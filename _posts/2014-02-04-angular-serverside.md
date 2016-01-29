---
layout: post

title: Moving from Client-side logic to Server-side logic with AngularJS, Node.js and Express.js
cover_image: motivation.jpg

excerpt: "With examples for a project I worked on"

author:
  name: David Boyne
  twitter: boyney123
  bio: Dev
  image: ks.png
---

Three weeks into a new project, I had written some testable, decoupled and modular JavaScript code for a web application I was creating. Using AngularJS I created directives, controllers and modules that were reusable and most importantly using dependency injection they were easily testable.

> "..I removed AngularJS from the project and deleted all the JavaScript..."

At the end of the third week I was proud of the JavaScript code that was written in such a short amount of time. With around 1000 lines of JavaScript the application was fully tested and working as expected. The following Monday I removed AngularJS from the project and deleted all the JavaScript I had written over the past few weeks. In this post blog I will explain my thoughts and why it was removed.

### Tunnel Vision

Recently I was given the opportunity to work on a new project at work, which was great and exciting. I got told that a web application needed to be written and being somewhat a JavaScript enthusiast I wanted to use a framework. In the past I have used Backbone.js, KnockoutJS and AngularJS. From experience with all these frameworks I choose to write the web application using AngularJS. Within no time at all I had my project setup with Karma, PhantomJS and AngularJS. With the aid of [angular-mocks](https://docs.angularjs.org/api/ngMock "angular-mocks") I was able to write testable Angular code fast!

> "..I was proud of what was achieved after a couple of weeks."

I spent time drawing the applications architecture down on paper then coding it up. Most things worked as expected and a couple of weeks later I had the web applications basics done. Everything was modular, decoupled and testable. I followed the SOLID and DRY principles and I was proud of what was achieved after a couple of weeks. I naturally wanted the web application to be a single page application and I used angular-router to load in different views. The only issue I found was the client would have to ask the server where the user should get directed to when the application launched. Which wasn't too much of an issue but it felt dirty. Although the application was in working condition, certain parts of it seemed to have this layer of unnecessary complexity.

> "...using a server side templating language could dramatically decrease the complexity of the application..."

Node.js was used for the backend and I was serving up static HTML, JS and CSS. Everything seemed to be working fine until I had a conversation with a colleague of mine and he asked what server side tempting language I was using. I told him I was just serving static HTML and he asked me why, and I replied I just needed HTML and AngularJS for the web application but that night on the way home I realised what I had done… I realised that a server side templating language could dramatically decrease the complexity of the application and remove the need or requirement of a front end framework such as AngularJS.

### Refactoring

I went back to work on Monday with them thoughts in mind and tested out some theory’s using express.js and node.js and I was right. In theory I could remove all client side JavaScript code and make the application structure simple. So I did. Using express.js (routing and middleware) with jade templating I was able to do everything I wanted from server-side. Most the requirements for the project could be delivered using server-side templating.

### Lessons Learnt

When I started the project I was so excited to get on board and I naturally thought a frontend framework would be best for the web application but I realised due to the nature of the web application (its requirements) I was able to do what was required server-side which greatly reduced the applications complexity.

> "...think about all possible scenarios even if it’s a different technology stack..."

I understand that some people might read this and think it’s a rookie mistake to make, but I learnt that when starting a new project to really think about all possible scenarios even if it’s a different technology stack, because there might be something that is simpler and easier to implement.