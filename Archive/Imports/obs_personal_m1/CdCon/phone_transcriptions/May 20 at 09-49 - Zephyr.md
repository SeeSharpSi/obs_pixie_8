---
type: transcript
topic: work
---

[Speaker 1]
You're talking about the Zephyr project real-time operating system. We

[Speaker 2]
need to work on when I came to LF. That

[Speaker 1]
is awesome. Uh, Zephyr was such a small project back then, and it has, uh, slowly but surely, uh, grown up to a pretty incredible footprint out there,

[Speaker 2]
and it's been by following the best practices that we've seen.

[Speaker 1]
That's awesome, happy to go into it. All right, let's hear about it. Thanks, Katie.

[Speaker 2]
Foundation incred. Dean and? That gave me some pretty interesting insights and opportunities because I've been in the industry for quite a while before that. And so, Zephyr's, a real-time operating system, and it's now being used in a wide range of emitted market segments. So, just out of curiosity show hands how many people have heard us ever before this?

Now, keep your hands up if you've actually developed products with Zephyr. I've been developing in Zephyr. Okay, some of you excellent. Um. For those not familiar, I've started because there's places where Linux is just too big. Okay, now this is like the sensors he actually there's small things, but you want to be able to make security best practices.

And you want to be able to do good open source development, so we design it to be scalable. And we make it flexible so you can just put in what you need. That's the key part so you can keep it small if you need to. But if you need to, you know, along with the Bluetooth deck?

Um, however, the project is almost insecure Security First that was. What we signed up with in mind, and we started a security practices too. And so. It's open source, of course, and we have a providing system available to us now. And so when we were filming the project, the mission right from the start was to develop.

To develop a best-in-class rtos and for resource and streaming devices to be secure and safe. And so, we've been working. We got this Vision by talking to developers in Dublin back in 2015 at OSS EU, and we've got lucky that it televised together and said, okay, what's missing? Bernard toss right now, and this is what we, you know, they want security?

They want safety, and that's where we went with it. So fast forward, we went from five boards, and we launched in 2016 now to over a thousand. And um, our governance with the developers contribute the code and steer the technical directions for the project. Um, our GSC chair has a seat on the governing board.

And that controls the funding. Which, and the TSC chair is pretty good about advocating for what he wants the money to be sent to help support the development. And from that, we've had a fairly good ecosystem emerging now in Zephyr to support developers, um, contributing the project of Building Products.

How we, what we used as a template when we were starting because a lot of the lessons from Linux? Um and. There was a report that came out around the same unstepper was being launched because it was the Lance Colonel's 25th anniversary. About what best practices work for them.

And so we use that as a template. And we started saying, okay, what are we doing, and for the most part, we've pretty much adopted a lot of the best practices, um? Dcl has been a big help for us, and we've got everything publicly documented. We started off with a short release cycle of Louisville for this community, it worked there to move.

Has we've been so broadly shifting the release cycle? So now, six months roughly. And we do to use long-term supports because for people making products, they don't want to be changing all the time. They want to have their security fixes and change if they need to. Um, similarly, the security we basically had it launch right at the start.

Um, we became a CDE numbering Authority back in 2017, and we've been generating s-bombs since five years now, and we're pretty much ready for the CRA to disc, and so this is helping the project do with its growth. Um, but the one factor. Communities start to grow. Um. Making sure that we're doing the right changes.

Feedback becomes a hardware is virtual, so we actually started doing surveys back in 2018 and doing an annual survey. And you know, checking on, you know, are the changes through making reasonable are the things we want to see improved? And. We've been keeping going ever since then. History of surveys has given some pretty good trend lines and so with over like 1500 developers contributed as effort last year and over 9004 percent project.

Getting a sense of what's working with people care about? Is even more important than it was, you know, earlier in the days because we want to make sure that it stays a good project for our community. And so, what are the results of applying these best practices? Well, this is a list of the rtosses that are out there, and as you can see, Zephyr now has well contributed in lots of these.

Other options have had in their entire lifetime. And currently, it's about 10x number of contributors and commits as the next highest one. So, all these numbers are direct from GitHub. And if you want to check me out because I always believe them, my standlines and benchmarks. Same neutral base.

And we're assuming about 3.5 minutes per hour right now. And this means that if you look at our contributors per year, we can actually measure ourselves against complex too now, and so we have steadily growing over the last 10 years by applying to practices. And as a result, also arguments have been growing up.

So Zephyr's got a fairly wide range of ecosystem, and what this means is a lot of really interesting products that are showing up in the field. Now, it's embedded, and there's a lot of them. I don't know off the top, but um, you know, anything from hearing aids to wind turbines to satellites?

And for those here at the show, gotta go chat with the framework people. They're in nursing activities, and they've got like, you know, their laptop. It's got Zephyrs firmware sitting in there and key krong. The keyboards are using it as well, so it's hidden generally. You don't know what's there, but it just makes things easier and much more power efficient.

So, even working with our developer community of Paramount and? Um, we've got, you know, the service coming in, but we really didn't know what was happening in the industry side for the product makers. So, we launched the survey last year and finished publishing results. And we've got a pretty good demographics across it in terms of the company size, the geographic region, and the rules.

So, and we got our top groups, not just several users, so we were able to do a bit of comparison this way, but pretty much results. Are you almost ever to be used for production ready? Um, products for longer life cycles. In fact, this is what's interesting to me, especially in the line of open source of continual changes.

Most of the people want things to be supported independental naturally for more than you know five years. So, I'm keeping open source projects and security commitments, and this is going to be important for people here. Um, the respondents. Appreciate the fact we've got such a wide selection of hardware for them to use and work with, and this helps with supply chain.

And in fact, you've got, you know. The hardware portability was one of the overwhelming factors that people appreciated Zephyr for, as well as their life community, and they like to help them make it faster. And so, when there's also left at the top of the road, so it's plugin instruction, you can see that it can now switch code, and this is from like the wind turbine folk.

And where people are using separage Hardware. It's mostly what the end series will respond, and it's mostly 32-bit. Okay, this is where it's coming in from right now. And you know how many Hardware devices are being employed? Well. 13 are deployed over 10 million of arms ever responded. So, when you start to think of it, there's a lot of devices with zipper up there.

The challenge of figuring us, which ones they are, because no one really wants to talk about. Who's that part of it, but people are using separate energy? So, and it's helping us making things more efficient and more power efficient and more performance. That's a good thing for all of us, right?

Um, especially, you know, when these resources constrain times? And, as you can see from that survey, we've got most of the market segments being pretty much covered. And okay. Luke has been around for 35 years. But, um, you know, we started fresh and loose, you know, living, learning from Linuxin as well.

A lot of stuff is very familiar to embedded links developer, so. Um, it's attracting a lot of startups, which is fun for me, too. And most of the organizations are planning to increase what they're doing with separate at this point now. And you know, you can sort of see a lot of the early adoptions happening in Europe, and you're just building up from there.

For 20 Asia Pacific, come online now too, as well as a little bit more young America. So, because we had that Geographic separation of our response. We can actually try to understand what was going on originally, which is kind of interesting. We passed 10 years now, um. And it has been a really interesting ride.

We've been learning a lot of lessons. And the fact that we've actually got things that are showing up and helping people. Is it, you know, something that makes me very proud? And it wouldn't be possible without, quite frankly, the zipper community of developers. And thank you very much for all the support you've done.

[Speaker 3]
What?

[Speaker 2]
What we're doing, right? We're doing wrong. There's a question or two about AI in there for those who are working with AI. Want to express your opinions? We're very interested in hearing what's working, what's not, and for those of you who are new to suffer, um, you know. Feel free to come join us.

Here's some participation information. Thank you very much.

Thank you.