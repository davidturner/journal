---
layout: post
title:  "Optimising Your Site: Images"
date:   "2012-06-19 15:12"
categories: posts
author: David Turner
twitter:
image:
  featured:
    src: /img/minority-report-image-sprite.jpg
    alt: "Optimising Your Site: Images"
    width: 1000
    height: 400
---
In my article [last week][1] I wanted to give an overview of some of the basic ways in which we can optimise sites, primarily for speed but also for the general well-being of sites in general. This week I want to take a look at one area I mentioned, and drill a bit deeper.

##Images

Images are a tricky beast to tackle, especially when it comes to getting things 100% right. But there are steps we can take to ensure that we have done all that we can, even if it's not perfect. In a way it mirrors how the internet is itself pretty awesome, but still not perfect.

So when it comes to dealing with images where do we start? The three key areas I'd look at are:

1. Image Dimensions
2. Image Compression
3. Image Sprites

###Image Dimensions

The larger an image is in terms of dimensions the larger the file size is going to be. It's an exponential growth too. A 100px by 100px image is going to be roughly a quarter of the size of a 200px by 200px image. It's a quarter of the size, both in terms of pixelage and size.

So don't use an image that is larger than it needs to be. If you're displaying an image at 300px by 200px then ensure the image is that size, not 600px by 400px. To highlight this I'm going to make an example of one of my partners in crime, [Kyle Gawley][].

![Comparison of Image Sizes][i2]

On Kyle's [portfolio site][2] he has four images. Each one of them is scaled down by default (**Note:** Caveat [down below](#caveat)). The images he uses for his latest work are scaled down from 400px by 200px to 288px by 144px. It's not *that* big of a difference in terms of size, right?

There is a difference though. Of the two versions of the [Vizuali][] the largest is 11KB in size. The smaller graphic, which is the size at which the image is actually rendered, is 8KB. That's almost a 30% saving just for using a version of the image at the right size.

Take that 30% and multiply it by three images, and you can see that the savings can mount up. Every KB cut out is a slightly faster loading time. These savings can really mount up on the more graphical sites out there.

<p id="caveat" markdown="1">There *are* exceptions to this, as there are with everything. In the case of Kyle's site the images are rendered in full size, but only at certain breakpoints in his responsive design. This initally slipped past unnoticed. It serves, quite nicely, to re-enforce that these serve as *guidelines*. Once you understand them you can choose to break them.</p>

###Image Compression

Whilst cutting down on the dimensions of an image cuts down on the file size, we can go further. I touched upon the importance of [compressing content][3] last week, but spoke only in general terms. Let's get a bit more specific shall we?

The comparison I listed above of the two versions of the Vizuali image has been run through [ImageOptim][], an application that does all that it can to cut down on image file sizes. I've also taken the liberty of preserving an [uncompressed version][4] of the image so you can compare the two.

![ImageOptim working it's compression magic][i3]

I don't pretend to understand the magic that makes software like ImageOptim work the way that it does, but a 16% saving on a 1000px by 300px image isn't something to be scoffed at. Again, even the smallest savings mount up, and it *all* comes together to create a faster site.

###Image Sprites

Image sprites are worth considering only if you are using a lot of smaller graphics in a site. You don't want to be combining a series of photos into a sprite, but if you're using image based icons then it's something to think about.

Why would you do this? As it turns out it's better for a couple of reasons, which Chris Coyier talks about in more detail over in an [article on CSS Tricks][5]. But at a basic level the final image is smaller and it results in less HTTP requests.

Every HTTP request takes time as you're communicating with a server, waiting for a result, and then transferring the data so it can be displayed. The more requests you make the slower things can get. So if you can remove some of them by using an image sprite, it's worth doing.

The hardest part of using an image sprite is creating them. Back in *my* day you could spend days wrestling with pixels to get things *just* right. Forunately things have changed since then, and they've changed for the better.

When it comes to working with sprites my best advice is *don't*. Not until you've finalised the design. Changing sprites isn't a pleasant experience, and is one I would recommend avoiding. When you've finalised a design, use a tool like [Sprite Cow][] to piece together all the images you need *and* help generate all the CSS you'll need.

What more could you want from a tool?

##Image Alternatives

Not everything needs to be an image these days. Web technologies are continually evolving. And the people that use them are crafty devils. We have @font-face allowing for the use of [fonts in the place of social icons][6], the advances in CSS3 allow you to combine images with CSS to create [awesome results][7], and advances in browser technologies allow for increasing use of [alternative technologies][8] in place of standard images.

A lot of the alternatives are really widely supported, and those that aren't usually degrade in a way that doesn't completely ruin things. It really is a great time to be working on the web. I want to talk breifly about the following:

1. @font-face
2. CSS3
3. SVG

###@font-face

Font face has become highly popular of late, with plenty of services such as [typekit][] providing access to an ever increasing amount of fonts we can use online. The fonts can be used for more than just body text and headings. They can be used to create simple icons.

![@font-face in action - social media icons][i4]

Above is a snap from a concept I'm tinkering with for a client site I'm currently redesigning. The icons for Facebook, Twitter, and YouTube are all icons displayed using @font-face. They've been put in place by some CSS to ensure that they make sense to users that are using assistive technologies. The icon is added to text that is currently hidden from view.

That is just one example. Think of how many buttons are used in services like email, or any other online system you're using. Quite a few of them use image sprites for these graphics, which is fine. But it's possible that they could be better if they looked at using an icon font instead.

###CSS3

CSS3 has brought a lot of new things to the stylesheet. Many of them were only previously available if using images and a lot of dirty hacks. Lots of images in a great many cases. The power provided to us by these advances is immense.

![BonBon buttons by simurai][i5]

[BonBon Buttons][] provides a glimps of what is possible. An extreme case, but an amazing one. As recently as a few years ago these kinds of buttons would only have been possible using images. But these are pure CSS. Amazing.

Of course the power of CSS3 goes far beyond the ability to style buttons nicely. You have an immense set of tools at your fingertips that, if used well, can create amazing effects. The key is, and has always been, in consideration of when and *how* to apply such things.

###SVG

SVG is one of those languages that has been around for a *long* time, but it's really starting to see some love on the internet. I'm not sure that I can really do SVG justice, as I am only just getting to grips with it. It allows for vector image use on the web without loading an image, as SVG is an XML based language.

![Some basic SVG][i6]

The above is a mix of some CSS and a chunk of SVG. I used SVG for the bottom part of the join, the transparent white block with a semi-circle removed from it. I tried using a PNG file but, for reasons that escape me, I couldn't get an image that would work. As I mentioned, SVG is all code, and the code I used for this was:

{% highlight xml %}
<svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="1000px" height="60px" viewBox="0 0 1000 60" style="enable-background:new 0 0 1000 60;" xml:space="preserve">
  <path style="opacity:0.6;fill:#fff;" d="M553.501,0c-4.749,25.543-27.137,44.889-54.057,44.889
    	c-26.919,0-49.307-19.346-54.056-44.889H0v60h1000V0H553.501z"/>
</svg>
{% endhighlight %}

That's not a lot of code. You can copy and paste it into your HTML and, so long as you don't have a white background, it'll work for you. All without loading in an external image.

Unfortunately I can't cover it in more detail, as I have only just begun to scratch the surface of what is possible. The potential is definitely there though.

##And That's A Wrap

We are visual thinkers. If someone says “cheese” you conjure up an image of cheese, not the word itself. This makes images an important part of communicatin information online. Getting the right image is only half the battle however. Getting it to the user of your site is the rest.

I've taken a look at some of the key ways that you can help do this more efficiently, and I've also taken a look at some of the alternatives out there that you can consider for some things. Use what works to say what you want to say. Then make sure to say it.

Want to add something to what I've said? Chime in below on the comments or [hit me up on twitter][9].

[0]: /optimising-your-site-images/
[1]: /optimising-your-site-the-basics/
[2]: http://kylegawley.com
[3]: /optimising-your-site-the-basics/#compress-content
[4]: /img/vizuali-comparison-uncompressed.jpg
[5]: http://css-tricks.com/css-sprites/
[6]: http://fontfabric.com/social-media-icons-pack/
[7]: http://duckbox.net/tests/jonnyMenu.php
[8]: http://www.alistapart.com/issues/299
[9]: https://twitter.com/intent/tweet?original_referer=&source=Optimising+Your+Site%3A+Images&text=@HerrWulf&url=https://davidturner.name/journal/optimising-your-site-images

[Kyle Gawley]: http://twitter.com/kylegawley
[Vizuali]: http://vizua.li
[ImageOptim]: http://imageoptim.com/
[Sprite Cow]: http://www.spritecow.com/
[typekit]: https://typekit.com/
[BonBon Buttons]: http://simurai.com/archive/2010/09/02/bonbon-buttons/

[i2]: /img/vizuali-comparison.jpg
[i3]: /img/image-optim-compression.jpg
[i4]: /img/social-icons-font-face.jpg
[i5]: /img/css3-buttons.jpg
[i6]: /img/some-basic-svg.jpg