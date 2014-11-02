---
layout: post
title:  "Getting to Grips with HTML5 - Part 3"
date:   "2010-07-09 15:42"
type:   posts
categories: posts
author: David Turner
twitter:
---
Well this article has been a while in coming. One of the side effects of freelancing is that, sometimes, you have to set aside some of your other projects to let yourself meet client deadlines. Fortunately I have been making progress with this article throughout this time, and I’m finally in a position to dedicate some time to getting this article live.

In case you haven’t been following the series, in Parts 1 &amp; 2 I have been dealing with some of the basic aspects of HTML5, covering the [aspects of HTML5 support](/getting-to-grips-with-html5-part-1/) in Part 1 and discussing the [changes that exist](/getting-to-grips-with-html5-part-2/) between XHTML and HTML5. Today’s article focuses on what I believe to be an interesting topic, how to convert an already existing XHTML Site into an HTML5 design.

Quite some time ago now I asked on Twitter for suggestions about sites that I could use as the basis of this article. David Hatch, the person responsible for the hosting of this very site, suggested another of his sites as the basis of the article. [MiniGameReviews](http://minigamereviews.com/) is a web site that reviews games in 140 characters or less, rating them on a scale of 0 to 9.

### Small Steps – Clean Slate

There are two ways to go about converting a site. You can either work through manually converting the existing code over, or you can recode things from scratch. Whilst it might seem odd to recode something that already exists, it is my experience that it’s generally less problematic in the long term, and can be much easier to develop quickly. It’s also the approach that I will be taking with this article.

Over Time I’ve put together a series of templates that I make use of for helping me develop sites. These templates cover elements of both HTML and CSS. Some aspects of the design are based on the [960 Grid System](http://960.gs/) to help in terms of layout, as well as Eric Meyer’s CSS reset modified to handle the new HTML5 Elements. At this point we have two files, which look like the following:

#### HTML5 Template

{% highlight html startinline %}
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<!--[if lt IE 9]>
		<script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
		<![endif]-->
		<link type="text/css" rel="stylesheet" media="screen" href="style.css" />
		<link rel="shortcut icon" href="" />
		<meta name="description" content="" />
		<meta name="keywords" content="" />
		<!--<meta name="robots" content="noindex,nofollow" />-->
	</head>

	<body>

		<script src="http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js" type="text/javascript"></script>
		<script type="text/javascript">
			$(function() {

			});
		</script>
	</body>
</html>
{% endhighlight %}

This provides for the basic structure of a site’s design. It covers the HTML5 DOCTYPE as well as the majority of the head section of the site, with some added jQuery script capabilities added in just before the end of the site. This is done to ensure a quick loading time for the content of the site, which stands out to me as the most important aspect of any site.

#### CSS

{% highlight css startinline %}
/******** GLOBAL RESET ********/
/* http://meyerweb.com/eric/tools/css/reset/ */
/* v1.0 | 20080212 */
html,body,div,span,applet,object,iframe,h1,h2,h3,h4,h5,h6,p,blockquote,pre,a,abbr,acronym,address,big,cite,code,del,dfn,em,font,img,ins,kbd,q,s,samp,small,strike,strong,sub,sup,tt,var,b,u,i,center,dl,dt,dd,ol,ul,li,fieldset,form,label,legend,table,caption,tbody,tfoot,thead,tr,th,td,header,section,footer,aside,nav,article,figure {margin:0;padding:0;border:0;outline:0;font-size:100%;vertical-align:baseline;background:transparent}
body {line-height:1}
header,section,footer,aside,nav,article,figure {display:block}
ol,ul {list-style:none}
blockquote,q {quotes:none}
blockquote:before,blockquote:after,q:before,q:after {content:''}

/* remember to define focus styles! */
:focus {outline:0}

/* remember to highlight inserts somehow! */
ins {text-decoration:none}
del {text-decoration:line-through}

/* tables still need 'cellspacing="0"' in the markup */
table {border-collapse:collapse;border-spacing:0}

/******** 960 GRID ********/
.container_12,.container_16 {margin-left:auto;margin-right:auto;width:960px;overflow:hidden}
.grid_1,.grid_2,.grid_3,.grid_4,.grid_5,.grid_6,.grid_7,.grid_8,.grid_9,.grid_10,.grid_11,.grid_12,.grid_13,.grid_14,.grid_15,.grid_16 {display:inline;float:left;margin-left:10px;margin-right:10px;width:auto}
.container_12 .grid_3,.container_16 .grid_4 {width:220px}
.container_12 .grid_6,.container_16 .grid_8 {width:460px}
.container_12 .grid_9,.container_16 .grid_12 {width:700px}
.container_12 .grid_12,.container_16 .grid_16 {width:940px}
.alpha {margin-left:0}
.omega {margin-right:0}
.container_12 .grid_1 {width:60px}
.container_12 .grid_2 {width:140px}
.container_12 .grid_4 {width:300px}
.container_12 .grid_5 {width:380px}
.container_12 .grid_7 {width:540px}
.container_12 .grid_8 {width:620px}
.container_12 .grid_10 {width:780px}
.container_12 .grid_11 {width:860px}
.container_16 .grid_1 {width:40px}
.container_16 .grid_2 {width:100px}
.container_16 .grid_3 {width:160px}
.container_16 .grid_5 {width:280px}
.container_16 .grid_6 {width:340px}
.container_16 .grid_7 {width:400px}
.container_16 .grid_9 {width:520px}
.container_16 .grid_10 {width:580px}
.container_16 .grid_11 {width:640px}
.container_16 .grid_13 {width:760px}
.container_16 .grid_14 {width:820px}
.container_16 .grid_15 {width:880px}
.container_12 .prefix_3,.container_16 .prefix_4 {padding-left:240px}
.container_12 .prefix_6,.container_16 .prefix_8 {padding-left:480px}
.container_12 .prefix_9,.container_16 .prefix_12 {padding-left:720px}
.container_12 .prefix_1 {padding-left:80px}
.container_12 .prefix_2 {padding-left:160px}
.container_12 .prefix_4 {padding-left:320px}
.container_12 .prefix_5 {padding-left:400px}
.container_12 .prefix_7 {padding-left:560px}
.container_12 .prefix_8 {padding-left:640px}
.container_12 .prefix_10 {padding-left:800px}
.container_12 .prefix_11 {padding-left:880px}
.container_16 .prefix_1 {padding-left:60px}
.container_16 .prefix_2 {padding-left:120px}
.container_16 .prefix_3 {padding-left:180px}
.container_16 .prefix_5 {padding-left:300px}
.container_16 .prefix_6 {padding-left:360px}
.container_16 .prefix_7 {padding-left:420px}
.container_16 .prefix_9 {padding-left:540px}
.container_16 .prefix_10 {padding-left:600px}
.container_16 .prefix_11 {padding-left:660px}
.container_16 .prefix_13 {padding-left:780px}
.container_16 .prefix_14 {padding-left:840px}
.container_16 .prefix_15 {padding-left:900px}
.container_12 .suffix_3,.container_16 .suffix_4 {padding-right:240px}
.container_12 .suffix_6,.container_16 .suffix_8 {padding-right:480px}
.container_12 .suffix_9,.container_16 .suffix_12 {padding-right:720px}
.container_12 .suffix_1 {padding-right:80px}
.container_12 .suffix_2 {padding-right:160px}
.container_12 .suffix_4 {padding-right:320px}
.container_12 .suffix_5 {padding-right:400px}
.container_12 .suffix_7 {padding-right:560px}
.container_12 .suffix_8 {padding-right:640px}
.container_12 .suffix_10 {padding-right:800px}
.container_12 .suffix_11 {padding-right:880px}
.container_16 .suffix_1 {padding-right:60px}
.container_16 .suffix_2 {padding-right:120px}
.container_16 .suffix_3 {padding-right:180px
.container_16 .suffix_5 {padding-right:300px}
.container_16 .suffix_6 {padding-right:360px}
.container_16 .suffix_7 {padding-right:420px}
.container_16 .suffix_9 {padding-right:540px}
.container_16 .suffix_10 {padding-right:600px}
.container_16 .suffix_11 {padding-right:660px}
.container_16 .suffix_13 {padding-right:780px}
.container_16 .suffix_14 {padding-right:840px}
.container_16 .suffix_15 {padding-right:900px}
{% endhighlight %}

At this point there’s no content and a rather excessive amount of CSS code to handle all of it. CSS Frameworks tend to result in a lot of excessive code but this is something to deal with later, by removing any unnecessary code from the CSS _after_ the project is completed.

Why after? Whilst you may think that you know what you want to use in your design, things may change, or evolve, over the course of the design. It’s better to not need something and have it than need something and for it to not be there.

### Adding Structure & Content

Now that we have the basic elements of the site in place, we can start to add in some actual structure and content into the design. One of the nice things about making the move from XHTML to HTML5 is that, for the most part, the content of the site can be easily reused, which very little effort required. This is exactly the case with this site, converting a few div elements into headers, sections asides and articles and the vast majority of the HTML layout is complete. At this point, even without styling, you can see the comparisons between the shapes and layout of the site.

From this point, all that remains is the CSS styling to provide the look and feel to the site, making it look like the original design. For the most part this is the same as with the HTML elements of the site, changing a few divs into other elements to ensure they are styling the right elements as well as, in this case, adjusting some numbers to match with the changes I made to the layout, making use elements fit together properly. With that, the process is pretty much complete. The current version of the site is available to be viewed [here](http://minigamereviews.com/) and the HTML5 version of the site can be found [here](https://davidturner.name/demos/minigamereviews-html5/).

### Conclusions

On the whole there’s not a great amount of difference between a site coded using XHTML and a site produced using HTML5. There are a few differences, mainly with the elements used for site structure. Whilst there are other advances made with HTML5, such as audio and video elements, they aren’t used in this particular design.