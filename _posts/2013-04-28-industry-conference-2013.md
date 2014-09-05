---
layout: post
title:  "Industry Conference 2013"
date:   "2013-04-28 12:14"
categories: posts
author: David Turner
twitter:
image:
  featured:
    src: /img/industry-conf.svg
    alt: Industry Conference 2013
    width: 1000
    height: 300
---

The last few days have been quite the journey for me. It was my first time in Newcastle, my first time attending any conference aside from Build, and the first time being involved with sponsoring an event. So many new experiences for me in such a short period of time, with high quality talks over the course of the day, but it was great to spend time talking with people about Get Invited. I _loved_ it.

##Sponsoring - Get Invited

The real highlight of the day was to be an official sponsor for the event, complete with our own exhibit that allowed [Kyle Gawley][] and myself could demo Get Invited for attendees. We've spoken to people about Get Invited before, but never as a sponsor. We had a few minor kinks in the run up to Industry Conference, but things went smoothly on the day, and it was great to spend time speaking with people interested in using what we've built, catching up with friends working in the same area as ourselves, and talking with a represantive from a local accelerator programme.

![Speaking about Get Invited][get-invited-photo]

Getting to talk with people about Get Invited was a real joy for me, and the feedback we got from people was positive. We also got input on how to work through some of the issues we’re currently experiencing. It's one of the truly great things about our industry, the openness we have and our willingness to share what we know with others. Something that Industry Conference attendees and speakers really demonstrated over the course of the day.

##The Talks

There was a lot to learn at Industry Conference, and I'm sure that others picked up on things that I didn't pick up on. Below you will find my thoughts on each of the talks.

###Rachel Andrew - Things Learned While Supporting Perch

Rachel was the first speaker of the day, and spoke about how supporting a product that can really help that product to grow and evolve. Interacting with customers is a way to see what they like about a service, but it also lets you see where things could be better, and where they could grow. In a world of free products it is this attention to customer needs that allows a paid-for product to stand out, simply making a good product that you charge for isn't enough.

This has really opened my eyes to some of the things that I, and my fellows at Get Invited, really need to start thinking about now. Having a great product isn't enough if people running into issues then have a bad experience. Everyone had bad experiences, and almost everyone _talks_ about those experiences. The number of people who talk about the _good_ experiences is much smaller, and in my own experience they also don't talk about them for as long.

In her talk she also spoke about the importance of getting the structure of supporting customers right from as early on as possible. As a product grows in popularity, the number of issues you get contacted about will too. A support structure that can't grow with your popularity is going to be a bad experience not just for the people giving support, but for those _needing_ it. That's not a pleasant experience for anybody.

###Harry Roberts - Architecting Scalable CSS

In my notes for this talk I jokingly referred to it as “Fixing Kyle’s CSS”. Kyle writes good code and good CSS, but I know from reading a lot of the things Harry writes that there is still a _lot_ that both Kyle and myself could do to streamline things further. The talk didn't disappoint me. Some of what he wrote about were topics I'd already read from his site, but there was a great deal that I still picked up from listening to him.

I _loved_ the idea of viewing CSS as similar to Lego. You can do so much with a single Lego set. You can make the set, but you can ignore the instructions and make a limitless amount of things with the bricks you get. And that is _without_ mixing multiple kits together. You can achieve similar results with CSS. You could follow a guide/tutorial and make a specific thing but you could then turn around and, with that same knowledge, make something completely different.

Harry also spoke about the idea of breaking things down into components, and about the idea of having bits of CSS that do only one thing, but that do that one thing _very well_. You can mix and match these comonents together to make things, all without repeating a vast amount of style rules in your CSS. It's something that I try and do when I'm writing CSS but there is still room for me to improve. I think I need to focus on the idea of a Minimum Viable Component. If I have to write a few more components in my CSS, that I can then use as needed elsewhere, I don't think I'll mind. At all.

Finally he spoke about the importance of having a structure for the styles behind a site, and sticking to it. Having a structure, and a flow, to things is important. He also spoke about the idea of having a shame.css file that is where you put in temporary hacks that need to be sorted when an opportunity presents itself. I'd heard of it before, but still love the idea of it. We've got something similar working with Get Invited at the moment, as you can see in the admin panel's source code:

{% highlight html startinline %}
<link rel="stylesheet" href="/themes/getinvited/css/last-minute-fixes-by-dave.css" />
{% endhighlight %}

I plan to have that file gone within the next week.

###Chris Murphy - We are Navigators

After a short break we had Chris Murphy, one of the founders of Get Invited and generally awesome guy, speaking about education in our industry. As someone who is involved, in a small capacity, with education for the web, much of what he spoke about resonates with me. His talk started with a [five minute clip][dead-poets-society] from the final moments of Dead Poets Society, using it to highlight the different approaches some people take to education.

The clip highlights that a good educator is able to truly help their students to grow as a person, to transform into something _more_. That this is something that education _should_ be doing as, ultimately, education helps to shape the mind… an important thing to get right. Something that, sadly, hasn't been the case through much of my pre-university education. Even there it was only certain individuals who cared, or seemed interested, in the material they cover.

Chris spoke about how education isn't just about teaching, but about the ability to teach students how to _learn_, rather than how to _do_. Teaching a person how to do one thing is very limited, teaching people how to learn more about what they are doing lets that person develop, grow, and ultimately do what it is they want to do, rather than doing the one thing that they were taught to do. Education should create good people, not people good at one techincial skill.

I've studied under Chris for the last year and a half and, during this time, he has been someone who has helped me turn something that I am good at, and that I enjoy, into the beginnings of a business that allows me to get paid for doing the things I love to do. Educators could, and should, be more like this, and having gone through at least some of what he covered in his talk it serves as a further motivation for me to do what I can to help in the field of education.

I wouldn't be doing what I am doing now without help from people like Chris. Education needs more of the things that he is doing and I'm more committed than ever to doing what I can to help in that sector.

###Ashley Baxter - Changing a Stagnant Industry

I'd heard that this was Ashley's first speaking engagement but there was _no_ evidence of it from where I was sitting. Speaking of her journey from her education to running a business she had no understanding of, she delivered one hell of a talk about how she's accomplished everything she has. I can only imagine trying to get to grips with insurance, but the idea that achieving small things allows the bigger things to happen is something I have found to be very much true.

There are so many industries that have issues in them. Education was mentioned in the previous talk, and Ashley works in another: insurance. It's an industry that seems so archaic, using ancient software to operate, but that seems to be continually pushing to find the smallest price possible. Technology provides an opportunity to produce a better experience to customers, an experience worth more than the "lowest price possible" that others stive for. Good things are worth paying for.

Insurance isn't the only industry that suffers from these kinds of techonology-related issues, and an application of technology can give a new edge to comptetitors. I'd love to see more people or businesses harnessing technology to improve some of the most tedious of industries to make them better for the people _working_ in them, and the people that _use_ them.

I'd also like to take my hat off to Ashley for her ability to pick up Ruby so quickly. I've tried doing the same, as a developer of multiple things, and I simply cannot wrap my head around it so I have a great deal of respect for people that can make it work for them.

###Noah Stokes - $50,000 Mistakes

Noah's talk covered his journey from Apple engineer through to setting up his own design studio, something that came from his lack of passion for what he was doing. A lot of what he talked about resonated with my own experiences in certain aspects of my professional life, experiences which have helped guide to to what I'm now doing professionally.

He also spoke about some of the other aspects of professional life, including something that I've heard multiple times before, that you will only get better by working at things and that you'll only ever get to do the work you want to do if you _start doing the work you want to do_.

###Rasika Krishna - Cross-Cultural UX

Rasika's talk was an impressive talk for me, not just because of the content, but because of the fact she'd just flown in from Singapore. Her talk took a look at how different cultures can perceive a design. Many designers will, of course, be familiar with the impact of colour in a design, but her talk went a bit deeper taking a look into the principles of psychology, cultural groups, symbols, and the need for things to be a conversation when working with people.

I really liked hearing someone talk about things being more of a conversation when dealing with clients. Communication is an important aspect of things to get right, but it's also important to listen and to _understand_ what is being said. I often find myself failing to do this. What a customer says is often worded in a way that we as designers don't get, but that makes perfect sense to people talking to us. We should learn to communicate better with customers and clients, and to guide them in ways that benefit both of us.

Oh, and the convention of naming icons in a manner such as "hamburger icon" is absurd. Can we stop that doing that kind of nonsense?

###Josh Brewer - Redesigning Twitter

Josh spoke about the process used in designing the #newnewtwitter, a large scale design project encompassing _all_ of twitter's public facing designs. He covered some of the problems they had, and some of the methods they used to solve them. He also empahsised the importance of not letting people fall into the trap of thinking design is magic. This is something I need to do a better job of handling with my own development work.

He also spoke about the importance of standardising the design tools used on a project. In my freelancing I often work with people using different tools, which is fine, but it can understandably become an issue when working with a team of people continually. Having a consistent design tool makes life a lot easier.

He also has me convinced that I need a plotter/printer so that I can attack all of Kyle's deisgn work with a red sharpie.

###Jeremy Keith - What We Talk About When We Talk About The Web

Jeremy was a last minute speaker who stepped in to replace John Allsopp. Jeremy himself was the first to admit that his talk wouldn't be the same as one by Jeremy, but it was a talk that I greatly enjoyed. He broke the web down into the components that make the web work, and upon the importance of understanding how links and forms should work. It's already making me rethink a significant chunk of the functionality in the work I have been doing recently.

Whilst I agreed with a great deal of what Jeremy spoke about with regards to how links worked, that they should never perform an action instead serving to connect pages together, I _really_ loved how he spoke with regards to making things work in the _responsive_ web With the shift from designer-enforced dimensions to a fully fluid experience, with the rise of the smartphone, and with mobile data connections, optimising sites is even more important than ever. Some of what he pointed out I had heard about/read up on before, but some of the ideas were new, and I'll definitely be putting them to use going forward.

##Community

I really enjoyed the talks and being there representing Get Invited, but the thing that I loved most about Industry Conference was the people there. The industry we work in has a great community, and I loved catching up with friends, finally meeting people I've spoken with for months on twitter, and making new friends at the fringe events that were put on over the time I was in Newcastle. I can't wait to do it again.


[Kyle Gawley]: http://kylegawley.com/
[dead-poets-society]: http://www.youtube.com/watch?v=UJsjNNp0foE

[get-invited-photo]: /img/david-turner-get-invited.jpg