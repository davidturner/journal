---
layout: post
title:  "Symbolset Sass Functions"
date:   "2013-03-22 15:03"
categories: posts
author: David Turner
twitter:
---
[Symbolset][] has a selection of, simply put, *awesome* icon fonts that make life easier when it comes to using icons on the web. Rather than creating static images of the icons, which can get unweildy and time consuming, you include a custom font and you're good to go.

Which is great, but sadly it comes with two issues:

1. Loading multiple files for icons can get quite unweildy, *especially* if you only need one of two icons.
2. The default CSS can get quite lengthy if you use it *as is*.

Fortunately the people providing the fonts [are working to fix the first issue][subsetting]. I thought I'd share one of the approaches I've been using for a while. I've [written about another][simple-css-goodness] in the past. This one's a bit more Sass-y.

I've put together a series of Sass functions that can be used to return the content you need based on keywords entered. I've managed to put together a series of mixins that cover the following fonts:

- Symbolset Standard
- Symbolset Social (and SS Social Circle)
- Symbolset Pika
- Symbolset Symbolicons Block (should work for Symbolicons Line too)
- Symbolset Gizmo

##How?

I've put together a Sass file on Github (link removed) that you can use in any Sass/Compass project. I've defaulted things to not include any fonts by default, you can enable fonts as you need them by changing any of the `0` values to `1`. You can also change the default font location by changing `'../fonts/'` to a value that suits your own file structure.

Once you've got the file included you can start using the Sass functions in your code. Each function requires a keyword, and will return the characters used in their respective Symbolset Font CSS. The keywords you'd use are the *exact* ones you see in the documentation for the fonts.

Example usage:

{% highlight css startinline %}
.rss:before {
  content: ss-standard-icon ( 'mail' );
}
{% endhighlight %}

This would return the output the following CSS:

{% highlight css startinline %}
.rss:before {
  content: '✉';
}
{% endhighlight %}

The different functions currently available are:

- `ss-standard-icon ( 'keyword' )` for Symbolset Standard
- `ss-social-icon ( 'keyword' )` for Symbolset Social (and Social Circle)
- `ss-pika-icon ( 'keyword' )` for Symbolset Pika
- `ss-symbolicons-icon ( 'keyword' )` for Symbolset Symbolicons
- `ss-gizmo-icon ( 'keyword' )` for Symbolset Gizmo

##Doesn't Include

Please note that this code does *not* include any of the Symbolset fonts, this is merely something that allows you to cut down on the amount of CSS in your code, because unnecessary code is never a good thing.

##Things to Note

I've found, whilst working out how best to automate this system, that Sass doesn't seem to like `if` statements past a certain number of options. You'll see that there are multiple functions called to return the right character. I found that these fonts simply had too many glyphs for Sass to be able to work their way through in a single function. If people are aware of any better way to implement this kind of thing (I'd *love* some kind of Sass switch function for this) then I'd love to hear it.

This is also a smaller part of a Sass toolbelt type framework I'm currently working on. If you find this useful and would like to play around with the more complete package let me know. I plan to release the full thing once I am happy with how it is structured and how it works.

<!-- [symbolset-sass-functions]: /symbolset/ -->
[Symbolset]: http://symbolset.com/
[subsetting]: http://help.symbolset.com/customer/portal/questions/872838-subsetting
[simple-css-goodness]: /simple-css-goodness/
[symbolset-sass-gist]: https://gist.github.com/DavidTurner/5222460