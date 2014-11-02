---
layout: post
title:  "Optimising Your Site: The Basics"
date:   "2012-06-13 15:47"
categories: posts
author: David Turner
twitter:
image:
  featured:
    src: /img/getting-in-shape.jpg
    alt: "Optimising Your Site: The Basics"
    width: 1000
    height: 400
---
In my work I spend a lot of time doing all that I can to ensure that things load *quickly* and *efficiently*. Speed is always a factor when it comes to loading content and, whilst home internet connections are always speeding up, mobile data plans vary from blazingly fast to painfully slow.

I have been pondering how best to go about this post. With the increasing fluidity of the web, some of the “best” practices are becoming more difficult to impliment efficiently. In researching for this article I myself discovered I could make a large saving in loading times. So this is more of a guide than a rulebook, since the best way for one site might not be the best way for another.

If you are interested in getting to grips with this aspect of site development, I'm going to start with some basics and work towards more complex aspects over a series of additional articles. I hope that by the end of the series everyone reading will have added a new tool to their belt, be that knowledge or an application that makes life easier.

##The Basics

When it comes to getting a site loading as quickly as possible there are a lot of technical aspects to consider. There are also some very basic ones that are, sadly, too often overlooked:

- Number of Files
- File Size
- Ordering Files

These aren't necessarily things that can be completely controlled, there are always going to be lots of images in a photo gallery for example. Even with these kinds of sites there are aspects that you will have contol over.

###Number of Files

All too often I see sites with code that looks like this:

{% highlight html startinline %}
<link type="text/css" rel="stylesheet" media="screen" href="/style/style_reset.css" />
<link type="text/css" rel="stylesheet" media="screen" href="/style/style_960.css" />
<link type="text/css" rel="stylesheet" media="screen" href="/style/style_structure.css" />
<link type="text/css" rel="stylesheet" media="print" href="/style/style_print.css" />
{% endhighlight %}

In terms of styling a site there isn't anything wrong with this. In fact, when coding a site I've always found keeping some things separate to be a good thing, as it keeps them out of the way. When it comes to launching a site, however, it's not quite as ideal.

The reason for this is that each time you load a file the browser has to fetch that file, which takes time. It's not a large amount of time, but [every millisecond counts][1]. The more files you add the longer it takes for a site to load.

####Solution: Combine Files for Launch

Keeping multiple files separate is fine for development of a site, but you want to combine them for launch. The above code could, with ease, be combined down to:

{% highlight html startinline %}
<link type="text/css" rel="stylesheet" media="screen" href="/style/site.css" />
{% endhighlight %}

Isn't that much nicer? As an added bonus, if you're using a [CSS precompiler][2] you can have it take care of this kind of thing for you.

###File Size

Lots of files is a problem, but it's not the only problem. Files that are larger than they need to be cause problems too, and is probably the area in which most savings can be made. This applies largely to images, but it also applies to JavaScript, CSS, and even HTML. Writing code that is easy to read is always a good thing. But indenting code, via tabs or spaces, serves to bulk out files.

When it comes to a live site every saving is beneficial. Smaller size results in faster load times. Faster load times result in users getting to your content faster. This results in less users leaving before seeing your content. It also results in Google being slightly happier with your site too. Everyone wins.

####Solution: Compress Content {#compress-content}

Compressing code results in files that are slightly smaller. Whilst small amounts of compression won't impact load times *that* much, these savings can build up. It also results in a saving in terms of bandwidth, which is a financial incentive for adopting this approach.

It's possible to go even further with JavaScript, using minification tools. When writing JavaScript it makes sense to name variables in a manner that makes sense to you. When deploying it to a server, it doesn't. The only difference between a variable named `a` and a variable named `humanReadableVariable` is the amount of space it takes up.

Images are the other area that vast savings can be made. The first area that you can make heavy savings is by ensuring that the size of the image is the size it needs to be. If you display a 400px by 400px at 200px by 200px, you're loading in four times the amount of data you need to. Never do that.

You can make even further savings though. Images almost always have extra information attached to them. Extra information takes up space. What can we do to get rid of that imformation? We use something to strip the excess data from the files.

[ImageOptim][] is a Mac application that can take care of that for you, and generally removes all the bits of an image that serve to make files bigger than they need to be. For anyone on Windows [RIOT][] seems to be similar.

For an application that handles everything, however, I would strongly recommend [CodeKit][]. It can be used to compress files, minify JavaScript, and strip excess data from images. Unfortunately it's a Mac-only app, so not useful for those Windows using readers out there.

**Update:** [Chris Grant][] suggests looking at [LiveReload][] as a partial alternative for Window users. It doesn't handle all of the things CodeKit can, but it's a start. It can also serve as an alternative for Mac users as well.

###Order of Files

The rules with the order of files seem to vary depending on who you ask. I follow a very strict set in the development work that I do. CSS in the `<head>` element, JavaScript goes right before the `</body>` tag. With *two* exceptions:

1. [HTML5Shiv][]/[Modernizr][] JavaScript goes before the `</head>` tag
2. [Adaptive Images][] JavaScript typically goes before the `</head>` tag

Both of these exceptions exist for *very* good reasons. Both HTML5Shiv and Modernizr are used to ensure that HTML5 renders properly in older versions of Internet Explorer. For them to function they need to be loaded before the content of the site.

The logic behind the Adaptive Images JavaScript is to ensure maximum effectiveness. In order to achieve this the cookie it creates needs to be in place *before* any images start loading. To do this I typically insert the code before the `</head>` tag. The current exception is this site, as I explicitly wanted to be able to measure the dimensions of an element of the site.

####Solution: CSS in the `<head>`, JavaScript before `</body>`

Ordering files like this, with the exceptions listed above, results in content rendering more quickly. Yes, it doesn't really change how quickly a page loads, but it changes the perception. The content is loaded more quickly, and the JavaScript functionality can be added on once it's loaded.

##The Basics - Covered

When it comes to optimising a site to load quickly, the above are some of the most basic areas that can be looked at in order to improve things. These simple guidelines can get things going in the right direction pretty quickly. There's a great deal more to cover, and I intend to look at other areas in future articles, taking a more in-depth look at things as I go.

If you feel I've missed something out, disagree with what I've said, or just want some more detail on a particular area feel free to comment below or [message me on twitter][3].

##What's Next?

This post covers some of the basics of optimising your site so that it loads more quickly. I want to take a look things in more detail going forward. Next week I'll be taking a look at some further ways to optimise images for the web, as well as some alternatives.

[0]: /optimising-your-site-the-basics/
[1]: http://googlewebmastercentral.blogspot.co.uk/2010/04/using-site-speed-in-web-search-ranking.html
[2]: /sometimes-less-is-more/
[3]: https://twitter.com/intent/tweet?original_referer=&source=Optimising+Your+Site+-+The+Basics&text=@HerrWulf&url=https://davidturner.name/journal/optimising-your-site/

[ImageOptim]: http://imageoptim.com/
[RIOT]: http://luci.criosweb.ro/riot/
[CodeKit]: http://incident57.com/codekit/
[Adaptive Images]: http://adaptive-images.com/
[HTML5Shiv]: http://code.google.com/p/html5shiv/
[Modernizr]: http://modernizr.com/
[Chris Grant]: http://twitter.com/duckbox
[LiveReload]: http://livereload.com/