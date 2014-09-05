---
layout: post
title:  "Simple CSS Goodness"
date:   "2013-02-27 11:09"
categories: posts
author: David Turner
twitter:
---
I've been tinkering with my site over the last few days, and it's resulted in a few under the hood improvements that I thought I'd share. None of it is especially mind-blowing, it may even be common sense to a some people, but when I mentioned it on twitter some people thought it was a neat idea, so here it is.

##Styling Based on Attributes

This is something Chris Coyier has [written about in the past][attribute-selectors] in the past, styling elements that have certain attributes attached to them. This can work really well for providing styling defaults to mutliple classes at once, such as `btn-large` and `btn-small` by identifying that they both start with `btn-`.

It's possible to do more though with CSS by using content *of* selectors using CSS. This is something that A List Apart [has covered][goingtoprint] when talking about styling things for print, showing URLs after links as a user can't click on a printed page. It's also a fundamental part of the [clearfix hack][micro-clearfix-hack] that anyone on the web is likely to be familiar with.

We can do some pretty clever stuff with these two things. I've recently put it to work with regards to using icon characters from the [Symbolset][] fonts. The CSS that they provide requires adding a lot of CSS classes to both your markup and in your stylesheet. I switched away from that to a set of Sass mixins that return characters, but it still requires that I add a chunk of CSS to my site to handle individual characters.

Then it struck me, I could switch to using an attribute on the HTML elements that I wanted to have these characters appear on. Something like this:

{% highlight html startinline %}
<a href="/" data-icon-standard="⌂">Home</a>
{% endhighlight %}

The important part of this is the HTML5 `data-` attribute on the link. It's got a standardised name for a specific type of character. I currently have two different attributes that I make use of:

1. `data-icon-standard`: I use this for characters from Symbolsets's SS-Standard font
2. `data-icon-social`: I use this for characters from Symbolsets's SS-Social font

This *vastly* simplifies the CSS I need to use to style these elements up. Previously each icon I wanted would have needed a new CSS class to add the right character for me. something like:

{% highlight css startinline %}
.home:before { content: "⌂"; }
.email:before { content: "✉"; }
.plus:before { content: "+"; }
{% endhighlight %}

Add more characters to this and you can see that it could, quite rapidly, become quite unweildy. Instead I can add the specific characters to my markup, and have them added using CSS:

{% highlight html startinline %}
<a href="/" data-icon-standard="⌂">Home</a>
<a href="/" data-icon-standard="✉">Email</a>
<a href="/" data-icon-standard="+">Add</a>
{% endhighlight %}

With this in place I can simplify my CSS to the following:

{% highlight css startinline %}
[data-icon-standard]:before {
  content: attr(data-icon-standard);
  font-family: SSStandard;
}
{% endhighlight %}

This takes care of the character *and* sets the correct font. It might be a bit over the top for just a single icon, but if you find yourself using multiple icons over the course of a project this simplifies the addition of characters to a site quite a bit.

##Let Me Know What You Think

This is something I've just started experiementing with, and you can see it on the navigation above but also in the footer below. I'd love to hear about how other people put this kind of thing to use, either in the comments on below on on twitter.

[attribute-selectors]: http://css-tricks.com/attribute-selectors/
[goingtoprint]: http://alistapart.com/article/goingtoprint
[micro-clearfix-hack]: http://nicolasgallagher.com/micro-clearfix-hack/
[Symbolset]: http://symbolset.com