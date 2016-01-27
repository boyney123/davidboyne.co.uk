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

Developers come in all shapes and sizes (literally...) and the web community is so huge and growing at such a rate its hard for developers to keep up to date. Due to this developers tend to pick an area of technology (front-end or back-end) and stick with it for years. This has been going on for years now which has lead to a divide in the web community between front-end and back-end developers which I think is unhealthy and in this blog post I will explain why I think its important for developers to cross the divide and from my own experience what it has to offer.

### Problems that the divide between front-end and back-end causes

Every company I have worked for has in some form or another a divide between front-end and back-end developers. The front-end developer will make things “look pretty” whilst the back-end developer will provide data required by the client. This theory works well but I believe we can achieve much more. Unfortunately for some reason I have found that back-end developers are not keen to learn and understand the front-end world and the front-end developers are not really interested in the back-end world. I believe this leads to reduced productivity and creativity within teams.

> "...crossing the divide leads to increased productivity and creativity for developers and teams..."

Imagine a team built from back-end and front-end developers but both sides of the divide were keen and interested in each others technology stack. Eventually front-end developers could write back-end code and back-end developers could write front-end code. Which are commonly known as web developers or full stack developers and these type of developers are becoming more and more common within our industry. From experience I have found that crossing this divide between front-end and back-end developers leads to increased productivity and creativity for developers and teams.

### My Experience and tips on crossing the divide

I started my career as a front end developer five years ago. I would spend hours making things look good and make things interactive through JavaScript. I would ask back-end developers for data which they would provide and our client would be happy. Overtime I felt restricted in what I could achieve for the team and personally due to my reliance on the back-end developers. I wanted to become more independent as a developer and started to learn and read the back-end code of our application. Overtime I got a good understanding of what was going on and could contribute to the team in a way I couldn't before. I would contribute with the architecture of our application and also start writing the back-end code. This opened up huge windows for me as a developer as I could contribute to both sides of the divide. I felt more productive and creative than I ever had before and since then I always try and contribute on the front-end and back-end development of the applications I work on. But stepping over the divide was not easy and here are some tips that helped me along the way.

#### Pairing

Start pairing with developers if you aren't already. Its a great way to share ideas and experiences but also a great way to learn. If you're a front-end developer try pair programming with a back-end developer, ask questions and keep the decisions following, same if your a back-end developer go pair with a front-end developer. With the right pair its amazing how fast you can pick things up.

#### Read Code

Every so often I find myself reading node packages / framework source code / plugin source code. Its a great way to step inside a developer's mind. Try and find out why and what they have written and what patterns they have used. I find this a great tool to learn. If you're a front-end developer start reading your back-end developers code. Have a look in the git history or just dive straight in, ask questions if you find anything your not sure about and the same for back-end developers. You will find it amazing how fast you can pick it up and start to understand the applications full flow, which in itself is powerful.

#### Just hack away

Want to learn a new technology? Don't just read about it, start writing with it. There are plenty of tutorials online and guides on how to get started with any new technology.

#### Teach it

Personal favourite of mine, if you want to know something teach it. Maybe do a talk or an internal lunch session at work? Teaching something makes you focus hard on what you want to talk about and for me is one of the most powerful learning tools I have used.

### Why you should cross the divide

I’m not saying that all developers need to cross this divide. But from experience I would question why you wouldnt? Moving across the divide from back-end to front-end or front-end to back-end is not easy. It has taken me years of applying these techniques to finally be able to do it with confidence but the rewards in my opinion are worth it. You will be able to contribute to your team is ways which you couldn't before making you and the team more productive and creative. You will be able to fully understand and contribute to the full stack of your application, making it easier for you to understand. You will be able to write applications from scratch, no longer requiring a back-end or front-end developer. You will be able to write the whole thing yourself. And much more! These opinions are from my personal experience and I hope it helps you or drives to give it ago and step over the divide we have created as a web community.

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