---
layout: post
title:  "jQuery Select Plugin"
date:   "2012-11-05 17:12"
categories: posts
author: David Turner
twitter:
---
CSS gives us a lot of control over how things look and feel in our projects, but I find time and again, that there is a single element that seems to consistently cause issues. The beloved `<select>` element.

It's such a useful element to have on a site, yet it seems to have default styling in many browsers that limits what we can do. Bizarrely, I've found Internet Explorer to have the best implementation in terms of styling. That's just *wrong*.

<!--[More]-->

##Working Around Things

Unfortunately there's no way to change some default styling decisions made with this element, so instead we have to come up with creative ways to work around the issue. In a recent project I found myself needing to do exactly that.

It is something that I have attempted before, during my final year of my Interactive Multimedia Design degree. The solution I implemented there worked, but wasn't very flexible. As this is something I find myself having to attempt ever more frequently, I wanted something that could work any time I needed it. I wanted to create an easy to use jQuery plugin for select styling.

Here it is.

##What Does It Do?

This plugin takes a look at select boxes that match the selector you provide, and will add in a label after matching `<select>` boxes. It will also add some classes to these elements for the purposes of styling.

##Usage

The plugin has been built with ease of use in mind, so that you can set it up and get *straight* to using it. Being a jQuery plugin you will want to load both jQuery and the plugin to ensure that it will actually run. If you're already using jQuery then you just need to load the plugin script, there is no need to add jQuery multiple times:

{% highlight html startinline %}
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>
<script src="js/jquery.select.min.js">
{% endhighlight %}

With the plugin loaded, and jQuery running as well, it's simple to get things running. Simply copy/paste the following code into your site, somewhere after the plugin:

{% highlight js startinline %}
$(function() {
  $("select").customStyle();
});
{% endhighlight %}

That's it. The plugin will work its way through all the select boxes on the site and start adding in extra labels. There's some styling that you'll need to add. I'll show the HTML & CSS that I'm using in the demo so you can see how I've implemented things. First, the HTML:

{% highlight html startinline %}
<label for="select-1">
  Pick a dinosaur, any dinosaur:
  <select name="select-1" id="select-1">
    <option value="Pterodactyl">Pterodactyl</option>
    <option value="Triceritops">Triceritops</option>
    <option value="Stegasaurus">Stegasaurus</option>
  </select>
</label>
{% endhighlight %}

And now the CSS:

{% highlight css startinline %}
.custom-select, .custom-select-label{
  height: 2em;
  line-height: 2em;
  position: relative;
  width: 100%;
  display: block;
}

.custom-select{
  margin-bottom: -2em;
  z-index: 2;
  opacity: 0;
  -webkit-appearance: none;
}

.custom-select-label{
  padding-left: 0.5em;
  background: #ddd;
  margin: 0;
  -webkit-box-shadow: 0px 1px 5px rgba(0,0,0,0.4);
  box-shadow: 0px 1px 5px rgba(0,0,0,0.4);
}

.custom-select-label:after{
  content: "";
  display: block;
  border: 6px solid transparent;
  border-top-color: #222;
  position: absolute;
  top: 50%;
  right: 0.5em;
  margin-top: -3px;
}
{% endhighlight %}

That's all it takes to get some rather nice looking `<select>` boxes going.

##Extra Settings

There are a few pre-defined classes that are used that you might have noticed up above, `.custom-select` and `.custom-select-label`. These can be changed as you see fit, by defining some settings for the plugin, like so:

{% highlight js startinline %}
$(function() {
  $("select").customStyle({
    selClass: "custom-select",
    labelClass: "custom-select-label"
  });
});
{% endhighlight %}

This will give you complete control over the classes that are used, and over the classes applied to content on your site.

##Support

In its current incarnation of things, I've chosen to support everything *except* Internet Explorer. In using this in site development I have found that there are certain oddities that liked to crop up that were counterproductive. This is also one of those instances where Internet Explorer actually handles styling of `<select>` elements pretty well, so it shouldn't cause any issues.

##Download

You can download isEmpty over at the [Github Repository][1], but if you just want to download the latest version you can [click here][2].

[1]: https://github.com/DavidTurner/jQuery-Select
[2]: https://github.com/DavidTurner/jQuery-Select/archive/master.zip