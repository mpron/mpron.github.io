---
layout: post
title: Static vs. Dynamic Websites
description: "Learning the difference between static and dynamic websites for hosting purposes."
tags: [Hosting, AWS, Jekyll, JavaScript, Database]
image:
  feature: sunsurface.jpg
  credit: NASA/SDO/AIA/Goddard Space Flight Center
comments: true
share: true
---

With all of the client-side scripting we can do these days to make sites feel more dynamic, it's a little unclear for beginners how you definitively distinguish a "static website" from a "dynamic" one.  Usually it becomes clear once you start building it, but in the brainstorming phase you might be unsure.

This is important to recognize in the planning stages of a project because it could make a big difference in how you host the website and what it will cost.  Hosting for websites like this one, which was [built using Jekyll](http://mpron.github.io/first-post/), can often cost little to nothing because it is static.  I host this blog on GitHub Pages for free, but another very inexpensive option is to [host static websites on Amazon S3](http://www.webmonkey.com/2013/01/host-your-static-website-on-amazon-s3-no-www-necessary/), which is free for the first year, and very cheap after that.

Dynamic Websites will require a hosting provider that supports whatever programming language and database you are using for your website.  So normally, that will cost more and require a little more research and legwork.

So I'll get to the point now.  For the purposes of hosting your website, here is the general rule for determining if your project will be static or dynamic:

> Static sites can contain HTML, CSS, and client-side scripts.  A site is dynamic and requires a different type of hosting when it uses server-side scripting.

That's the simplest way to clearly define your website's type for hosting purposes.

# Some More Info on Static vs. Dynamic

[Client-side scripts](http://en.wikipedia.org/wiki/Client-side_scripting) are usually written in JavaScript, but there are a few other languages that can work on the client-side, like [Dart](https://www.dartlang.org/).  You can do an awful lot of dynamic-like things with JavaScript (see [Ajax](http://www.seguetech.com/blog/2013/03/12/what-is-ajax-and-where-is-it-used-in-technology) aka. Unobtrusive JavaScript).  If you don't use a database, you can still pull content from other sources without using server-side scripting, so I think you could also have dynamic content based on whether that content from another source changes over time.

Basically, what I'm saying is that you can actually build a website that has a bunch of animations and changing content while still being able to host it somewhere like Amazon S3.  This is what was confusing to me as a beginner.  "Static site" doesn't always mean static content with no animations or visual changes to the page.  You can see, for example, that this static-hosted website has dynamic animations for the upper-left corner menu.  

I don't know specifically how far you can go with a website using just client-side scripting, but client-side technologies are getting more sophisticated all the time.  I'd try googling this question to find out how sophisticated static sites can be.

I'll leave you with a table to help you make some quick distinctions between static and dynamic websites for future reference:

| Static | Dynamic |
|:--------:|:-------:|
| No server-side code   | Server-side code   |
|----
| Can't make changes to the site content on the site itself  | Generate new content while on the site   |
|----
| No database   | Can add and retrieve content from a database |
|----
| More secure, the client can't manipulate the server   | Less secure, the client can write to the server and database   |
|----
{: rules="groups"}

Hope that makes things clearer for the beginners in web development out there.  If any veterans notice an error in anything I've said, let me know in the comments.