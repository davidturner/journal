---
layout: post
title:  "Presto Chango"
date:   "2013-02-15 10:18"
categories: posts
author: David Turner
twitter:
---
This week marks another step forward for me. I've received my last mark for my Masters, it has been confirmed that I've passed. Excellent, but where to next? The answer, with me, is *always* onwards.

Yesterday marked a step forward for me, I've made some adjustments to the site. Some of them are quite noticeable, others are under the hood. All of it has been done with a goal in mind, that of getting me to be more active on the site.

<!--[More]-->

##Design

I've changed the overall design quite a bit as a part of the process of updating things, but I have maintained a consistent visual style. I look at it as more of an iteration than a redesign. What I had before wasn't bad, but I was capable of producing something *better*.

Text is now larger, and fills out across a larger area, the full column rather than the previous half column. A lot of what I do is text heavy, and keeping things constrained in such a small column was proving troublesome for the writing that I do.

As a part of this I have rethought how I want certain elements to appear in the design. I don't use graphics terribly often on my site, so when they do appear, I want them to stand out.

The same is true of certain other elements in my writing. In addition to images, code blocks and blockquotes are displayed across the full width of the site, though any written elements will be kept to the same width as other written content.

##Development

I've also made a few adjustments to the site under the hood. I've stripped out my previous code syntax highlighter, PrettyPrint, and replaced it with the rather lovely [prism][] syntax highlighter. It's a lot lighter, and supports (after a *little* work) all of the languages I write in.

This helps make things just a little bit snappier, but I really wanted to speed things up when it comes to loading content. I already cache my site, so that you're almost never loading something generated on the server side, but could I do better? Yes.

I already use jQuery on my site for certain things, which made implementing the [pronto][] plugin an easy choice for me. Pronto allows a site to update just the main content of a site, rather than downloading the whole page each time. Smaller download, faster loading.

This required some tinkering with how my pages are generated. Pronto uses a JSON based structure to update the content, whilst the average page load will return a complete HTML page. Fortunately pronto makes the process of telling when JSON is needed quite easy.

Pronto attaches a `GET` variable of `pronto` when it's requesting a specific page. Using this I was able to determine whether or not to return JSON or HTML. I've also been able to cache the returned JSON, so everything should be pretty smooth. You can check out the [pronto data for this page][pronto-this-page] if you'd like.

I've also put some thought into how I'm going to be handling images on the site going forward. I'm a big fan of the [adaptive images][] approach to handling images. Set a cookie that tells a script how large the screen viewing the site is, and use a script to process images so that the image is at an optimal size.

I've also become quite the fan of [compressive images][], the idea of making an image larger in terms of dimensions, but dropping the image quality right down, and then letting the browser scale the image down. This results in an image of comparable quality that is much smaller than a higher quality image would be.

> I cannot overstate my love of [ImageOptim][]. If you use images on the web, and use a Mac, you should be using this.
{: .pullquote}

I've combined both of these approaches on my site. Smaller devices get smaller versions of the image, but they're still large images that get scaled down. The savings have been quite impressive. Each image on my portfolio was taken as a full screen image at 1920px by 1200px, cropped slightly, and then blown up to 200% of their original size to get a final size of 3840px by 2320px. They saved out at about 250kb, and when processed through [ImageOptim][] this size was cut by about 50%. By contrast images saved at the original size, with a decent level fo quality, where coming in at sizes up to **eight** times this size. *Madness!*

I also managed to resolve a long standing issue with my site when dealing with the responsive versions of this site. The day before launching, ironically the day Opera announced it will be switching to webkit for their rendering engine, I managed to resolve an issue that I had been having with Opera displaying my responsive navigation.

##Comments On

Finally, I've flipped the switch on site comments back over to on. I'm not sure that this will last, as spam bots seem to quite love harassing comment systems and I'm not sure that the hassle of dealing with them is worth the comment goodness I get. The quantiy of spam can get quite insane at times.

I'll likely be tweaking things over the forseeable future, and I'll be adding more content to the site as things progress. Feel free to sound off on things either on the comments below or hit me up on [twitter][].

[prism]: http://prismjs.com/
[pronto]: http://www.benplum.com/projects/pronto/
[pronto-this-page]: ?pronto=true
[adaptive images]: http://adaptive-images.com/
[compressive images]: http://www.filamentgroup.com/lab/rwd_img_compression/
[ImageOptim]: http://imageoptim.com/
[twitter]: https://twitter.com/intent/tweet?original_referer=&source=Presto%20Chango%20%E2%80%A2%20Portfolio%20of%20David%20Turner&text=@HerrWulf