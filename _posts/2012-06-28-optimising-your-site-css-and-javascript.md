---
layout: post
title:  "Optimising Your Site: CSS & Javascript"
date:   "2012-06-28 18:57"
categories: posts
author: David Turner
twitter:
image:
  featured:
    src: /img/hand-optimised-code.jpg
    alt: "Optimising Your Site: CSS & Javascript"
    width: 1000
    height: 400
---
At the [start of this series][1] of posts I gave an overview of some of the best ways to start optimising a site. Last week I looked [more in-depth at images][2] and this week I want to turn my attention to the other files I brought up: CSS and JavaScript.

##CSS & JavaScript

These are fundamental building blocks of the internet, alongside HTML and CSS adding visual effects to sites and JavaScript adding additional functionality and interaction to sites. As a result it isn't all that hard to see them becoming quite large files. Which isn't really ideal.

Whilst CSS and JavaScript are entirely different types of content, and are written differently, the approaches to optimising them overlap and, in some cases, are identical. The guidelines I follow are:

1. One CSS file, one JavaScript File
2. *Always* place CSS before JavaScript
3. CSS goes in the `<head>`, JavaScript before `</body>`
4. Compress and Minify content for deployment
5. CSS Preprocessors are *awesome*

As with all guidelines there are exceptions that I afford. I'll cover them in the relevant areas below.

###One CSS File, One JavaScript File

I default to using a single CSS file and a single JavaScript file. This provides a maximum level of efficiency when it comes to loading. One HTTP request for CSS, one HTTP request for JavaScript and then we're good to go.

The big exception to this is when using a CDN (Content Delivery Network) to deliver JavaScript Libraries. These files generally aren't that small, and by using a CDN you can help mitigate some file loading times.

How? A CDN is a way to deliver certain files quickly in a global manner. If you're in Europe you get the file *from* Europe. The same is true in the Americas. But, better yet, these files are *cached*. So if someone else uses the same CDN as you to serve the same JavaScript file as you then the user doesn't have to download the same file when they visit your site. They have it already.

In addition to that it also lightens the load on your own site, as you're not having to serve a larger file that includes whichever library you're using.

###*Always* Place CSS before JavaScript

JavaScript files block the rest of a site from loading. Whilst there are instances where this is fine (I'll touch on this in the next area) you always want to have the CSS ready to go when the body of a site is rendering. The alternative is that your site looks sloppy, as if you don't care about your users. That's never good.

Little things like this don't seem important, but can have unforseen consequences if you don't properly consider them. Which leads nicely to the next point.

###CSS goes in the `<head>`, JavaScript before `</body>`

The order of files is important in terms of page loading and rendering times. JavaScript will, for the most part, block content beneath it from loading. This can cause pages to appear to be slower loading. So we want to ensure that doesn't happen.

An example of this in action is a project I worked on over a year ago, called [ReferenceIt][]. There are a few key things to note. The first is in this cut down version of the `<head>` element:

{% highlight html startinline %}
&lt;head&gt;
  &lt;link rel=&quot;stylesheet&quot; media=&quot;screen&quot; href=&quot;https://referenceit.org/-assets/css/site.live.css&quot; /&gt;
  &lt;script src=&quot;//cdnjs.cloudflare.com/ajax/libs/modernizr/2.5.3/modernizr.min.js&quot;&gt;&lt;/script&gt;
&lt;/head&gt;
{% endhighlight %}

There are two things of note here. A single CSS file and, what's that, JavaScript? In *my* `<head>` element? Well, yes. Which leads to my first exception to this guideline. HTML5Shiv and Modernizr need to be in the `<head>` in order to get Internet Explorer to understand HTML5 elements.

If we carry on down the site we'll see that there's some more JavaScript waiting for us:

{% highlight html startinline %}
  &lt;script src=&quot;//ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js&quot;&gt;&lt;/script&gt;
  &lt;script src=&quot;/-assets/js/site.live.js&quot;&gt;&lt;/script&gt;
&lt;/body&gt;
{% endhighlight %}

This is the *real* JavaScript that's running on the site, and it's left until the *very* end of the site. This lets the rest of the content on the site load as quickly as possible before layering extra functionality on top of the site. This lets the user get straight to *using* the site, without waiting on things to finish downloading.

###Compress and Minify Content for Deployment

There are really two different stages to a site. Development of the project and the live version of a project. Each has it's own nuances that need to be taken into consideration. For instance, when developing something you want to be able to quickly identify *what* is causing problems if something goes wrong.

By the time you're launching a project such problems shouldn't exist, which affords us the ability to make some savings in terms of space. We do this using the wonderful technologies of compression and minification.

I'll stick with the example I used above, ReferenceIt. You saw in the footer there was a reference to a file called `site.live.js`. You can view it [here][3]. As you can see, it's pretty clustered together. I didn't write this file. The file I wrote can be viewed [here][4].

There's quite the difference in looks, isn't there? This is a principle I apply to both my JavaScript *and* my CSS, though it's much more effective with JavaScript as when minifying variable names can be reloaded. What does my CSS look like then? It looks a lot like [this][5], though it starts out quite differently.

Why do this? The savings in terms of file size can mount up. The JavaScript I use isn't *that* large, but by serving it as a compressed and minified file, I make a saving of about 20-25%. Think about how much space could be saved with *larger* files.

Compressing and minifying JavaScript is simplified greatly using tools like [CodeKit][] and [LiveReload][]. CSS is a bit more fiddly. Compressing it, natively, usually requires a bit more in terms of manual effort. There's an alternative though, which I'll cover below.

###CSS Preprocessors are *Awesome*

I mentioned above that the CSS for ReferenceIt starts out quite differently. That's because I didn't write it as CSS *at all*. Instead I used a language called [LESS][], a language that builds upon CSS but is compiled into the CSS that browsers know and love. Nowadays I use [SASS/SCSS][], but the principles remain the same.

Preprocessors allow you to us a load of fantastic things in addition to the CSS you know and love. The biggest features for me:

- Automatic CSS Compression
- Usage of Variables
- Mixins

####Automatic CSS Minification

This is probably the biggest win for me. I can write CSS that is perfectly human readable and have it compressed into the file I want to be served to browsers. This makes tweaking things nice and easy too. Save, upload, done.

####Usage of Variables

Variables are handy for a lot of things. I mainly use them to store colours and dimensions, which allows me to quickly change the layout or design of a site by changing just a few elements of code.

####Mixins

Think of mixins as functions and you're pretty much there. Rather than writing multiple lines of `border-radius` CSS you can just call a function and have it work it all out for you. I use this with great results in [960-LESS][], a flexible grid framework I now use in SCSS.

####There's More

I couldn't do preprocessors justice in this post, there's too much to cover for it to be just a part of a larger topic. Chris Coyier has done a great series of articles on this topic however, and they are well worth a read:

- [Musings on Preprocessing][6]
- [SASS vs. LESS][7]

##And That's A Wrap

I wanted to take a bit of a more in-depth look at ensuring that everything that can be done to save in terms of file space *has* been done. It's important to get this aspect of things right before I talk about the next area of how to optimise your site, which will be dealing with caching of files and a few other technical areas which go hand in hand with caching files.

As always your comments are appreciated, both below in the comments area and [on twitter][8].

[0]: /optimising-your-site-css-and-javascript/
[1]: /optimising-your-site-the-basics/
[2]: /optimising-your-site-images/
[3]: https://referenceit.org/-assets/js/site.live.js
[4]: https://referenceit.org/-assets/js/site.js
[5]: https://referenceit.org/-assets/css/site.live.css
[6]: http://css-tricks.com/musings-on-preprocessing/
[7]: http://css-tricks.com/sass-vs-less/
[8]: https://twitter.com/intent/tweet?original_referer=&source=Optimising+Your+Site:+CSS=&amp;+JavaScript&text=@HerrWulf&url=http://davidturner.name/journal/optimising-your-site-css-and-javascript

[ReferenceIt]: https://referenceit.org
[CodeKit]: http://incident57.com/codekit/
[LiveReload]: http://livereload.com/
[LESS]: http://lesscss.org/
[SASS/SCSS]: http://sass-lang.com/
[960-LESS]: https://github.com/DavidTurner/960-LESS