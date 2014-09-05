---
layout: post
title:  "PHP Generated Mosaic"
date:   "2010-06-10 16:58"
type:   posts
categories: posts
author: David Turner
twitter:
---
This particular piece of experimentation came about as a result of needing to get reacquainted with PHP's ability to generate images. Why? I was working on an image related piece of script and, at the time, couldn't find anything suitable. It also gave me a chance to reacquaint myself with PHP scripting for something other than handling Database Content.

##How?

PHP has a great deal of functionality when it comes to generating content to be displayed on a website. One thing it can't do, by itself, is produce images. To do this it needs a little bit of help, in the form of the GD Library, which enables image generation with PHP. Two files were needed to generate the example. The first was the file that loops through all of the required number of images to get them displayed, and the second generating the images, which looks something like this:

{% highlight php startinline %}
$w = $_GET['w'];
$h = $_GET['h'];
$r = rand(0,255);
$g = rand(0,255);
$b = rand(0,255);
header("Content-type: image/png");
$im = @imagecreate($w, $h) or die('Cannot Initialize new GD image stream');
$background_color = imagecolorallocate($im, $r, $g, $b);
imagepng($im);
imagedestroy($im);
{% endhighlight %}

This allows for easy image genration, passing in variables for the required width and height. Click the link below to see an example of it in action.

**Update:** I've updated the demo to use css backgrounds generated using PHP rather than generating multiple images using PHP. The updated code is:

{% highlight php startinline %}
function image(){
	$r = rand(0,255);
	$g = rand(0,255);
	$b = rand(0,255);
	return $r.','.$g.','.$b;
	unset($r);
	unset($g);
	unset($b);
}
$total = 30*20*20;
$start = 0;
while($start &lt;= $total){
  echo '&lt;span style=&quot;display:inline-block;width:32px;height:32px;background:rgb('.image().');&quot;&gt;&amp;nbsp;&lt;/span&gt;';
	$start = $start+1;
}
{% endhighlight %}

A demo of this can be viewed [here][1].

[0]: /php-generated-mosaic/
[1]: /php-generated-mosaic/