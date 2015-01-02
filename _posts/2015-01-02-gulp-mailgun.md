---
layout: post
title:  "gulp-mailgun"
date:   "2015-01-02 20:00"
categories: posts
author: David Turner
twitter:
---
I'm a big fan of gulp.js for automating tasks when it comes to design and front-end development. I use it for my own personal work, any freelance work I've undertaken, and we make heavy use of it at [Get Invited][]. It makes our lives easier and I plan to write a bit more about that, and share how we use gulp.js day-to-day, in a future post.

Today I wanted to write a little bit about my own little contribution to gulp.js in the form of a package I released several months ago. It's been in the wild for a while now, but I haven't written anything about it until today.

## Building Upon Gulp.js

Gulp.js is built upon packages, and there are quite a few available to users. It doesn't have as comprehensive a list of packages as other tools like Grunt.js do, but it covers what I've found to be my standard needs.

Except one.

Sending emails.

_Fucking_ emails.

One of the areas that we need to test at Get Invited was cross-service email client consistency. We send a lot of emails out to customers so it's important that we test all email layouts thoroughly to make sure that everything works. Services like [Litmus][] are great for testing how an email looks but we needed to get the email through to the service before we could test things.

Gulp didn't have anything that fitted our needs, but [Grunt did][]. Both gulp.js and grunt.js are powered by JavaScript, so at their core they're the same thing. If there's one thing that I've always been good at, it's breaking one thing and reassembling it as something else. It's how I taught myself to code in my teens, and I applied that approach to learning here.

Much confusion and frustration later, and I had a working implementation of mailgun for sending emails directly from gulp.js. I could send emails quickly and easily as a part of my build process, rather than having to manually submit the markup via a web interface.

It was bliss.

## Released into the Wild

I quickly put it up on Github, but I've [published the package on NPM][], as it makes installing gulp-mailgun a lot easier. It's been seeing usage since I released it but I'd love to hear what people think of it.

## More to Come

I'm planning to write more about how we use gulp.js at [Get Invited][] in the future, and hope to share some of the tools and approaches we use with things over the coming weeks and months.

I'm also hoping to inflict more of my own thoughts and processes on you all too. Running a startup really eats into my time but this year I plan to set aside the time to share my thoughts more often. I hope that it'll be as beneficial to those who read my articles as it is for me to write them.

[Get Invited]: https://getinvited.to
[Litmus]: https://litmus.com
[Grunt did]: https://www.npmjs.com/package/grunt-mailgun
[published the package on NPM]: https://www.npmjs.com/package/gulp-mailgun