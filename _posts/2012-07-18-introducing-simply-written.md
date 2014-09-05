---
layout: post
title:  "Introducing Simply Written"
date:   "2012-07-18 10:09"
categories: posts
author: David Turner
twitter:
---
In the design community there is a *lot* of sharing. Information, ideas, concepts, and suggestions. Feedback, criticism, and Q&A sessions. There's a *lot* of consumption. People wouldn't share the things they do if nobody was noticing them.

Sharing things online is great, but putting content up online isn't always the best medium for sharing. There are alternatives, most notably digital publications. They have a lot in common with online content, but creating the formats for them can be troublesome. I'd like to change that.

##Meet Simply Written

Simply Written is a project I've been working on for quite some time now. The idea first appeared in the autumn of 2011, and the first real “demo” cropped up in January before it took a back seat to [other projects][1]. Last week I took the time to resolve this, and I feel it's now ready for sharing with the world.

At its core, Simply Written exists as a service, a system, to allow authors and writers to create content that can be wrapped up into multiple book formats with ease. Right now it works with ePub and mobi (Kindle uses the format) but I intend to add PDF support once I figure out the best approach to doing so.

In my experience most digital books aren't created, they are *converted*. This leads to sub-par books, as machines aren't good enough to get the conversion process right. We could sit and wait for them to become good enough, or we could use something that works now. *You*.

Simply Written uses you, as the author of your content, to work out how content should be structured. It processes what you write into a format that can be used in any of the popular digital media readers. Rather than *converting* content, it *processes* it, wrapping it up in the relevant code to make an ePub file, or a mobi file.

###How?

Simply Written takes a complex process and simplifies it. It's actually not that difficult to create an ePub file from static HTML content. Working with mobi files is a bit trickier, there's some extra bits needed and some that need removed, but the format can be generated from the same content as an ePub file.

It is, however, *tedious*, and it takes up time. That time could be better spent writing, or having fun. So Simply Written takes the tedious parts of book creation and leaves you with the most fundamental area of digital book authoring, the authoring part. You create your content, and Simply Written will handle the rest.

###Why?

Over the course of this year I have really grown to enjoy writing content, content that I believe is *good*. I have always enjoyed sitting down with a good book and getting lost in it. With the shift towards digital, and being able to carry a whole collection of books in my iPad, I have embraced digital books quite happily.

Unfortunately not everyone creating content has embraced it as much as I have, and many that *have* embraced it create sub-par versions of their printed books. I witnessed a few tweets about books published by Penguin, showcasing how *badly* structured the content was. I witnessed it first hand with one of [Tami Olsen][]'s books.

I owned a copy of her printed books, and really enjoyed them. Unfortunately the experience with the digital books wasn't nearly as good. They weren't responsive, I'd say they were sluggish. It made reading them less than enjoyable. A painful side effect of converting a PDF file into an ePub file. The result is sub-par, which frustrated me when trying to read them.

##From Frustration to Prototype

Books deserve to be looked after regardless of the medium, and I decided to do something to prevent as many of these stories as I could. Over the months of November and December I pieced together a prototype that could be used for content authoring. It supported text-only content, and no covers could be added. It *worked*.

From the very start I knew that supporting the open format of ePub was vital to Simply Written. I also knew that supporting kindle devices would be important, as Amazon is a powerhouse in the sales department. I invested time in ensuring that these formats were crafted in a way that was valid, and provided a high quality of content.

With the structure in place I turned my attention to creating a platform for the actual authoring. Having a solid system for creating books means nothing if people don't have an enjoyable writing experience, as they won't *use* it. Sadly at this point my university studies, and work on [Get Invited][1] took over my life, and Simply Written became a lower priority in my work schedule.

##From Prototype to Beta

This changed last week, when I decided I was going to undertake a solid week of development on a single project, and take it from where it was already to something I could share with the world. Simply Written was the *obvious* choice. It had sat neglected for too long, and I already had a solid idea for what I wanted to achieve.

The week consisted of a complete redesign of the site, and a major overhaul of the codebase. I've pieced together the key tweets I sent marking progress throughout the week in [this storify][2] story. All told, the week consisted of:

- Site design overhaul
- Site architecture overhaul
- Better book details
- Better authoring functionality
- Support for WYSIWYG *and* markdown editing
- Chapter and book organisation
- Chapter and book deletion
- Book cover support
- Inclusion of important book pages:
    - Title
    - Copyright
    - Dedication
    - Epigraph
- Improved book generation suporting new book features
- Account settings
- Allow chapters to have headings removed

Looking at that list is actually rather overwhelming, it's amazing what can be achieved in a short space of time if you break things down into smaller parts. I wanted to work towards a solid goal, of allowing for book creation, and the above list matches nicely with that goal.

It's not the final goal for Simply Written, as it doesn't allow for the addition of images inside of chapters, something that is beneficial in many types of content. Thus far Simply Written also lacks PDF generation. I realise that this is something that *is* needed but I don't want to add functionality until I am confident that it will meet user expectations. I *will* work it out though.

##Beta Launch

I've had a few quieter launches of Simply Written, largely due to needing to show off progess during the last two semesters of university. Today marks a more public beta, as I feel that things have reached a level of stability and quality that I can open things up to a wider audience.

Today marks the public beta launch of [Simply Written][], and I invite you all to [register][3] and try it out. Try things out, make some books, and if you break things please [let me know][4].

##First Steps

Simply Written is only just starting out, but it is already being put to good use. I mentioned earlier that I encountered a sub-par experience with one of [Tami Olsen][]'s books. As much as she is an author, I also view her as a friend, and I believed that her books deserved better than they had received.

As a result of this I have been working with her to provide copies of her books in both ePub and mobi format that she can sell online. Those books are now ready for her to sell, and she plans to via both the iBookstore and Amazon. The book is now available on Amazon, both in the [United Kingdom][7] and the [United States][8]. Once they're available on the iBookstore I'll update this post with links there too.

##The Goal, The Future

The goal for Simply Written is to allow authors to follow in Tami's steps, to author content that they can then sell online. To facilitate that there are some features that I want to add, but over time, so that I can get Simply Written out there. Iteration allows me to add new features as things progress and lets me get people using things *now*. Things I plan to add in the future:

- Adding images to chapters
- Multi-author support
- Billing for the system
- Book promotion system

I currently plan to charge for the service, but that's it. You get your books from Simply Written and any profits you make are yours. I don't have any plans to sell content directly from Simply Written, I believe that there are already services out there for handling that. I *do* want to provide a means to promote content authored using Simply Written.

##Check It Out

To close, I'd love it if people would check out the [beta][Simply Written]. Write books, follow [Simply Written][5] or [myself][6] on twitter, and let me know what you think.

[1]: https://getinvited.to/
[2]: http://storify.com/HerrWulf/simplywritten-dev-week
[3]: http://simply-written.com/register/
[4]: mailto:hi@davidturner.name
[5]: https://twitter.com/simply_written_
[6]: https://twitter.com/HerrWulf
[7]: http://www.amazon.co.uk/gp/product/B008LXQJGW/ref=as_li_ss_tl?ie=UTF8&tag=refer05-21&linkCode=as2&camp=1634&creative=19450&creativeASIN=B008LXQJGW
[8]: http://www.amazon.com/gp/product/B008LXQJGW/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B008LXQJGW&linkCode=as2&tag=refer05-20

[Tami Olsen]: https://twitter.com/keilantra
[Simply Written]: http://simply-written.com/