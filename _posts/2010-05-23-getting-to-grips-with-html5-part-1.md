---
layout: post
title:  "Getting to Grips with HTML5 - Part 1"
date:   "2010-05-23 17:45"
type:   posts
categories: posts
author: David Turner
twitter:
---
This article is one of a series that I plan on covering, regarding HTML5. Over the series I plan to take a look at various aspects of HTML5, be it browser support, how you can start working with it _now_ or how to get HTML5 Video working across browsers, with support for those who don’t yet support these tags.

### Browser Support – Here &amp; Now

Today, as the title suggests, I’ll be dealing with the support offered by the most common browsers, and what we can do for those browsers that don’t support HTML5 currently. The browsers that I’ll be covering are:

*   Firefox
*   Safari
*   Chrome
*   Opera
*   Internet Explorer 6
*   Internet Explorer 7
*   Internet Explorer 8

Whilst IE6 isn’t a modern browser and many designers/developers have an intense dislike for it, including myself, it is an unfortunate reality that it is still a common browser and thus it is a browser that we need to keep in mind when developing using HTML5.

#### Firefox, Chrome, Safari &amp; Opera

I have bundled these four browsers together as, from my own experience, the current versions of these browsers support the important parts of HTML5 pretty consistently. These include the new semantic tags used for laying out elements: header, nav, section, article, aside, figure and footer. They do, however, typically need to be pointed in the right direction when it comes to styling them. Fortunately this is a simple task, completed by adding the following CSS into your stylesheet.

{% highlight css startinline %}
header,
section,
footer,
aside,
nav,
article,
figure {
	display:block;
}
{% endhighlight %}

This code will ensure that all elements that _should_ be displayed as block by default _are_ displayed as block when pages load. This will almost certainly be a default in future versions of browsers.

##### Older Browsers

Older browsers, as well as browsers that are rarely updated, really are the problem children when any new standard is released, as they cannot be developed to support features that have yet to be created. It’s quite understandable but I thought I’d go into a little detail about what the result of this is.

As pointed out already, the current versions of these browsers all support, to some extent, HTML5. The problem with older browsers is that they don’t see, or register, HTML5 elements. This can cause problems when using elements such as header, section or pretty much any of the elements I have mentioned so far, as they make up an important part of sites developed using HTML5.

This causes a really tragic breakage, for lack of a better work, of the design of a site. Without the styling of such features a design can, and quite possibly would, fall apart. Fortunately these browsers are _very_ good in terms of updating their software, ensuring that such incidents are very much the exception than the norm.

#### Internet Explorers 6, 7 &amp; 8

Internet Explorer has a mixed reputation, as the browser has become increasingly good, or less bad, over the past several years and, with Internet Explorer 9, will become even better, with full HTML5 support. That, however, is the future. I’m discussing the here and now in terms of support for HTML5.

I’ll keep it brief for you, there isn’t any. Currently Internet Explorer does not support HTML5 in any way, shape or form. Fortunately, there’s a way to force Internet Explorer to acknowledge the existence of HTML5 elements, which has both upsides and downsides.

**Upsides**

1.  HTML5 element support
2.  Allows for CSS Styling

**Downsides**

1.  Project becomes JavaScript Dependant

That’s right, the solution for Internet Explorer’s lack of HTML5 support is dependant upon JavaScript. How does JavaScript help? JavaScript has a rather nice command, document.createElement(), which when used in the `<head>` section of the site forces the browser to acknowledge that the element created can be styled. An example of how this can be done would be:

{% highlight js startinline %}
document.createElement('article');
document.createElement('footer');
document.createElement('header');
document.createElement('hgroup');
document.createElement('nav');
{% endhighlight %}

The code above would force Internet Explorer to acknowledge the existence of the 5 elements mentioned. Personally I would recommend that you look into making use of [Remy Sharp’s](http://remysharp.com/) fantastic [HTML5 Enabling Script](http://remysharp.com/2009/01/07/html5-enabling-script/), which is also available on [Google Code](http://code.google.com/p/html5shiv/), which spares you from having to manually create each element.

An alternative that you could make use of [Modernizr](http://www.modernizr.com/), which is useful for much more than making HTML5 work for Internet Explorer, having the capability to detect what features a browser supports using JavaScript.

Anyway, that’s it for today’s post. My next HTML5 post will look at how you can start using HTML5 now, covering what has changed and will cover a guide on making the switch from XHTML/HTML4 to HTML5.