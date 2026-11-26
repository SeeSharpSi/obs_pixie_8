---
type: transcript
topic: work
---

[Speaker 1]
Category of what people call the one percent developer proud for these Elite developers who you know are a 10x efficiency in development. He's going to say that's not true, but I'm telling you this is a very talented developer, and he's going to be talking about AI and, and it's really curious to hear from these folks who are sort of the best of the best in the software space.

How api is impacting, uh, their world? Brendan Burns works at Microsoft. He was the co-founder of the kubernetes project, uh, obviously, uh, you all know what kubernetes is. He's now a technical fellow and corporate vice president for Azure Cloud, uh, and he is going to talk to us about building the AI native era, please.

Welcome, Brendan Burns.

[Speaker 2]
Thank you

[Speaker 1]
so much

[Speaker 3]
and I can't do a Minnesota accent like Jim, but I did get a chance to visit my sister who lived here. So I appreciate both being here to talk to you, but also to visiting my family as well. Um, as Jim said, I want to talk about this development from the cloud native era to the AI native era, and it's been an interesting journey to go from talking to people at the very beginning of cloud native as we started the journey about how you know infrastructure is.

Code was something they might want to consider. Uh, containers were a thing that they might want to to be interested in to see this technology now being the foundation for the AI era that we're in

[Speaker 1]
and the AI native work. And I don't think that it. Exaggeration to say that what we are seeing in AI today couldn't exist without all of the contributions that the cloud native Community put in, so I think it's a thank you to everybody who's been involved in that and a real achievement and a demonstration of the value of this.

This openstack that's been built? Um, I think as Jim said, and I actually we didn't coordinate at all, and so I accused him of stealing my slides when he came back after his keynote, um. But AI has been built on a foundation of Open Source. In the fact this reimagining of tuxes as well, a generation from, uh, from open source.

But I think everybody who's been involved in open source from the beginning all the way through to the present day should feel. A certain amount of pride in the fact that this whole era has been built on this really, really robust foundation. And then even more than just being built on an open source Foundation.

I think it's been built on an open ecosystem Foundation, which I think is an even more important part of the journey, which is that we can come together and collaborate as individuals on Source repos, but when we come together as companies and when we come together with, you know vested economic interests and various things, it's really only through neutral Foundation.

Like the cloud native compute Foundation that we found in a long time ago, through to things like the agentic AI Foundation that really are the thing that also bear the weight of all of this collaboration and the obligations to continue that collaboration going forward into the future, but I wanted to talk about how we're actually thinking about building this egenic stack and all the technologies that we contribute to along that way to create the ecosystem.

I will jump

[Speaker 3]
through that slide. You know, I wanted to talk about how we've talked about how, as a company that uses a lot of AI. We can't just use technology. We can't just use open source. We have to contribute to open source, and so we contribute back to what any number of these very important projects that are part of how the AI staff gets built.

We contribute our own, uh, contributions out. And if you haven't seen things like the Microsoft Asian governance toolkit, I strongly recommend checking it out, um, because as we do this.

[Speaker 1]
And as I think about deploying AI out to Enterprise use cases and a bunch of customers and regulated Industries being able to control the output of these agents is a critical part of how we can go and do. Ai and scale. You can't just have, you know, a chat by?

I think sometimes people think you just throw a prompt at a chatbot, or you throw a content in llm and good things happen, um, unfortunately, good things don't always happen. And so, you need governance around and guard rails around these, uh, these models in order for good things to happen.

And so, we're doing a lot of innovation, I think, to not just build the technology that allows AI to exist, but actually, the technology that makes it easy for people to build AI driven applications and and. Years we've contributed to. The core Technologies that make up the foundations of Ai and, and really honestly, the cloud data Community as well, whether it's languages like python or a number of other programming languages, typescript and others that Microsoft attributes to obviously the kubernetes community and the Upstream team that we've built to contribute to the kubernetes community is very near and dear to my heart, but we also have a number of people who are working deep down in the the lower levels of the colonel and ensuring and.

Have carnal support across across the ecosystems and as well. Also on the Azure Cloud and that particular part of Linux running on the Azure cloud is also something that's particularly near and dear to my heart. You know, when I started at an Azure 10 years ago, it was not the majority operating system, uh, running from the Azure Cloud.

It is become the majority operating system running on the Azure cloud in those 10 years. Uh, and today, I think we're really excited to announce that we're going to be having Microsoft's open source Linux distribution, a supported version of Linux supported by Microsoft available on Azure out for anybody to use starting on.

On June Saturday, virtual machines as well as a container oriented flavor that's connected to our flat car project, which is a container oriented Linux that we donated to the cncf a little while ago, you will be available in the Azure. Service. I think this represents. I mean, for me, I'm coming up on in in June, uh, it will be a 10-year career at Microsoft, the 10-year anniversary of me being at Microsoft.

This moment, I think, is a real culmination of a lot of the work that we put in throughout and a lot of people put in throughout to really bring forward how open source um is a part of the Azure cloud, and it really, really critical part, not just of how our customers are building, uh, applications.

But how, our, uh, our own native? Are being built as well. I wanted to transition from that to the, you know, so that's that's sort of the. The corporate part of the talk. I wanted to transition from that to my own personal experience of Agents running, uh, an open source.

Okay, the first thing that I've noticed is that on the projects that I maintain, um? There's been a new level of contribution that comes, and some of that is very positive. Because, as Jim said, people who weren't able to contribute before are now contributing it. Some of it is a little bit negative, and it contributes to the the sort of PR spam that we've seen across for a while now, as people are gamifying and looking at and raising their GitHub profiles in order to contribute to other places and some of it contributes to security concerns where you know I now, and of you that every PR is a potential security.

Threat looking to infiltrate my software secure supply chain, and so agents have made this easier for everybody, and it's made my roles and maintainer harder. And that's something I think we need to acknowledge and figure out how we support, but it also makes my life as a maintainer easier.

Uh, and I would highly emphasize to everybody. If you are not using ghetto, co-pilot, or some other agent to ensure that your dependabot PRS are merged as quickly as possible, all of the threats that Jim talked about earlier are very, very real, and the very first way that you defend against it is to make sure that you're patching up to the latest dependencies.

So, if you haven't been using dependabot from GitHub or something equivalent, you should have years ago, uh, but a lot of those PR's linger because there's subtle API changes or other things like that, and so the magic of being able to add. And to make those small API changes and make you know the merge rate and dependent on PRS go from 90 to 99.

Makes a difference in keeping our projects secure. Um, I think the really also great thing is at the end of the day. I'm into open source because I want to help our users, and we're seeing agents assist users as well, right? This is a PR that I author and recently, uh, with the collaboration with copilot, um, that adds an Informer if you know kubernetes, it's a.

It's a tech it's a. Ips that clients use to do high efficiency access to resources and kubernetes. There hadn't been one in the python client. And we used an agent to add it. What's really interesting about this is not that I used an agent to add the Informer. It's that the issue asking for.

This was opened in 2019, right? So this one merged February 20th this year. The issue was opened in 2019, about seven years of lingering in a GitHub repo, not because it was a bad idea. This is a good idea, but just nobody kind of gotta around to get into it.

You know, it was always just below the cuff on. And and agents reduce that barrier injury to the point where, instead of me being like man, be kind of annoying to write that, um. I just did, right? Well, actually, I didn't do it. The agent did it for me with some supervision.

Um, and I think that this is a huge win for a lot of these features. They've just kind of sap below the cut line for years and years and years, and that's good for our users. Um, I wanted to conclude with my own thoughts about how we're going into the future, uh, I second, Jim's, you know, uh, idea that this is just leading to the development of more software.

I run a pretty large engineering team, and there's definitely a lot of concern about where this is going. I'm really excited personally because it's allowed me as a contributor to do a lot more code, you know, every boring meeting now has turned into an agent session. Where something's right.

Two monitors I'm looking at this monitor, but there's an agent over on the second monitor that I'm, you know, likely supervising. It's really felt empowering to me. And I think it's empowering to a bunch of people who may not have been willing to contribute before, are able to contribute before.

But the Fear Factor is really there as well, right? And so, if you're a maintainer. Or you're involved in open source. I definitely want you to to mind all the things that Jim said around the security concerns that are coming. There's some really concrete things you can do to start out, right?

Like, I just went through and actually using an agent, uh, switched all of the GitHub actions and all the projects that I run from being tied to versions to being tied to Shaw songs, right? If you haven't done that, go do it. It's trivial. It works. It secures against a whole class of attacks that, actually, we just saw being exploited within this dis.

Last year. And then there's a lot of other steps that you can do to start securing your supply chain. Improve your CI CD. All of the things that are sort of software hygiene that we didn't quite get to. Um, a, you know, as as Jim said that bill is due, but B, you can make the agent do all that boring work.

And so there's really no excuse at this point for not taking that stuff on and getting our projects to a place where, uh, you know, we truly have the health needed for the vulnerabilities that are going to be incoming. So, with that, thank you so much for for attending.

Um, there will be a book signing at the Microsoft Booth later on. Um, and we would love to come see you there. And there's going to be a whole bunch of other talks as well. So, don't hang out with us and we'll see you later. Thank you so much.

[Speaker 3]
First of all, I agree with everything but the most important thing is.

[Speaker 1]
Did Microsoft just drop a Linux operating system? And you know it is, it's been a very a very cool thing to be able to do part of that journey. So, what I love so much about this is when it must have been like eight, uh, 10 years ago, um, Microsoft joined the Linux Foundation.

I was on stage with Scott Guthrie, uh, he was in New York. It was this big conspiracy theory that somehow the Linux Foundation was undermining open source in partnership with Mighty Carousel. And now, you announce that you're shipping a Linux distribution. It's kind of, like, yeah. And it's been.

It's been a really great journey, and I, and I think I like to, you know, I, I? Uh, it's been awesome to see everybody within, uh, the company rally around it as well, and all I think AI has been a huge part of it. Actually, because AI is built on Linux and we are an AI company, and so it's a, it's a really important part of it.

Amazing! That's awesome. Yeah, I love that. All right. Thank you. Thank you.