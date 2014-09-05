---
layout: post
title:  "Simple Smart Quotes"
date:   "2012-12-14 10:25"
categories: posts
author: David Turner
twitter:
image:
  featured:
    src: /img/simple-smart-quotes.jpg
    alt: Simple Smart Quotes
    width: 1000
    height: 300
---
In a recent article I talked about shipping curly quotes in [Get Invited][], and that I'd then added it to my portfolio. I wanted to take a little time to talk about how I did this, as it turned out implementing it was a *lot* easier than I'd expected it to be.

##Boiling Down Complexity

When trying to figure out how to get smart quotes working I spent a *lot* of time, probably too much looking back, in trying to find a PHP function, or library, to automagically convert quotations from the "standard" quotes to their curlier equivalents.

I couldn’t find one, and that forced me to think about how I’d go about doing it myself. Normally character replacement is easy, you would just call a `str_replace()` function in PHP and be done with it. The problem with quotes is that the characters I’d be searching for are the same on both sides when dealing with standard quotes, but different when you convert them to their curlier equivalent.

This caused me to consider the option of working out a way to convert every other match to the corresponding opening quote, and the remaining ones to the closing quote. This would work for double quotes, but would fail horrible when dealing with single quotes, courtesy of apostrophes.

In the end I was able to implement a solution courtesy of [Tami Olsen][] who, as an author, had encountered similar issues in Microsoft Word. She suggested a solution that boiled down to looking for quotation marks with a space before or after them. A space before denotes that it is an opening quote. A space after denotes it is a closing one.

This, with a small number of edge cases that can also be processed, leaves remaining single quotes as apostrophes. I wrapped this up in a simple function and pushed it out to Get Invited. It worked *perfectly*. The code looked like:

{% highlight php startinline %}
function smartQuotes($str) {
  $search = array (
    " \"",
    "\" ",
    " "",
    "" ",
    " “\"",
    "\"” ",
    " ‘"",
    " "’",
    "..."
  );

  $replace = array (
    " ‘",
    "’ ",
    " “",
    "” ",
    " “‘",
    "’" ",
    " ‘“",
    " ”’",
    "…"
  );

  return str_replace("\"", "’", str_replace($search, $replace, $str));
}
{% endhighlight %}

##Not Issue Free

After building this into Get Invited I was quite pleased with how it looked, and it *vastly* simplifies issues with getting smart quotes into written text, as the shortcuts for curly quotes aren't nearly as easy to remember as the commands for the more commonly used characters. So I coded it into my portfolio.

It broke things. Pretty badly. What was causing it to mess up? There's *one* difference between how Get Invited uses this function and how my portfolio does, and it's a major one. Get Invited only processes text using the function, but my own site uses a basic templating system and the function made changes to the whole template.

This would include any HTML that was included, in particular HTML attributes, which would then cause certain important aspects of my site, such as classes, to stop registering correctly.

I was able to find a workaround for this, though I'm not as happy with it as I would like to be. In order to resolve this issue I needed to add two regular expression filters to find text inside of HTML tags, in order to find the attribute quotations. I was then able to replace any text that had been turned into curly quotes in error back into the intended quotes. The final function looks like this:

{% highlight php startinline %}
function smartQuotes($str) {
  $search = array (
    " \"",
    "\" ",
    " "",
    "" ",
    " “\"",
    "\"” ",
    " ‘"",
    " "’",
    "..."
  );

  $replace = array (
    " ‘",
    "’ ",
    " “",
    "” ",
    " “‘",
    "’" ",
    " ‘“",
    " ”’",
    "…"
  );

  $str = str_replace("\"", "’", str_replace($search, $replace, $str));
  $str = preg_replace("/<([^<>]+)>/e", "<" . str_replace("”", """, "$1") . ">", $str);
  $str = preg_replace("/<([^<>]+)>/e", "<" . str_replace("’", "\"", "$1") . ">", $str);
  return $str;
}
{% endhighlight %}

It *works*, but I feel that it could be better. I'd love to hear if anyone has any thoughts on how to improve this code, or alternatives that people have used in the past. You know where to find me.

[0]: /simple-smart-quotes/

[Get Invited]: https://getinvited.to/
[Tami Olsen]: https://twitter.com/keilantra/