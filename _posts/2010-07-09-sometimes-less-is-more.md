---
layout: post
title:  "Sometimes LESS IS MORE"
date:   "2010-07-09 15:35"
type:   posts
categories: posts
author: David Turner
twitter:
---
CSS is an important part of any web design. Without it the content of you site would be a very plain looking black and white design, with blue links. It's not that it isn't *usable* but that it's not very visually appealing, which is why CSS is so important. It affords people the ability to provide a unique and visually moving site design.

As a result, every web designer worth their salt needs to have a pretty strong knowledge of how CSS works as well as how to use it. If they're anything like me, they're also looking for ways to speed up the process.

##Helping Speed things up

For a while now there have been emerging technologies to do exactly that... speed things up. Technologies such as [SASS][1], [compass][2] and [LESS][3] all provide server-side technologies to allow you to code better, and smarter, code.

All of these technologies are based on Ruby though, and so far as I'm aware it's not an overly common technology on servers, I know it's definitely not installed on mine. There have been PHP and even .NET powered versions of these technologies available but, to me, these is an added level of complexity that I don't want to have to deal with. Recently there has even been a javaScript version of it released. Unfortunately, I prefer not to make my site entirely reliant upon JavaScript.

Fortunately, for Mac users at any rate, there is a [fantastic application][4] for Mac users that allows for the use of the LESS Platform to be used to compile .less files into fully functioning .css files, ready for deployment on the web. So what's the benefit of this? LESS allows for a few things that can be of great use in CSS terms. Examples of these include:

- Variables
- Mixins (think functions in PHP or JS terms)
- Nested Styling
- Includes --- keeping code you don't need separate until you're done
- Adding values together (mixing colours together)
- Basic Math functionality (addition, subtraction, division and multiplication)


Whilst I've not had reason to make use of all of the functionality of LESS, in particular mixing and altering values with math, I have already found the other aspects to help speed up my coding. I've put together a few mixins for various CSS elements I frequently use that let me code multiple lines of CSS with very little effort on my part. Things like border-radius and box-shadow suddenly become a *lot* easier to implement without forgetting a browser-specific tag, as it's all generated for me.

There are a few problems with LESS though, which I hope will be fixed in the future. My main gripe currently is that I cannot use a mixin to create the font: css element, it simply refuses to work because of the syntax. I've also had a few instances where values (such as 14px/20px) have been divided instead of expressed as I want them. These problems are the exception rather than the norm.

Unfortunately for those of you working on Windows Machines, I have yet to find any equivalent application that can be used locally whilst developing your CSS. If you happen to find to find one feel free to let me know in the comments.

##Conclusions

I've only been using LESS.app in the development of my CSS but I've been finding it to be a fantastic tool for helping speed up my development of sites. If you're working on a Mac I would highly recommend trying it out!

[0]: /sometimes-less-is-more/
[1]: http://sass-lang.com/
[2]: http://compass-style.org/
[3]: http://lesscss.org/
[4]: http://incident57.com/less/