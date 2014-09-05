---
layout: post
title:  "Building Simply Written"
date:   "2012-08-01 19:18"
categories: posts
author: David Turner
twitter:
---
A couple of weeks ago I publicly introduced [Simply Written][] to the world. It's been an idea in my head for some time now, and I'm really happy that it's finally out where people can start using it.

In my original article on the project, I discussed the thought process behind it and how I took it from being an idea to being the web app that you can make use of today. I didn't really talk about how I *built* it, or any of the technical aspects of it.

Let's remedy that.

<!--[More]-->

##Goals

Every project has goals. The development of Simply Written was no different. The goals in this particular project were:

1. High quality output
2. Simplicity
3. Gets out of the way

Each of these goals impacts the work in some capacity.

###High Quality Output

This goal serves as the bedrock of Simply Written. It's why I started the project. Digital books were being mangled by automating the process of digital book creation. Simply Written needed to get this right, otherwise it just contributes to the problem.

###Simplicity

Simplicity in a service is difficult to get right, and is one of the key principles I have identified that help my work [make people happier][1]. Simplifying a process doesn't mean dumbing something down, it means removing complexity. I don't want users to have to jump through hoops and perform tricks in order to create.

###Gets Out of the Way

This goal goes hand in hand with Simplicity. I don't want Simply Written to require hand-holding. I don't want the service I built to get in the way. It shouldn't be a tool that holds users back from creating. Microsoft Word can do that, I don't need to.

##Problems

Simply Written's inspiration comes from a problem I encountered: *Digital Books aren't being generated in a manner that provides a quality product.* That serves as an encompassing problem, but it's not really a solvable problem as there are components that create it. To me, the problems are:

1. Content output quality sucks
2. Generating multiple formats

###Content Output Quality Sucks

This is closely related to the original problem above. Digital books being generated quite often are sloppily done. They're being created from content aimed at being printed, and the end result suffers for this[^1].

In addition the best of the digital book formats, ePub, suffers from such automation as there is no way to identify break points that could be used to create high quality ePub files. I'll talk about this later.

###Generating Multiple Formats

As mentioned above, converting from a format meant for print to a digital format is messy. Doing the same for multiple formats isn't going to be any better. It's important to ensure that all the output formats are of a high quality. If it's not something I would be proud of, I don't want to make it available.

It's also important, to me, that content isn't *converted* between the different formats. The content should be slotted in to them. Conversion of content rarely ends well. I don't want to see that happen to content in Simply Written.

##Having a System

I didn't just throw myself into building the current version of Simply Written. I did that for closed testing and, whilst it worked, it wasn't as good as it could have been. I was able to build upon some of what I learned during closed testing, along with other work I have done. The key things for Simply Written were:

1. Use a Framework
2. User Authorisation and Security

###Use a Framework

Having a framework in place allows me to get the ball rolling quickly. Over the last two years I have been using/developing my own framework, called the Wee_ Framework[^2], that provides a basic shell for web apps. It also provides me with a great deal of flexibility.

It's something of a Model & View framework, with a single file controlling what is loaded. I've tried many of the common MVC frameworks out there and the have always felt that they do more to get in my way than help me get things done.

###User Authorisation and Security

Any service that handles user details should have this on the top of their "Get This Shit Right" list. Sadly it seems that not every service out there does. Ever since I started work on my first web app, [ReferenceIt][], I have worked to ensure that user information is secured.

The majority of information that I store is encrypted. Email addresses and passwords are stored in such a manner that if the system is somehow compromised that the information accessed is rendered useless. The only person who will ever know a user's password is the user. The way it should be.

##Building a System

As mentioned above I didn't just *build* Simply Written, I thought things through to ensure that what I built would be of high quality. This required an understanding of what I wanted the site to have, and how I wanted the site to be.

The closed testing of Simply Written served as the first test for identifying the structure required for the service. Some of this was obvious, as there would have to be a user-only area. For the current version I was able to build on this to create a more fully formed structure.

###Registration

![Simply Written Registration Form - Complex but it's all I need to let a registered user immediately start writing][i1]

I wanted to ensure that the process for registering for an account would let those who register immediately start writing. As a result the registration process asks for a decent amount of information, more than I would normally ask for. The information is important though, it is used in digital book publishing.

Every book has an author, every author has a name. Every digital book needs a method to create a unique identifier for a book, and the username allows this to be created with ease. Every account requires an email address and password to login, as email addresses are easier to remember than usernames.

###Book Setup

![Simply Written once logged in - you can immediately start writing][i2]

With the information users provide on registration I am able to let them *immediately* start creating books. Digital books require a great deal of information, but getting started requires only one thing: a title. With that anyone can immediately start writing.

There is a collection of extra information available that is hidden from view. It's important information but isn't necessary for a book to be generated, and is all optional. Some of the more useful information is pre-populated at this point, but all of this information can be edited at any point.

Once a book has been created an extra piece of information can be added, a cover for the book. This isn't available when initially creating a book for technical reasons, and book covers are organised based on information about both the author and the book. The information needed to save the cover isn't available until the book has been created.

Users will also note that books are listed on this home section in order of most recently added. This sidebar allows users to re-order their books as they see fit. It can also be used to delete entire books if necessary. Obviously, deleting a book will delete all the chapters it contains.

###Chapter Creation

![A freshly created book, awaiting new chapters][i3]

Once you have created your book, you are taken to a book edit view. The structure is similar to that of the create book page, but with two notable differences:

1. A book cover can now be added
2. The sidebar now lists chapters, not books

The sidebar will adopt this view when you are handling a single book, allowing a user to quickly switch between chapters as necessary. As with the books, it is also possible to re-order and delete chapters as they desire.

Having just created a book, there will be no chapters created just yet. In place of a list of chapters will be a note letting the user know that there aren't any chapters, asking them if they would like to create one.

![Writing using Simply Written is just like using Microsoft Word or WordPress - easy][i4]

Creating content for chapters is much like writing content using Microsoft Word, or popular Content Management Systems like WordPress. I want to provide the best experience possible and doing this can involve providing a familiar experience. Not everything needs to be re-invented to provide an improvement.

##Providing a High Quality Structure

The goal of simplifying the process of digital book creation isn't an easy one. Simplicity isn't an easy thing to achieve, there needs to be a solid structure in place to ensure that simplicity doesn't turn out to be a dumbed down process. It is important to ensure that you get this right from the start, as it can be *very* difficult to go back and fix this later without scrapping things.

To get books right there were two key areas that I needed to think about, and ensure that I handled them properly:

1. Content management
2. Output formats

Content is *key* to any form of book, printed or digital. If you handle content poorly or, worse, fail to store it properly then Simply Written would not be a service people would care for. Ensuring that content was handled appropriately formed one half of the puzzle I needed to solve.

The second half was the formats that digital books are typically formatted in. There's a small collection of key areas to get right: ePub, mobi (Kindle), and PDF. To provide a service that does justice to users, I needed to build a system that would allow Simply Written to provide these formats.

These areas formed the basic issue that I felt needed to be solved, that of allowing users to write content once and be able to publish it in the multiple digital formats required. How did I go about solving them?

###Content Management

Solving the issue of content was one I put a lot of time into. It forms the basic inspiration of creating Simply Written. Taking a book formatted for print and trying to create a digital edition wasn't working.

Similarly I didn't want to take a book formatted for ePub use and try to and wrap it up as a mobi file. It wouldn't work, and if it did it would be poorly done and deliver a sub-par experience.

The solution to this problem came from looking at what these formats had in common. HTML is the underlying structure of the web, and digital books have a *lot* in common with the web. Content written in HTML would fit perfectly into both ePub and mobi formats, and PDF files can be easily created from HTML. I had a winner.

###Formats

Handling digital book formats can be tricky. What works for ePub might, sometimes, work for mobi and PDF plays by a different set of rules entirely. As I mentioned in the original Simply Written Beta Launch, ePub and mobi files have a lot in common when it comes to building them.

An ePub file is essentially a zipped up collection of files and folders. The book's content is saved as XHTML files, it's styled using CSS and there are a collection of files that handle information about the book. It can be a bit messy when you dive into it, but as you progress things start to make a lot of sense.

To provide the best experience it is also important to properly separate content in the book. The most suitable manner to do this is by chapter. The reason for this is to provide a better experience for people reading the content.

To provide an example: If someone is reading a book that isn't split, digital book readers need to load content from the start of the book. This is fine when someone is starting a book. It's not so great if they're five chapters in. Then they have to *wait*.

Splitting a book into multiple smaller chunks allows the reading software to start from a more suitable start point, such as the beginning of the chapter the person is trying to read, and then load in extra content as needed.

A finished mobi file is rather mysterious, as it's a proprietary format owned by Amazon. There are tools you can use to extract the content from mobi files but don't. It's a terrifying and scary thing to look at[^3].

Fortunately you *never* need to look inside of these files, as the same structure you would use to create an ePub file can, with a few adjustments to some of the files that store information, be used to generate mobi files.

Some considerations need to be made for some files though, as all images are processed into mobi friendly content and, if you have any PNG files with transparent areas in them, the end result of this process is not a pretty one.

##Generating Digital Books

Every part of Simply Written is important, but if any part serves as the cornerstone of the project it is the book generation process. Making it easy for users to register, create books, and write means *nothing* if the end result is of poor quality.

It should come as no surprise then that this is the part of Simply Written that took the longest to implement, and is the most tweaked part of the service as I continue to improve the quality of the content generated here.

To ensure that each format available (currently ePub and mobi) is of the highest quality, each has a separate book generation system. This means that I can optimise ePub files separate from mobi, and vice versa. The same will be true as additional formats (namely PDF) are added.

Each of these formats has slightly different structures and needs. Simply Written's book generators cater to these. They also deal with some of the more fiddly aspects of content styling for the various formats. The mobi format isn't nearly as flexible as ePub when it comes to CSS support, I do what I can to provide a consistent experience where it is suitable, and embrace difference when it's appropriate.

##Moving Forward

I have put a great amount of time and effort into Simply Written to date, but there is still room for growth. At the moment there are three key things I will be implementing in the future:

1. PDF format
2. Image support
3. Charging a Fee

###PDF Support

Of the three key formats for digital books, I currently handle two. The third, PDF, has proven to be a bit trickier. It's not that I have difficulty generating them, that part is surprisingly easy. The difficult part is generating PDF files with a quality of design that I expect from books my system will provide.

I'm a firm believer in not releasing a product until it is at a level you are happy with. PDF will happen, but only once it is of a high enough quality.

###Image Support

So far I've added support for book covers to Simply Written. They're a bit easier to implement than images in a book's content, as I have more direct control over how a book cover is used. Graphics in the book's content become trickier to manage, which is why they're not included just yet.

Again this is a case of not wanting to implement something that isn't ready for use. I want it to be usable when it's implemented, not a mess.

###Charging a Fee

Money makes the world go round. It pays for important things, like coffee, electricity, and internet connections. It also covers things like rent, travel, food, and hosting. I want to make things better for people, and that includes for myself.

By charging for the usage of Simply Written I am able to ensure that the service remains available, and it further motivates me to continue working on it. If I can't afford to keep a service running I won't, so it's in the best interests of everyone that uses the service that it's profitable.

##Lots Done but More to Do

Simply Written has come a long way recently, but there is plenty more to be done. I hope to be able to dig a bit more into some aspects of what Simply Written does in the future, looking more closely at some of the technical aspects of the site.

##Further Reading

- [Introducing Simply Written][2]

[0]: /building-simply-written/
[1]: /making-people-happier/
[2]: /introducing-simply-written/

[Simply Written]: http://simply-written.com/
[ReferenceIt]: https://referenceit.org/

[i1]: /img/simply-written-registration.png
[i2]: /img/simply-written-logged-in.png
[i3]: /img/simply-written-new-book-no-chapters.png
[i4]: /img/simply-written-content-editing.png

[^1]: This really shouldn't be tolerated in any aspect of content management. Trying to convert a poster into a web page doesn't work. Why would anyone think it would with books?
[^2]: Wow, it's hard to believe I started work on both Wee_ CMS and this framework two years ago. Time flies sometimes.
[^3]: Interesting note for the developer folks out there. Simply Written's codebase weighs in at 23.4MB, the file that Amazon provides for creating mobi files weighs in at 20.5MB. Yikes!