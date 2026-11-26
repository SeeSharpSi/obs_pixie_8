---
type: transcript
topic: work
---

[Speaker 1]
Or the Linux Foundation. This follows 2025, which is the best year the Linux Foundation has ever had in terms of net new members, new projects, just an incredible growth in the organization in the open source Community. Just this year, we've had a whole slew of new projects that are addressing big issues in the open source world and in the technology sector in general, uh.

At high torch, we have the Safe Care Service project, so this is prevents binary code exe. In AI models. As AI becomes a more prolific part of our Lives, we've got to think about security. This is a tool that really helps those models be safer for all of us.

We also have the helion project, uh, this is a project for inventing DSL for offering kind of high performance AI kernels. We announced the okudu project, so this is an opencu-du. For those of you who are not networking Geeks, this is an open ran. I've got like a couple of networking geeks up front here, uh, it's an open ran, uh, implementation, uh, definitely a really big deal.

We announced this at mobile World Congress with dozens and dozens of mobile operators and telecommunications infrastructure providers. X402. We just recently announced this is a Commerce, uh protocol, for open native payments for AI agents. This is part of an ever growing agentic Commerce stack SQL mesh. We just announced this isn't book and Source data transformation project, uh.

And then, finally, uh, an oldie, but goodie, how many people here use react? Yeah, because it's a pretty popular, uh framework, uh, and the? Foundation is now part of the place. So, a whole bunch of good stuff today. We are also announcing, uh, an intent to form an ancient naming service, so everybody knows what DNS is.

But when you have agents out there, you need a new form of DNS, so to speak, uh. And today, we're announcing an incentive form an effort with GoDaddy. And here to talk about it. I have Oliver George from GoDaddy, who will go over a little bit about this new exciting project we have.

So come on out, Oliver, please.

[Speaker 2]
Hey

[Speaker 1]
folks, good morning, um Mike Sam can't put it off. I'm keen enough from Minnesota, but it's a bit. It's great to be here. Really, really happy to be here. We are a gold sponsor of the Linux foundation and double AIF, and I'm here to talk about our intent to submit.

Astounded in the coming weeks, but essentially uses. Dns. As Jim said. As a way of? Registering agents throughout the world. Um.

[Speaker 2]
Why are we excited about ANS? Hey, this is actually a written as a ietf draft originally. We're the contributors from a wasp and distributed AI apps and Cisco. Uh, naturally, um GoDaddy, having 22 of the world's remains. So we're very interested about the DNS and how it works, and how it supports the internet today, so we looked into.

It got very excited by it and started sharing about what ANS could be, but um, why wouldn't you use the DS? To be open standard to register agents. Um, short answer is, it just works.

[Speaker 1]
Okay, it's worked for a long time. People don't question whether it's going to be live or not. For the most part, I'm sure there are Engineers here that would disagree with me. But it just works okay. It's called on a trillion times, uh, a day, and it has sub 100 millisecond performance.

So when you think about everyone's going to build a registry or a shared secret about how agents talk to agents at some point, you're going to say, well, there needs to be a registry of Registries and above that there needs to be of industry of Registries okay, and DNS does?

That is beautifully simple, so we got behind this. We started looking at it. Our engineers starters contribute towards it, and that's what, really, really intend. Uh, on logic is an open standard for the DNS to register agents. Um, in terms of just the back of the vacuum math and scale about how it would work if you think.

One percent of the world's websites now deploy an agent tomorrow, and that agent is used a thousand times a day. Okay, that's six billion requests. That's less than one percent of the capacity. For the DNS. Um, so we're in a situation now where every agent would have. A viable.

Viable identity. It would have a clear owner. I only had a set of missions that comes with it. Okay, so when someone shows up and an agent shows up and does? That was something it buys something. It accesses your business accounts, you know who it is, what they're doing, and where they came from.

And without this kind of infrastructure that we all want to support eight inch or Anonymous. Agents or a bike? Um, we don't want that. Businesses don't want that and consumers them. So, that's the drop that we'll be submitting in the very, very near future. We're super super excited by it.

We spoke to many, many companies as being public press releases with cloudflare and Salesforce, and also. But if any of you folks want to learn more or join us on this journey, love to have you? Thank you.

[Speaker 3]
All

[Speaker 1]
right, uh, I know, that my brother and sister are following the Asian nating service registry very closely. Actually, my brother probably is fun fact, uh, he is a third generation software engineer. My grandfather was one of the founders of cray research, which was started here in Minnesota, uh. My dad was a computer programmer, and my brother is a computer programmer, so he is actually following along with this excited to have him, uh, here.

[Speaker 4]
Today, I want to talk about,

[Speaker 1]
uh, broadly. What's going on in open source, uh, and the the topic of the conversation is about things that are going good in open source and things that are a little bit of Challenge. And, of course, all of this has to do with artificial intelligence because it is just becoming such about an important part in the tech industry.

Uh, and keeping in line with a Minnesota reference, which, uh, some of you may or may not know. I'll get to that at the end of the title, the talk is sometimes eat the bear, and sometimes the bear eats you. It's kind of an old line, uh, but for a 20 years, you know, uh, the story of Open Source has been kind of two halves of kind of opportunities and challenges, uh, you know, the movement has been built on on a big battle that open beats close.

Neutral governance speeds vendor capture that the best ideas don't need permission, but you know AI itself is built on these Concepts? And so, in that case, we kind of ate the bear. And then, in the last 18 months, aai started to really, really improve. And I would argue in about the last six months or so, uh, AI started to write code in many ways better than people could actually write code, and it's also finding security vulnerabilities.

There's also a whole bunch of challenges around whether or not that technology remain open versus close. So, a little bit of the bear is eating us right now, and it's my job to kind of walk you through the context of where open source is eating the bear. The.

The thing to know about the bear we ate when it comes to AI, is that open source? Isn't it not just a part of the AI software stack? It is the AI software stack. Eras.

And today we are seeing a new unprecedented era of investment in technology. And this is that bottom Hardware layer that I'm talking about 700 billion dollars is forecast to be invested just by the large hyperscalers in the United States and a few other countries in Hardware data center infrastructure.

I mean, this is a massive, unprecedented increase in spend. And the demand for this spend has just been growing also exponentially. You know, I gave a talk, not that long about six seven months ago in Tokyo, Japan, talking about whether or not we're an AI public, you know, bubble is when the supply of something is, you know, not outstrips the demand.

And then you have this kind of calamitous, uh, bursting of the bubble. And everybody loses. I've now reversed for that position when it comes to this kind of capac. And the reason for that is. The agents have essentially broken the demand curve for intelligence, you know. Now, one person, I think I read an article yesterday, that the open Claw folks, three people are spending over a million dollars a month in tokens, uh, uh, from their open AI acquisition, uh, just by running all of these agents in parallel.

So, three people spending millions of months of millions of dollars a month, just, you know, token Max. To the extreme. That's kind of how that demand curve got broken, and that's why I think when it comes to this capex investment. Whether you're a hyperscaler, a neocloud, like a core weave, anybody building data center infrastructure, uh, pretty much is going to win because that demand.

And for any of you who are using agents right now, assuming almost everyone here is, you know that you just want to use more and more, you parallelize it, and you do more and more. This investment is happening, uh, and its biggest constraints really are access to Capital, which seems kind of crazy at 700 billion dollars, but it's really, you know, the access to power cooling and the ability to just manufacture this stuff.

So, there is like a limited physical constraint to it, but this is likely to continue for quite some time. However, everything above this is really built on open source, whether as at the base infrastructure layer with things like Linux and kubernetes training with tie torch Ray inference with things like vlm, uh, openweight models.

Things like deep sea Kimmy. How many people here are using open wave models? Okay, quite a few of you, quite a few of you. And then agents, of course. Natively built with open protocols, like mCP, uh, you know, desktop Frameworks like booze to deploy them and much, much more, and I'll take you through that step.

At layer one, the Linux foundation's projects were proud to say really own this lower level substrate, like Linux, has literally become the substrate of all Computing in the world, other than a couple of desktops whose names I can't recall.

[Speaker 3]
Cloud all the world super computers. Most of the world's mobile devices, it's all running on Linux, and on top of that.

[Speaker 1]
For inference, workloads, and orchestrations, it is the cloud native Computing Foundation family of projects. It's you know, uh, kubernetes. It's all of the tools that you need to scale out AI training AI scaling AI inference that really is owned by open source. At Layer Two, where training happens. This is where you do all of your pre-training.

You take all of your data. You run it in on a server to train your models. This is where pytorch really also has become the open source defective standard and the reason for that is because it's a neutral, open platform. And because it's a neutral, open platform, all of that Hardware investment is really enabled by tools like pytorch that are in.

A little bit. Whatever silicon is out there, it enables this. This sounds pretty familiar for those of you who've been around Linux for a long time, one of the great breakthroughs in Linux was the fact that it was able to hop from, you know, its original x86 home to arm two, uh, to risk five to other semiconductor technology.

And that's what makes it so prolific. At the third layer of inference and scaling, which is where we're seeing incredible growth again. This is where open source plays really, really well, and has become the de facto substrate. The important thing to understand about this, and again for those of you who've been around open source for a really long time, no.

One of the things that open source is super super good at is optimizing performance. For finite Hardware resources, it's one of the things that Linux in fact does really, really well, like back when Linux started going into the mobile market. The Linux developers, who were building devices using, you know for Android?

We're trying to get the most out of battery life, so they were doing work in the kernel and in Linux in order to optimized battery life. That optimization actually also translated into Data center efficiency, which made the data centers more efficiency efficient and allowed them to have lower cost of power and crewing, right?

Same story now, but at a much, much larger scale, you know if, if? You're really constrained by the availability of your company to get access to Nvidia Hardware or rent it through a hyperscaler. The only way you can get more bang for your buck is using things like vlm and Rey, and all of these open source projects lomb to get more efficiency out of that finite resource, and you need to amortize that resource over a long period of time again.

Open source has proven over and over again, and this ain't changing any time soon. The best at optimizing at this layer of the stack. Finally, in the model World, open source is also doing well with open weight models, right? So, obviously, the frontier model providers is a huge amount of investment, I think.

Just this week, I saw announcements that both had profit and open AI, raising additional tranches of multi-billion dollars of investment, and these Frontier models are real and important. You know, I certainly use them every day, but we, we. Also at the Linux Foundation. Use these open weight models which tend to lag the closed models today by about three to six months.

Think about that, you know, it was not too long ago just over a year ago, where these models really trailed by over a year in terms of performance relative to the frontier. The Munich's Foundation actually did a study with MIT or chief Economist Frank Nagel kind of looked at okay.

How are open weight models performing versus proprietary models and found that companies were starting to really adopt open wave models because the cost or the performance was incredibly Advent Pages, you know, 90 is good. Would catch up in about three to six months, but 90. Cheaper actually means a lot.

And so the estimate we looked at and this was about, uh, eight. Nine months ago was a collective 25 billion dollars of needless spend on overspend on Frontier models that could just as well been done in a much more efficient way in open weight models. So open weight models this game is kind of over.

They're going to be a permanent Park of the AI landscape when I talked to CEOs and folks who are. Employing intelligence in their Enterprise and building out agenda control plane technology. One of the big things that y'all tell me is make sure you have configurable intelligence. Meaning B model promiscuous, you know today?

It might be Claude tomorrow. It might be codex the next day. It might be Kimmy two on your desktop, then it might be when then it might be an openweight model from the US, which teaser a guarantee. In 2026, we are going to see a frontier open weight model built here in the United States that you are going to love.

Check out companies like reflection AI. There's a bunch of other ones in Silicon Valley coming out with these. This is going to be a permanent thing, so. His fourth layer open models continue to be a thing that they will be a much more important thing. As Enterprises deploy configurable intelligence and realize the price to value for intelligence, really, really happens.

Finally, at the top of the layer. Agents open from day one. How many people here have heard of our agentic AI Foundation? So, we announced this in December of last year, which seems in the world of AL, like an eternity, uh, but we have already gotten 184 organizations. It's one of the first times I've ever had a long wait list to join a Linux Foundation project, you know, usually I'm begging people to participate.

I'm like, no, trust me. This thing's going to be big. Now, you know, people are angry with me about not being able to join as quickly as possible, and the reason for that is because. Basic protocols like mCP, things like x402 on the Commerce front. These are the fundamental building blocks of an agentic stack, and all of that is going to be open, and it is being built right now.

At the egyptic ad Foundation, I want to take a little bit of a Segway. For those of you because that are building agent platforms tools, how many people are using agents today? So almost everyone but my sister.

[Speaker 2]
Uh, so the the, how many people are using a claw like an open claw Hermes?

[Speaker 1]
All right, just just for me because I want a little market research Hermes. Open call. Okay, even that's, uh, that's interesting. I think a lot of the same people raise their hands, so that's like a terrible a surveyor. But if I get asked all the time, um? How do we deploy agents at our organization?

How can I really get the most value out of age just beyond just using? You know, kind of quad co-work, or you know, nodex, or some of these cam agent tools and I, I, when I first started working on the agenda foundation and going to different meetings. I was really sort of, had this kind of weird imposter syndrome where I'm like, you know, what?

I just like, I gotta figure out. Get up to speed on this stuff. Like, I had no idea how this stuff works and how to deploy it. Good news for all of you. If you're thinking that nobody knows exactly, and this is what the agent AI Foundation is building, it's defining this stack, which is a really interesting set of Technologies.

And when you sort of pick it apart makes a lot of sense. If you're going to deploy a digital Workforce, you need management. You need ways for those digital workers to communicate with each other to pay for things you need an ability to review their work in progress to validate whether that work's been effective enough you need training, you need skills.

You need all of these different layers, right? You need a control plane to manage costs to configure that intelligence to be able to deploy. That are trained by experts in your company, and so on and so forth. And so, when you're looking at employing agents in your Enterprise, you have to understand every single one of these flavors.

With open source in the agenda, Ki Foundation are going to do, is they're going to just like cncf Define the stack that you can count on, you know, mCP? How many people here are using mCP or how many people have written an NCB server? So quite a few of you, you know?

MCP now is a factor standard for providing context to agents. A2a is huge in Asia, where clause are all the rage and being deployed on mobile devices, and they need. People off to talk to each other, but you're going to see every one of these layers being defined at the eugenic Gap Foundation so that as you deploy agents in your Enterprise and you consume this Upstream code, you could be confident that.

Is it a neutral organization and very, very well managed. Um, it is just amazing what's happening in ancient life. So I went through all these layers one through five, but I wanted to point out one layer of the staff where maybe the bear has eaten us a little bit, and that's in in the data side.

So, I think a lot of people out there think that all of these Frontier models were trained with sort of open data from the internet, and we kind of sucked all this stuff in from an open internet, and that was weapons used to train. It turns out that is not actually.

The case. The amount of investment that a frontier model provider will spend in data licensing is actually quite massive. And when I go and talk to folks at, you know, open web organizations places like common crawl and others who, which are large internet data training sets, but they tell me is that their data set isn't getting more open.

It's actually getting less stupid. And when you actually use AI, particularly AI agents in your Enterprise. For any of you that even dabbled, what you realize is that the intelligence really doesn't do much for you without context. I mean, that's literally why they call them out of context protocol if you're not able to connect intelligence to information about what your customers want or historical data about your manufacturing process, essentially, we've actually enabled a.

What that means is that data is more of the commodity or more of the differentiating thing. Not only other stuff is interested out in those five layers. This really an open, neutral commodity that we can all use. And unfortunately, it's not getting better. It's really getting much worse. I see a lot of legal uncertainty cases that are still working their way through the court system around Concepts like fair use or training Frontier models.

We're seeing a lot of technical infrastructure walls, you know, cloudflare, uh, has, you know, a default to deny for AI crawlers? I'm, you know, I'm sure that you've all been just in your own web browsing. Noticing how much more you have to verify that you're a human when you go from one side to another.

You see a lot of the big sites that we're using for have been used for trading Corpus, throwing up paywalls, and so on and so forth. You, you also see techno-nationalism where different regions and governments around the world are starting to realize how important this data is and starting to essentially create wool Gardens around their particular jurisdictions.

And so. This is sort of depressing, but I want to offer maybe some solutions that we're starting to see. Emerge at the Linux Foundation, uh, that might give you a little bit of Hope that we can, uh, actually eat the bear here. And what that really is all about.

Is that? And we've seen this before whenever there's too much consolidation whenever there's too much close. You tend to get a counter reaction, and I think we're going to see that, uh, happen also in the data space right today, really? You have this closed arms sales billions of dollars of investment happening, like with companies that have the funds to be able to do it and what we're preparing for at the Linux Foundation.

Is a counter reaction where people who have just as many resources as the folks who are investing right now in data might go ahead and combine their resources to share data as well. I mean, you know, if you look at the history of Open Source? It moved far beyond a hobbyist movement quite some time ago, where companies that had been in proprietary software made a conscious decision to share software as well, right?

You know, companies like IBM? Who invested a billion dollars in Linux in the early 2000s were hardly Saints when it came to being open. They were one of the largest power portfolios in the world, and they were historically proprietary software and did a Computing company, and they decided to go to open because it was a better strategy for them.

As the market evolved, we are going to see the same thing. We're building open data licenses to help enable that we have our cdla, which has been signed off by all of the major legal teams of all of the Linux foundations member companies. We convene them to come together and decide how can we collectively build out legal framework to scale and sharing data, and we have a little bit of a canary in the coal mine with our overture Maps Foundation oh Richard Maps is a multi-million dollar data sharing effort.

It's the largest geospatial mapping data set in the. Used by companies like meta, Microsoft, Amazon TomTom to help create happening services to help create augmented AIS or augmented reality experience through that, uh, mapping data. And that's just the Canary in the bullmite. We are going to see more and more of these shared data assets, so I think right now, at every layer of the staff, we're doing well, except the data layer.

And I think that we're going to see a counter reaction with these open data consortiums. And if you think about how these consortiums will get built? The limiting factor is not actually technology. The limiting factor here is money. And I think what we're going to see happen is that you know if we're spending billions of dollars on Hardware and people want to reduce and make more efficient the cost of intelligence you're going to see, just like we see in the software world, a collective investment and shared data.

So, I want you to just kind of bookmark this spot, uh, I think there's going to be a lot of room here for the Linux Foundation, our member companies. For other organizations on the Linux Foundation to really take advantage of this data sharing. So, I want to talk a little bit about AI, Doom, and blue now.

And, uh, the Doom and Gloom. And I think I asked, uh Peter norovic, who's one of the kind of founders of the AI movement kind of wrote the book on a lot of artists. Intelligence is at Google. He's a professor at Stanford right now. My question, I had to him.

He gave this great presentation on AI coding. The question is, when can I get rid of Venus tour bolts? You know, if the AI is going to be doing all the coding, you know, as you're going to be your role for the open source Community, one of the questions people ask me all the time is, like, hey, if ai agents are doing all the coding, are there going to be more people at kubecon or less people that who come, will there be more?

Were less developers. And I kind of want to talk about this by framing it as a cheat code concept, um Tom Wilkie. The CTO of grafana has a line that I love, which is open source is the cheat code for AI. Any, what he means by that is because llms were trained on open source code agents naturally discover, operate, and extend open source projects like ancients actually prefer open source, because most of these llms were trained on open source.

Uh, and so he sort of talks about this being this cheat code for AI and then Rich Aberman is a veter capitalist firm with Sid sigilant named Cookingport Ventures. He wrote the inverse in April, which is AI is the cheat code for open source. What he meant by that is.

It's chica because now anyone can contribute. There's even more people will be able to contribute, uh, to a good source. So I think agents are. Going to do a lot of Open Source work because they're actually going to gravitate to that, and there's going to be more people working in a resource.

The cheat code goes both ways to both. These things can be true. Let me show you what that means. Uh, first of all. Starting in about November. And this is when it is 4.5 came out permitted. Rocket what we really saw was Escape velocity in the ability for Frontier models to be able to play the code for agents to actually do coding work.

Now, I remember this really well, because I was, uh, maybe a month later on vacation somewhere, and I called up Greg Crow Hartman because we're the number two long-term stable kernel maintainer and I said, hey, Greg, you know, I want you to go try, uh, I can get oops, opus's.

Had just been released to try these AI tools, right? And I got the same reaction that I always got from him, and Venus and other Chrome developers was, like, dude, we tried that this stuff sucks. You don't get the kernel, you're just the suit. Yeah, they've been through 20 years of this, right?

And so, I figure. After 20 years, I've been a call on a personal favorite. I'm, like, great. Listen, personal favorite. Just go try it, like, just as a favor to me. I know it sucks, and I suck, and I'm the suit. I've just tried, and then I, as is Greg here, by the way up.

Um. After getting these emails. Previously. Wow, we can do this, and I think this is the big difference in the last six months or so. Is we really reached this point where the AI tools are not crappy voters. They're actually pretty damn good. News and agents are a really creating serious efficiency, and, and the reason I know this is like, for some of you, who've seen me talk three times before.

I used to talk about, like, hey, if these AI agents are gonna, you know, replace, uh, software develop? This is like a year ago. I'm like, where's all the code, like the App Store, the number of apps on the Apple App Store had not gone up. Like the number of projects I've given up had not gone up, and I'm like, is it so good you.

You would think if all these agents are in code, where is it? Uh, and guess what? That damn, just broke. People are using agents to rapidly develop, and here is a great illustration of what that looks like. You know, literally. You can almost map it to when I was whining about this fact.

Like, hey, we're not seeing any of these codes to November, December of last year. These things come out, you know, we get these releases. Codex comes out what Opus four, six, and seven come out. And wow, look at that, and it keeps going up. And so what's happening here is the dam is broken.

People are really writing work out. That means that we're not seeing less developers. What we're seeing is more developer productivity that's leveraging agents in this intelligence area. It is really an incredible cheat code for, uh, open source. And whether you want to forget whether AGI is going to happen.

And you know a little bit, all these intelligence tools take over the world really. Honestly, it just doesn't matter right now, because even if AGI never happens, this stuff is really, really, really freaking good, like Google claims, a quarter of its code is AI generated. I think Mazinger here from Google, but you were at Google recently.

I think it's probably more than that way more than that, so maybe fifty plus percent. You know, Rakutena? Company in Japan 79, faster time to Market, you know? At meta, I recently talked to an engineer who said, like, nobody is writing code at that. People don't write code anymore.

It's the agents that are writing. What's important to understand is that the intelligence is now writing that code. But people still matter. And again, this comes back to this debate. That's both ways, right? You know, it's this great cheat sheet. We're going to be able to have these agents on time because we do all this stuff, and then the fear is like, what happens to all the people and this is what's really, really important to think about and why data is important and why context is important because context lives in people, not the model, right?

You know your customers? You, you remember all that institutional knowledge in your particular organization? Whether you're a small company or a big company right you, you might recall a customer conversation you had. That's not. That's not public data that will never be public data. I think there'll be other forms of shared public data that this a n, and it's that context that's in people's heads not figuring out.

You know how to write code, but deciding what code should be? And then writing. More of it. That's what's really going on here. So, for all of you, how many people here are software developers in the room? Yeah, a lot. Obviously, is the next, uh, fear not. You are not going to lose your job.

I, I got it. I gotta be honest on this one. A few months ago, I was a little bit lean in the other direction and secretly thinking to myself, I don't have to put up with all these open source people anymore. They always complaining about, you know, the coffee selection at our events, and like, you know, it's like, did you not predict a thunderstorm would come in?

My flight was late, and I'm like, this is gonna be great. Let's get it, the agents. It turns out there's going to be more more of you, we. How do we know this? We're already seeing it. So we just recently did a survey, and we looked at what is happening with tech jobs.

Don't believe all this hype out there that ai's going to kill tech jobs. It's not we having that tech jobs are going to be more important. We had an event in New York a month and a half ago, our mCP Dev days event, we had a job wall that was much larger than this entire half of.

The screen here. Filled with Post-It note card job board posts for people who could help build an agent control plane who could help build a security tools for HS like, help, you know, Implement this stuff at scale. Openai, and, uh, you know, a group of private Equity investors. It's just I think three days ago announced a.

Billion dollar fund and the acquisition of a services company that they're going to invest in to help people build a cheapest Solutions. Do you know who's going to help these eggetic Solutions get built? Engineers software developers people who actually understand this technology can make it safe and effective and extract this complexity of ways.

And so, what I think is happening is not a reduction in jobs. It's an increase in jobs, and this is. Not receive here. You're not maybe going to write soccer anymore. If you're a developer, you're going to work on software security. You're going to upskill to agentic management, but boy, there is a lot of opportunity here, so take advantage of it and see you soon.

I think AI coding is the next abstraction layer of tech and history, I think, is going to prove me right and open source will be the subscript. I mean, you know, when my brother, Tom, and I grew up, we ran a bulletin board system out of our house when we were kids and we used to, uh, take what doctor Dobbs magazines and we would like re-type machine code into the computers, and this is very small group of super nerdy people here in, uh, Minnesota, who it is just a small group of folks at this time.

What happened is as new abstraction layers and Technology? Of course, you know, you became, uh, became a bigger Community, right? Because, oh, now, I have programming languages that I can use to write code more efficiently. Now, I have abstracted programming languages where I understand language pretty well. I can make the machine do things in a much simpler way, and now I have GitHub and I've got this error of social coding it, and uh AI agents are going to be that next abstraction layer where any of you?

And describe what you want and write that up and doing that in a secure, reliable, effective ways to take a lot of engineering coordinates a long time. What this is going to do is create an incredible Revolution of incredibly unsexy code. Uh, what we're going to be able to do now.

That subject matter expert can work with an engineering team augmented by agents to write software is write all that software that we wish we had been able to write a long time ago. It was just too expensive to write too difficult to write too difficult to take a subject matter.

Experts knowledge and transfer it to an engineer, uh, and Implement. Now, the subject matter can directly work in making these agents build the constitutions. I'll give you a very specific and ear and ear example. I have a 18 year old daughter who's going to play college basketball, uh, in the fall in California, and she and I are going to code up a road to college basketball app.

On a train, how to get recruited, how to speak to a recruiter, and all these little tools that she can use for a kid who wants to go to an academically a high performing school and play college ball and the cool thing is. And she. Is a little bit technical, but she really knows a lot about how to recruited for college basketball, and she's going to take all that knowledge and directly deploy it using a genifique AI tools to create this super cool app.

Like, and that's the power to get the subject matter expert that knows everything about everything about that particular Niche, and they're going to be able to code it up so, and it's kind of a boring revolution. In that Bible, we get to create my product development scene this year in the front row, and they know that for years I've been coming up with new features every week that they've never been able to implement, and they were always real jerks about saying no.

And now, they're saying yes, and I love it, and that's the important thing to remember. It's not going to be less. It's going to be more. Value is going to be true to this layer. You know, all this investment is happening at the infrastructure layer, the billions and billions of dollars.

But what I'm telling you is going to happen, and I don't know what the time frame is, but eventually that application layer is going to be where value accrues to like sun is not given a business anyhow, right? This was the.com company at the internet infrastructure era, right at the mobile era.

It was semiconductor companies and Nokia. Companies that we're building mobile devices. Now, it's all about Instagram and Tick Tock and strike, and I think we're going to see the same thing. My only caveat is, I just don't quite know the timing here. Because there's so much heartbread of the structured investment to happen.

But if the stars align and we can build that data center and Hardware infrastructure out that openstack can optimize it effectively. To get the most out of that infrastructure for the longest period of time, I think that's when we end up Landing in all the value according to this higher level of the staff built on open source technology.

And so that is. The good news is that open source with a little bit of a side Journey down. Data is just dominating the stack, and the reason for that is because it is neutral. Everyone can collectively invest. Most importantly, it makes this stuff more efficient so that we can naturally flow to the place where all the value accrues, which is at the application layer.

All the momentum is behind it to Source. The entire stack is built on open source. Everything is good. However. That's the optimistic part of the talk. Now, I have to give you the tough turn of the talk, and if you'll allow me to go about five minutes over. I'm going to tell you a little bit of a depressing story about the bear now, eating us.

And the problem is around cyber security. Ai is writing a lot of code, but AI is also finding a lot of cyber security vulnerabilities. And here's what it looks like. You know, if you look about the past, you know, decade, or so? There's been this? Back and forth between adversaries and Defenders in cyber security world.

And the adversaries would try and find sturdy vulnerabilities. Exploit them, do that stuff, you know, uh, whether it's a, you know, an exfiltration of data, whether it's malware attacks, whether it's cyber extortion, you name it. But there was this back and forth between adversaries and Defenders, where you know?

Uh, it would be 63 days for a mean time to exploit the number of days between the vulnerability being publicly disclosed and being exploited in the wild to now, minus seven days. According to Google stem trains for this April, negative seven days exploitation is, on average, happening before a patch is released.

Think about that exploitation is happening before patches get released. The balance is off. The bear is eating us. One Frontier model. Would be anthropic ethos. Model has found thousands and zero days in just a few weeks. Um. You know when anthropic bench Market against vulnerabilities and Firefox 147 JavaScript engine, It produces working shell exploits 181 times out of several hundred attempts, its predecessor, which is about 6 months older, succeeded twice.

It's a real generational jump. The bill for cyber security is coming with you. Uh, I don't know how many of, you know, Thomas, dolly, and he's a better known as Paul were playing is a very famous, uh. Cyber security researcher. He has this quote, which is. A quote that people in the open source World know well.

Which software was never designed for purpose period? You know, we favorite features over testing. We didn't document this stuff as well as we should have, and we would complain about it for decades, uh, Brian Fox, the CTO of sonotype groups made in Central this year. You've been complaining about this for, like, more than a decade, right?

He's like, someday the bill is going to come due. These poor security packet practices are going to come back to bite us. No joke that day is here. The bill is due right now. We need to do something to fix it or this balance, which is now minus seven days.

Is going to get too out of wax, and it's going to put us all positively at risk. The good news about this is that there is something we can do about it. Because. Um, not only is this happening, but? We have the same tools that the attackers have. Defensive AI is already starting to work.

It's just not working fast enough how many people here have heard of project last week, which the Linux Foundation is part of. So, a few months ago, anthropic came to a group of organizations all the companies that create was the imported software in the world. You know, whether it's Microsoft or Power local networks or Amazon or Google so forth and the Linux Foundation and said, we want to give?

A head start as Defenders in this new world, and we're going to give private access before we release to the public. Our Memphis model, so you can sort of get ahead of this. And what that does is it tips the balance a little bit more in the Defenders favor because that model is only available to a very small amount of folks break compartment.

The electrical project is using it right now. As, of course, a crusty kernel developer. I asked them, you know, what do you think about it? Well, it's finding a lot of stuff had already found, and you know, he's kind of, like, well, I'm not sure. But then I asked him, would you like me to take it away?

And he said, no.

[Speaker 3]
So, something's going

[Speaker 1]
up. Uh, these tools are good and what we need to do is get these tools into the hands of Defenders as quickly as possible. What is another good news about how we can defend against the bear? Eating us is that we already have a bunch of tools that we've been working on for a long time, uh, we've got scorecards.

The open source Security Foundation, we finally got package signing into all the major package management Registries, we have supply chain levels of software artifacts standards that help end-to-end security and providence across the supply chain we have. Software bill of material standards that help people understand what software they're deploying in production so they can better pass that software more quickly and so on and so forth.

We have coalitions of the willing like project glasswing that are coming together and spending time, money, and resources to batten down the hatches before anyone else can. This Coalition is particularly interesting, and we're proud to be a part of it. Um, with a small group of companies. But the point I want to make today if we're going to go remediate the world's Collective open source software and retire that technical debt that Thomas was talking about.

This has got to get a lot bigger a lot faster, and it's not just going to be glass swing. We need more of these glass ways, and I think it's really important. And the most important part and the thing I want you all to think about, and then you want you to take back to your companies.

Is that it ain't a technical challenge in that sense? Look at this. We have coalitions of the willing. We have the tools to get it done. What we need is collective will. What we need is to get ahead of the attackers because the attackers only got to be right once, right?

They don't care about what tool, how they get access to that tool. They don't need permission to break things. We have to do better. The good news for us is if we have the will, the tools are there. These tools are actually really good at writing tests. Why can't we go back and collectively create that test coverage?

We all neglected from 30 years to help us be more secure. Why can't we collectively succand folks from all over the industry to help fix vulnerabilities? Many of these maintainers, more than a helping hand in terms of cash or a bug report that actually fixes with tests. We can do this if we have the will to coordinate, and that is what we're going to have to do in the next three to six months or this situation is going to get much, much worse.

So, in conclusion, what I'm asking you all to do today here is to think about whether you're working on an open source project or if you consume open source technology. To one adopt that defender of Staff right now. Like, if your project is not using a baseline standards for cyber security practices doesn't have an s-bomb file, uh, you know, isn't using Sig Store for package signing.

Get on it because you can't complain that the tools weren't there. When people start to lose trust in all the good things that happen in open source, because, uh, this code is no longer trustworthy or secure. Wire AI into your software development by segment like AI is super good at static and not Dynamic testing.

Like, I don't know if you all remember. Like, you know, 10, 15 years ago, we were using all these, uh, testing tools, and like static and dynamic code analysis and the number of false positives was infuriating, and people followers like we give up stuff's worthless because I can't figure out signal and annoyance.

Guess what's really good at figuring out signal to noise AI tools? We're actually, really, really good at it. You gotta check these things out, and even if they're not perfect, they're a lot better than the alternative. Me, nothing. Third, I want you to all help fund the maintainers who are carrying this load.

We don't just need, uh, people which we need a lot of, but we need to support the maintainers who actually have the commitment somebody has to merge these AI patches. And at the end of the day, that bird is going to happen by personal. As a maintainer, we gotta support them to do that work, and they're going to have to do a lot of it really fast in the next few months.

Participate in these projects. Number four, join open source Security Foundation, participate in helping to coordinate the remediation of all these vulnerabilities. And then, for goodness sake coordinate. This is my spinal act. Any are going to have to figure out ways to coordinate this work. Why, because if we're finding vulnerabilities at light speed, we can't just dump them on the world all at once.

Why? Because of vulnerability is a map to an expert in the excellent to happen in the minus seven days. Most companies take several weeks to deploy fixes that are already Upstream. I think Brian and Maven's Central, uh, people using the bad version of log4j. It's like, download like 50 million times a month.

People are still on the, you know, bad version of old packages. We need to fix that. And so we're gonna have to figure out a coordinate how to display securely how to share it effectively. And if we do all of this? I think we can eat this bear, too, but it's all on us, and we will to do it.

In phase one open source, ate the baron AI and phase two, the bear is eating us, but we get the collective. Will we decide to do this together? We can get it done. That's what I want to leave you with today. I want to thank you to con for coming to Minneapolis.

If those of you did not understand the eat the bear reference, uh, it's from a film from a pair of Minnesota filmmakers who were famous for the movie Fargo, but also big Lebowski, uh, you can check it out online, uh. And I want to thank you all for coming over today.

So, we've got some incredible speakers coming up. Uh, our first speaker is from Google, uh, he is a senior software engineer and manager at Google. He leads engineering for the Commerce AI. Native integration protocols at Google. Remember, I was talking about x402 well. X402 is not the only way that agents are going to buy stuff.

There needs to be other protocols, and Google is leading in these protocols through something called UCP, the universal Commerce protocol, and it's an open standard for Next Generation agent and Commerce, uh, please, welcome Aaron Singha, who's going to come up and tell us us. Ucp.

Hello, everybody! And welcome to this talk on Universal Commerce protocol.