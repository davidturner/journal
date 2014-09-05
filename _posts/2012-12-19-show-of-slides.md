---
layout: post
title:  "jQuery Show of Slides Plugin"
date:   "2012-12-19 15:21"
categories: posts
author: David Turner
twitter:
---

When it comes to code for projects that I'm working on, *nothing* annoys me more than code bloat. All too often people will grab a plugin to complete a single task, which is in and of itself fine, until you realise that the codebase encompasses much more than the functionality that you need, and results in a bulky collection of files and code being tagged onto a site needlessly.

Increasingly I find myself writing my own plugins to accomplish goals, each being coded to achieve a single thing well, rather than trying to do many things at once. It's easier to use multiple plugins than it is to rip code out of a single plugin. That is the reason that both my [isEmpty][1] and [Select][2] plugins exist. Today I am adding my Show of Slides Plugin to that list.

##What is Show of Slides?

I've increasingly found myself having to code up image slideshows for clients. At first it was a challenge, coding things up to work quickly without using a plugin that did much more than was needed but, as with all things you do repeatedly, it lost it's appeal. So I decided to create a plugin that I can use to quickly get slideshows working.

I have built Show of Slides from the ground up to be *flexible*. I didn't want my work to be limited to *just* image slideshows, you can just as easily use HTML content inside of the slider. It's all about keeping things both *flexible* and *minimal*.

I've also built it to afford you the maximum amount of control over how the various elements of the slideshow are laid out. This plugin adds classes to elements as needed, but ultimately leaves styling up to you. I'll be providing some basic CSS in this article though, so that you'll have some guidelines you can work with.

##What Show of Slides *isn't*?

In keeping this plugin flexible and light in the code base I've intentionally removed some things that are typically handled using jQuery as they can be handled using CSS3 in the majority of browsers these days and, for those that can't, animation is a very minor piece of functionality in the grand scheme of things.

By removing the animation from the plugin and placing it in the hands of CSS it also affords a much greater control over how the slides move, along with how they are presented. You're no longer constrained by the JavaScript powering your slider. How awesome is that?

###Caveat

There is one small problem with moving the animation from the JavaScript to the CSS, in that it becomes a bit more fiddly to handle reorganising slides once they've been moved from view. I've coded in a little bit of JavaScript math to handle this, I'll be covering it in a little more detail later.

##Getting Started

Show of Slides is relatively painless to get set up. As with all jQuery plugins you'll need to include jQuery for this plugin to work. If you've already included jQuery in your project you only need to add the plugin, ideally by adding the code to your a single, combined, JavaScript file:

{% highlight html startinline %}
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js"></script>
<script src="js/show-of-slides.min.js">
{% endhighlight %}

With the Slide of Shows plugin added to your project, it's easy to start using it. The plugin does require a specific structure to it's HTML though, in that it needs to look like this:

{% highlight html startinline %}
<div class="show-of-slide show1">
  <ul class="slides">
    <li><div class="slide-content">1</div></li>
    <li><div class="slide-content">2</div></li>
    <li><div class="slide-content">3</div></li>
    <li><div class="slide-content">4</div></li>
  </ul>
</div>
{% endhighlight %}

The *important* part of this is that there is a `div` wrapped around the slideshow. The list itself can be replaced with any elements you would like. I'll cover this a little further down as well, when I dig into the settings for the application.

With all of this in place it's simply a case of calling the plugin on the elements you want to become slideshows:

{% highlight js startinline %}
$(function() {
  $(".show1").showOfSlides();
});
{% endhighlight %}

You can, of course, list multiple selectors or add a specific selector to all of the slideshows you're after.

##Plugin Settings

There are, of course, multiple settings you can tweak with the plugin. The different aspects of the plugin that you can tweak are:

- `tag`: This is uses as the basis of CSS classes added to slides (defaults to `slide`)
- `timer`: The amount of time between slides changing (defaults to 5000, aka 5 seconds)
- `transition`: The transition time, so that the plugin can clean things up after any CSS animations have finished (defaults to 500, aka 0.5 seconds)
- `pagination`: true/false on enabling pagination (defaults to `false`)
- `arrows`: true/false on enabling previous/next buttons (defaults to `false`)
- `slides`: defines a default element that is used for slides (defaults to `li`)

This allows you a great deal of flexibility in how it's laid out, and what features you have enabled and disabled. I spoke about being able to adjust a few settings previously, some of which need to be adjusted depending on your CSS and one that can be adjusted if you're not using a list for your slides.

The first of these is that you will want to adjust the transition variable to match and CSS transition time you've set up. I've found 0.5 seconds, or 500 milliseconds, provides a suitable default. To change this you can do the following when setting up your slider:

{% highlight js startinline %}
$(function() {
  $(".show1").showOfSlides({
    transition: 1000
  });
});
{% endhighlight %}

This changes things from the default of half a second to a full second. This timer is used to call a function that reorders slides in the slider so that there is always a next slide. You can similarly adjust the `timer` variable to adjust the time between slide changes.

The second important piece of customisation that can be considered is that, in certain circumstances, you might not want to use a list for the slider. You can change this quite easily, by doing the following:

{% highlight js startinline %}
$(function() {
  $(".show1").showOfSlides({
    slides: "div"
  });
});
{% endhighlight %}

This will look for a selection of `div` elements and use them as the slides instead of list items. Ultimately the structure of the content will be the same, this allows you to define the HTML structure that suits your project/site.

The CSS is also kept pretty minimal. Below is the unminified CSS used for the examples you see on this site, but you can also [view the minified source][3] to see just how small it works out at:

{% highlight css startinline %}
.slide-pagination a, .slide-prev, .slide-next {
  text-indent:100%;
  white-space: nowrap;
  overflow: hidden;
}
.show-of-slide {
  background: #ececec;
  position: relative;
  padding: 0.5em;
  max-width: 100%;
  margin: 2em auto;
}
.slides {
  margin: 0;
  position: relative;
  height: 100%;
  width: 100%;
  max-width: 100%;
  padding-bottom: 50%;
  overflow: hidden;
}
.slide {
  list-style: none;
  position: absolute;
  top: 0;
  left: 100%;
  width: 100%;
  height: 100%;
  transition: all 0.5s;
}
.slide-current {
  z-index: 2;
  left: 0;
}
.slide-previous {
  left: -100%;
}
.slide-pagination {
  position: absolute;
  z-index: 5;
  bottom: 0.5em;
  left: 0;
  right: 0;
  text-align: center;
  margin: 0;
  pointer-events: none;
}
.slide-pagination li {
  display: inline;
}
.slide-pagination a {
  display: inline-block;
  background: #c00;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  margin: 0 0.25em;
  border: 2px solid #f9f9f9;
  pointer-events: auto;
}
.slide-pagination .slide-active {
  background: #940000;
  cursor: default;
}
.slide-content {
  width: 100%;
  height: 100%;
  font-size: 10em;
  line-height: 100%;
  color: #f9f9f9;
  background: #8080ff;
  text-align: center;
}
.layout-1 {
  background: #a00;
}
.layout-2 {
  background: #0a0;
}
.layout-3 {
  background: #00a;
}
.slide-prev, .slide-next {
  position: absolute;
  top: 50%;
  height: 4em;
  width: 4em;
  line-height: 4em;
  border-radius: 0 50% 50% 0;
  display: inline-block;
  margin-top: -2em;
  z-index: 6;
}
.slide-prev:hover, .slide-next:hover {
  background: rgba(0,0,0,0.4);
}
.slide-prev:after, .slide-next:after {
  text-indent: 0;
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  font-size: 2em;
  width: 2em;
  height: 2em;
  line-height: 2em;
  text-align: center;
}
.slide-prev {
  left: 0;
}
.slide-prev:after {
  content: "◅";
}
.slide-next {
  border-radius: 50% 0 0 50%;
  right: 0;
}
.slide-next:after {
  content: "▻";
}
{% endhighlight %}

##Support

This plugin should work well across pretty much any browser you care to throw at it. I've intentionally kept the code to a minimum which should prevent issues in older browsers. The only thing that *will* fall apart is that CSS animations won't work across every browser. If this is something that concerns you I'd strongly suggest you reconsider your approach to web design to be a bit less rigid before you go insane.

##Download

You can download isEmpty over at the [Github Repository][4], but if you just want to download the latest version you can [click here][5].

[0]: /show-of-slides/
[1]: /is-empty/
[2]: /select-plugin/
[3]: /show-of-slides/extra.css
[4]: https://github.com/DavidTurner/show-of-slides
[5]: https://github.com/DavidTurner/show-of-slides/archive/master.zip