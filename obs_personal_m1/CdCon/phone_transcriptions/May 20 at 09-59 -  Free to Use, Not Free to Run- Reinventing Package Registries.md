---
type: transcript
topic: work
---

[Speaker 1]
Robin is the head of our openjs Foundation, and I'm excited to be here in this talk because it's a subject I referenced a little bit on Monday, but it's important to understand, you know, most people when they think of critical where critical Source infrastructure is, and you immediately of GitHub, right?

Like, GitHub is where people go, but projects and so forth. But there's also another set of supercritical, uh, open source platforms, which are the pack? Registries npm, Maven, Central IPI, Ruby, you know. These are places where a lot of code is distributed, where dependencies come from, uh, and these, uh, critical components of the infrastructure are facing a lot of stress these days.

And Rob, tell us about things we can do to fix it, hopefully.

[Speaker 2]
So, yeah, good morning.

[Speaker 3]
Let's just start with something simple, uh, you all paid to be here, right? Flights, hotel tickets time? Because you know this experience. This infrastructure of people and ideas has values. Now, imagine walking in here and saying, Hey, you know, I like all this for free. You're all open source, right?

Hopefully the Linux Foundation. Well, of course, that sounds ridiculous. And yet, that is exactly how most of the world treats the research infrastructure, not the code, but the infrastructure behind it. So, you know, we built an industry on a powerful idea, something I'm very passionate about open sources free.

It's we free to use free to download. And of course, the wonderful community that freely builds upon it. And that part isn't a changing. But here's what we've overlooked. Free to use has never meant for you to run. Open source being free is not the problem. It's the promise.

The problem is assuming that infrastructure, the infrastructure behind that promise, has no cost. So, you know, if you think about it, we've quietly turned open source into something else. We've kind of turned it into the equivalent of free overnight shipping and software. You know, it's like a button dependencies show up instantly around the world, just like magic.

There's no friction, no second thought. But, you know, anyone who's ever run a logistics system knows that overnight shipping isn't free. It's one of the most expensive systems you can operate in warehouses, routing people, solving problems, abuse prevention, and that's exactly what package Registries have become. They become a global, a real-time distribution Network for software.

And we've been treating it like it runs on Goodwill. So, think about the scale of Registries, uh, it's just staggering 10 10 trillion downloads. In 2026, that's across ecosystem. So, JavaScript, python, Java rest, PHP, Ruby, that's over a billion per hour. And so that's what we're kind of calling industrial infrastructure.

And for years, you know, it's kind of worked. But in reality, a small number of people have been carrying this enormous burden. You know Registries today, they often survive on infrastructure credits from some wonderful Partners. A lot of small teams often volunteers many Registries, and I know there's some registry owners here are just run by one person.

So, you know people again. They're doing the hard work and critical work because they care. But Goodwill is not an operating model. And for years. Again, that was just barely manageable. But, you know, today, of course, the Baseline changed. And, as you know, modern apps aren't built on 10 dependencies.

They're built on hundreds and a gosh, I know, with JavaScript, often thousands, and so AI often didn't create the problem. It just accelerated an existing curve. So, you know, this week, I pulled some just some data points from a few of my projects at openjs. And if you look at npm and downloads are just exploding many 50 in the last quarter.

Um, I even looked at lowdash this morning. Now, two months ago, John David Dalton calls me goes Ryan Robin. We're like, we just passed 100 million downloads a day. Well, yesterday, it was 155 million. Okay, that's just barely she wants. Um, so if you think about, you know just a few of these projects Express hours apps.

Low Dash is just buried deep in the dependency tree, almost in almost everywhere, whom DG Powers modern node networking. So, you know, different layers same Trend, and again, these are not trendy AI Frameworks. Not that they're trending, they're foundational JavaScript infrastructure, and all of this is changing because the consumer changed.

So, if you think about npm, npm is no longer just serving human developers, it's serving automation. CI Cloud environments build system, and of course, AI agents. So, we've essentially moved from Human triggered installs permission, scale consumption. But here's the deal, and you already know how this ends when infrastructure gets stretched.

The impact doesn't stay hidden. Many of you, you probably all feel it right. Slower incident response. More sympathy, more supply chain risk, and the trust starts to erode. So, what essentially looks like an infrastructure quickly becomes your business.

Uh, Brian Fox, who I think is out here somewhere at Maven Central with Sona types. He said it well. Open infrastructure became the free extension of private optimization. He described one default Enterprise. Workload can trigger 80, 000 downloads of the same artifact a week. That's in 40 terabytes in 24 hours.

Another common problem he's experienced reacts native build scripts, pulling debug, and release binaries via curl. It adds 27 terabytes a day. So, you know, really. No one is really behaving irrationally. They're just, you know, companies are optimizing for Speed, right? But unfortunately, the shared infrastructure absorbs the cost. And that's the shift package.

Registries are no longer just dependency servers. They quietly become runtime infrastructure for Global Systems. So, you know, from the outside Registries can look deceptively simple. Upload a package download a package, but what's really being managed today is trust. Because when trust breaks the consequences, scale just tremendously. If you think it, take a look at axios that happened about a month ago as an npm issue.

Axios is one of the most widely used JavaScript's HTTP libraries in the world, and that one compromise maintainer account briefly during what a JavaScript's most trusted packages into, like a malware delivery path. And the malicious versions were only live for a short time, but when you look at axios and How Deeply embedded it was in everybody's dependencies, the supply chain risk and attack did not take long.

And that's why this just isn't package hosting it's critical infrastructure. Um, but good news. Here's the important point. This isn't quite theoretical, and the market is already adapting. Um, the eclipse Foundation saw the same pressure with openvsx, which sees 300 million downloads a month again. They saw the same sort of Behavioral shift AI agents Cloud IEDE CI, again turning human scale usage into machine scale consumption.

So, Eclipse adapt adapted, and recently they announced a managed service where the common stays open. Developers stay free! Commercial platforms at scale pay and rate limits protect the shared infrastructure, the shared service so that distinction really matters. So, Eclipse is not abandoning openness. It's just updating the economics. Because again, you're not paying for open source.

You're paying for industrial scale usage. Um, again, sonotype for Maven. The message was direct. Public infrastructure has been treated like a free extension of private platforms, and that model doesn't hold, and we're seeing it happen Beyond package Registries. If you look at the Linux vendor firmware service, they have more than 145 million updates, delivered same pattern critical infrastructure, scaled Way Beyond the model, the funding model, and the cool thing is.

Dell and Lenovo stepped up so. Different infrastructure, same economics.

So today, I'm here not just representing JavaScript, but my friends across the open source language ecosystems working on this together and the conversation didn't start today. Um, registry leaders have already been selling the alarm. I don't know if you saw some of the open letters that we've, uh. Released in the last few months.

Our first one kind of made the point that opened infrastructure is not free. And then we recently released a second open letter really focused on that really operational burdens and what it takes to run a registry at scale. Um, and really the messages, uh, free to use, does not mean free to operate again.

AI is only adding to the pressure. Um, and so if you think about the folks running these Registries, we've been meeting weekly 7 A.M great friends from Pi Pi, roomy gemscrates.io packages, openbsx, and other friends. From openssf to the CD Foundation Pearl, and what have you? So, again, this is not about any one registry.

Um, and so many again of these Registries are running at non-profit foundations who are really committed to keeping open infrastructure open and trusted. But again, an open Mission does not solve structural economics. So that's why we just recently launched the sustaining package Registry's working group, the Linux Foundation, which I'm proud to be a part of.

But the one important thing to note. This is not about charging developers or restricting access. It's about aligning cost with value for industrial scale commercial consumption. Because these systems are really just too interconnected for anyone registry to solve alone. So, let's think about what are we actually doing in this working group?

And again, we've just started, but we're really excited. We have a charter on GitHub, and first we're tackling economics again. The hard question, how do we fund the infrastructure, the operations, the governance, and the people who are working to to keep these systems running? Um, second, governance. Where can we collaborate on on common areas because no registry wants to reinvent legal terms?

Terms of use policy Frameworks or commercial models alone? And third communication is really an important part of this, and setting expectations with those who are using our Registries. Um, and again, the industry is treating this, like infrastructure, like, it's costless, but we really are getting more clear and more aligned about what sustainability actually requires.

So, you know, our message again is open structure. Open infrastructure has become essential infrastructure, and as we know, it powers every app. Every company, every AI system, and here we share the same value, and our responsibility is to is to sustain it collectively, too. So I just want you all to be on the lookout for your favorite package registry.

You may see some of them changing their business models. Because we recognize that if the sustainable models don't emerge, some of this infrastructure won't survive. And as one registry owner said in our working group scosh, you know, we just might simply go out of business. Things don't change.