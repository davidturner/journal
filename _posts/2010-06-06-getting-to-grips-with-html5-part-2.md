---
layout: post
title:  "Getting to Grips with HTML5 - Part 2"
date:   "2010-06-06 17:45"
type:   posts
categories: posts
author: David Turner
twitter:
---
HTML5 introduces, changes and, in some cases, removes things. It streamlines some old elements and expands into new, more semantic areas. As I mentioned in the last article, there are new elements to help you set up basic areas of the site, such as the header, navigation, sidebars, content articles and footers. But there is a great deal more available. Let’s take a look, shall we?

#### Back to Basics – DOCTYPE

Some of the following may look familiar to you:

{% highlight html startinline %}
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
{% endhighlight %}

What’s that? They _do_? Any web designer who knows anything about coding understands the necessity of having a DOCTYPE declared for a web site. It helps to ensure things work properly in browsers, and lets them know what’s coming up in the code. HTML5 has a DOCTYPE too, though I’m sure this doesn’t shock you in the slightest. But things have changed. Things have **improved**. Want to see the HTML5 DOCTYPE? Here it is:

<pre class="brush: xml; title: ; notranslate" title=""><!DOCTYPE html></pre>

Complicated, isn’t it? All it does is tell the browser that it’s viewing an HTML document, and you’re golden.

#### Letting things go to your <head>

The head section of the site is an important one. It contains a great deal of information about the site, including information about the character set that your site is using. It also contains some important information that is useful for helping identify &amp; display your site, covering things such as your title, your style sheets, favicon and information about the content of the site, in the form of meta tags and descriptions. Some people, though not all, use it as an area to place their JavaScript.

HTML5 helps strip away some elements from this section, and helps streamline others. Below is an example of the code for a pretty standard XHTML Site:

{% highlight html startinline %}
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
		<title>Page Title</title>
		<link type="text/css" rel="stylesheet" media="screen" href="site.css" />
		<link rel="shortcut icon" href="" />
		<meta name="description" content="" />
		<meta name="keywords" content="" />
		<meta name='robots' content="noindex,nofollow" />
	</head>
{% endhighlight %}

Let’s compare that to how the template for my own site demos looks, just for comparison purposes, shall we?

{% highlight html startinline %}
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="utf-8" />
		<title>Page Title</title>
		<!--[if lt IE 9]>
		<script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
		<![endif]-->
		<link type="text/css" rel="stylesheet" media="screen" href="style.css" />
		<link rel="shortcut icon" href="" />
		<meta name="description" content="" />
		<meta name="keywords" content="" />
		<meta name="robots" content="noindex,nofollow" />
	</head>
{% endhighlight %}


There’s not a whole lot of difference between the two. The HTML5 declares the language is in and also specifies, in less space, the character set that will be used. The remaining content remains pretty much identical regardless. It should be noted, just for ease of use, I have continued using the self-closing / at the end of elements as was the norm with XHTML. This isn’t required with HTML5, it’s just something I have grown accustomed to over the years.

##### Wait… I spy JavaScript!

That’s correct, you do. I covered in the [last post](/getting-to-grips-with-html5-part-1/) that Internet Explorer doesn’t currently support HTML5 in any version currently available. The workaround for it consists of some JavaScript which forces these browsers to recognise the elements. Support for HTML5 elements _is_ a part of Internet Explorer 9 but, so far as I am aware, there is no release date set yet. This means that if you hate JavaScript, HTML5 is currently off limits to you.

#### Most people, however, are all about the <body>

Cheap pun I know, but when it comes to web design it _is_ almost all about the body. Your users don’t see your header. They don’t see your CSS or your JavaScript. What they _do_ see, however, is the body content of your site and the effects of your styling and your JavaScript. So what has changed here?

In the grand scheme of things, not a whole hell of a lot. Everything you used before in creating a web site will work _exactly_ the same in HTML5 as before. It’s part of the beauty of it all. You don’t need to learn anything new, but it adds a great deal of new tools to your set. Let’s take a look, shall we?

##### Out with the old (and in with the new)

HTML5 doesn’t change the game a whole lot with regards to layout and structure. It merely neatens things up and makes things more consistent. To do this there are several elements removed in the HTML5 specification but, to be honest, I’ve not encountered many of them at all in recent years and none are likely to be missed. The list of removed elements in HTML5 consist of:

*   basefont
*   big
*   center
*   font
*   s
*   strike
*   tt
*   u
*   frame
*   frameset
*   noframes
*   acronym
*   applet
*   isindex
*   dir

Honestly, I’m not going to be missing any of these elements as they have either been irrelevant for quite some time, courtesy of CSS, or superseded by newer technologies. As much as there has been stuff removed, there have also been some new elements added in that you are able to use. Some exist to make laying out your design more semantically, some exist to make your contents easier for search engines to understand and some, such as the video and audio tags, exist to make it easier for you to add multimedia to a page. The main new elements that you should concern yourself with, at this point, are:

*   section
*   article
*   aside
*   header
*   footer
*   nav
*   figure
*   figcaption
*   video
*   audio
*   time

Whilst there are several others, several of these aren’t currently supported enough to make them usable. I would expect this to change over the coming months. In addition to new elements there are also new attributes for elements. Whilst many of these aren’t supported yet, or are self explanatory, it is possible to make use of some of them to help future-proof your code.

This is _especially_ true with form elements, as unsupported input types default to text inputs when they are unsupported in current browsers. It should be noted that this can cause problems with certain JavaScript Plugins from libraries such as jQuery and Mootools, as these often specify which elements they support.

##### New Ways to Embed

HTML has always provided way to provide various types of content. Images are as simple as using the img tag. HTML5 looks to expand beyond this introducing methods to embed both audio and video in web pages. This area of the HTML5 spec is currently undergoing some shifts and is a topic I intend to cover at a later date in more depth.

### Coming Soon!

I _had_ intended to cover the ins and outs of making the shift to HTML5 in this article. Clearly this hasn’t happened. In writing this article I believed that it was getting to be a bit unwieldy in terms of length and structure, covering too much in one go. As a result I will be covering shifting from XHTML to HTML5 in my next article, paying more attention to the code aspect rather than discussing what has changed.

### References

*   Anne van Kesteren. 2010. _HTML5 differences from HTML4_. [ONLINE] Available at: [http://www.w3.org/TR/html5-diff/#backwards-compatible](http://www.w3.org/TR/html5-diff/#backwards-compatible). [Accessed 28 May 10].