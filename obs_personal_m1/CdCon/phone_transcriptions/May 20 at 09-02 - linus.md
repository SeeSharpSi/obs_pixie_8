---
type: transcript
topic: work
---

[Speaker 1]
Uh, welcome back everybody, uh, we have a great lineup today. Obviously, we have a great speakers. Before we kick off, I want to share next year's venues

[Speaker 2]
and dates with you for next open source Summit, and this is pretty exciting because we are going to double down on Minnesota next year. Yeah, so we will be having it in Vancouver, Canada.

Texting me again jokes?

[Speaker 3]
Uh, but yeah, we're excited. Please

[Speaker 2]
come next year, Vancouver. As you all know, it's a beautiful city in lovely Canada, uh, and we hope you can join us. Final thing before I bring out our first speakers is stick around for the raffle. We got lots of cool prizes. You got to be here to win, so hopefully it'll stick around.

Uh, with that, we're gonna kick off today with, uh, someone who needs very little introduction. And is in a great mood. This morning, we're having so much fun talking back today. We have Lena store balls here as a creator of Linux.

He's joined by Dirk Hundel, who is a long time open source. Contributor has been a huge Community Advocate and leader, please. Welcome to the stage.

[Speaker 1]
Good morning, everyone. Um, my name is, I have been doing Linux and open sourcing. One of other things for a very long time, and I always enjoy the opportunity to talk to this guy. Yes, I'm I'm Lanes, and I don't do public speaking anymore and having it for a long time.

So that's why we keep on doing these Q A fireside chat kind of sessions, and this is actually number. 30, so we are.

[Speaker 2]
We are celebrating our own little anniversary here today, uh, lovely weather in Minnesota. Sunday night slideshow, that's very impressive.

[Speaker 1]
Super lucky! I made it to the hotel right before it started, so I enjoyed that.

[Speaker 2]
The other thing we always hear about in Minnesota, nice how nice

[Speaker 1]
people are here. I learned that yesterday morning, crossing the street blocks from here on a walk signal at the light and with a daring leap imagined by about this much. Not to be killed by the SUV drivers. Yeah. I need to hide after this presentation, so no one, uh, twice again, so?

Let's do something different. We've done this so many times.

So, um, I know that your YouTube channel of 3D printing we actually happen to have the same 3D printer and one of the things that is interesting in this technology space. Is that basically everything is open source? The old, soft perspective everything is built and open source. Those who follow this stuff know their strictly a bit of a thoughtful about the agentcling.

What it might mean, or what I found interesting that in this in this super? Leading Edge constant in new development space. Everything is done in open source. All the development happens there and the tooling that we use is distributing open source, and 3D modeling is is a big part of the in 3D printing, and I learned from you that we both don't like the visual tools.

We both like tools where you actually write program code. Yeah, so open scab. Have you actually used? Code hasn't worked on the project, or I could just do. I'm just a user. I don't know. How many people here actually do things like 3D printing? Yeah, oh yeah, fair enough.

And and the same people among you use these nice visual tools where you can see what you're doing, but when you come from a programming track background like me, I actually like describing things in text, treating 3D printing as program and. And yes. All the sufferings open source, but at the same time, this is something where I like doing the.

The toys I'm tinkering and having something physical, which obviously my normal work is not. But when I do coding, I like to be really close to the hardware and work at a different level. So I use all these some other open source tools without actually ever walking. Getting involved in that project, because it's getting something that is.

So different from what I'm used to go. Yeah, and so, for me, it's it's always this, this fascination. Oh, this thing doesn't work, I want to fix it and look at the code. And I realized I have absolutely no idea how I would fix that. So it's, it's a wonderful learning experience that there are a million more things I know nothing about, but still enjoy music.

But what is really interesting to me, is that for the longest time we all have said, you know, the open source tools are kind of? Be a little blank here, and the proprietary teams are so much nicer and the device are actually really cool. I, I love the quality of people that you get that you talk about the 3D modelers they are.

I, I think we're actually past the point where people think that open source is just for engineers and that largely. Time gotten over the hunt, and I mean. Just look at all the people who now talk about it. Uh, limits in the gaming space to. I'm not going to say this is the year ago let's desktop, and that is an inside joke because I actually did this to the Press

[Speaker 3]
in 1998. But but I do think that. Open source. Obviously, it's very long accepted. Commercial, like serious space, but at the same time.

[Speaker 1]
My argument has always been that software is very complicated and the only really good way to manage the complexity of a complex infrastructure in so and sorts. And having everybody be able to be involved? And then most people don't actually want to be like, like me, and 3D printing software.

It's not that. That these?

Things I maintain, but it turns out as of a few weeks ago, Venice

[Speaker 2]
has

[Speaker 1]
done that before. Guitar pedal is on limous's GitHub, and you can actually play with a guitar effects pedal written by the one and only ministerials. Well, be careful now. Before we start playing with it. You have to manufacture it. All the manufacturing files are also pencils, so you can.

You can choose to actually send the design files over to your favorite PCB manufacturers. You could try to place the components by hand, which I would suggest to you not do because it's pretty fiddly, uh. And everything.

It's really fun, so it's gonna become tall balls guitar kettle. Check it out. I will change the world of music too. I am certainly, you will. So, talking about hobby projects a little while ago, you started another hobby project. Nothing big and professional, like canoe, but it's something that some idea took off and recently released last Sunday released released 71 rc4 and.

My usual question what's going on? How are we doing? Um. I've been saying that we've been doing the same thing, you know, for? I mean, I've been doing it for 35 years, right? But we have actually had the same process now in place for pretty much, exactly 20 years where, when we switched over to git, and then it took a while to kind of get the holes modern release process guide.

Uh, so for 20 years, we've done the same old thing. And I used to say that it's a working fines, and it's smooth sailing, and it's steady progress. And then, about half a year ago? Things changed. I mean, in the last six months we've seen. Lot more commits small details.

Just doing the numbers. I think the last two weeks it's been about 20 percent more commenced than we had in the previous release. It's over many years,

[Speaker 2]
and

[Speaker 1]
at first I thought, hey, people are excited about 7.0 released because I changed the major number every once in a while and I thought, hey. We saw that in 6.0 that a lot of companies wanted to get their stuff in for. And uh, it turns out I was wrong.

The real change that happened the last six months was? The AI tools actually got good enough.

Just development. On pretty much all problems. And we talked about this. Six months ago in Tokyo that the tooling actually lowers this initial barrier, the barrier of Entry to to writing a Linux kernel path. The tooling does a big chunk of the work, and that concerning has had an impact, and it's had not only a positive impact.

So, in the announcement of RC4, you announced the new AI. This, the security disclosure guidelines with especially. Point of view on the eyes. Yeah, so again, I have a hard time seeing everybody because I have the lights in my face, but how many people hear news actually AI for perfect?

Yeah, so. I have a love-hate relationship that I, I actually really like it from a technical angle. I love the tools. I find it very useful and interesting, but Is simply causing pain points

[Speaker 2]
and

[Speaker 1]
and the big pain points in. In Linux traditionally, and I suspect in most projects. Have not been so much. The code itself, but has been when you're forced to change how you work and people get into a rut. People know this is this is how I work, and this is how I like working, and then something comes along.

And for me, it was like a long time ago, around 2000, I had to change how I work because I did not scale anymore for the project as. Is crying? And that was, I still remember it being one of the more painful episodes in kernel development, and it was literally 25 years ago.

Uh, and I think we're seeing some of the same effects now with AI. It kind of forces people to get out of their comfort zone. So, we've had a lot of social issues with the AI generated. Five reports should also code, and then there. It's not a leanus, doesn't scale like it was 25 years ago now.

People don't necessarily scare like it takes a while to learn how to use the tools in. Maybe responsible isn't the right word, but in a way that actually works with the community and works with the other developers. And we are definitely seeing some other big one of the pain points recently has made the security mail list where people applying bugs with AI a lot of the time.

We went. A lot of bugs can be security issues, and I've said for years, decades that a security bike is a bug, but the other side of that is about is often a security bargain. You may not even realize it. And, and people think that when they find a bank with AI.

The first reaction seems to sometimes be. Let's send it to the security list because this may have security implications. And the security list for the colonel was overrun by duplicate reports by tenants. Hundreds of people running AI, often the same AI tool. I'm getting slightly different results, often with the same underlying cost, but newer blooded by people sending 70 bucks, and then you have.

List with very few people on it because it's all supposed to be super secret. And we spent all of our time just supporting these reports to to other. I think developers who do that area better. And we made the policy change that. Basically, if you find that security or any bug with AI, you should basically consider to be public.

And. Just because if you found in the 100 other people said bombing with AI? Uh, and obviously that when it comes to the things that really are security issues, you may not want to make the exploit public, right? Don't go and say to the world. Hey, this is a and this, by the way, I want to make it very clear.

This is not just about doing this car when you find the next, like, for any piece of software. Don't be that guy, oh God, who then crows about it? Probably can't say Luke, hey, I could ring down. Uh, this big company or whatever. Just let people know what the problem was and don't necessarily tell them exactly how to make somebody's life really miserable on a Friday action, so we are seeing some pain points with AI, and uh.

It's not that the technology is bad. I mean, I, I personally, really enjoy it. But, like, there's like the social issues that it causes, uh, have yet to be all worked out. I would say and social issues, I think, is the key. Here, we have this tendency for a long time.

I, I don't know. The heartbeat was the first one, but the companies who are branding the bug and create the domain and the logo, and they want to get all the fame for the body and then release it before they ever talk to the victims, I.E the maintainers, whoever?

Fix that, and we've had four recent local privilege escalation Department in Wisconsin, two of which were exactly this way. My response is always here is a company I never want to work with, because if you do that to the Linux kernel, you do this to anyone, you don't want to work with you.

However, we've had these four bugs, and I think they have really brought out a challenge that you just talked about, but between the Linux current developers learning learn. About the most privileged excavation and the world learning about it. There is a difference of zero minutes, so you have no opportunity to fix this, you have no opportunity to.

To get patches ready, you have no opportunity to actually help people who run the code. And so you said you, you won all AI bugs to be public, which I totally understand the logic of. But can you explain a little more? How bad does things? The situation that the the maintainers are always on the back plate.

Um, I'm sadly out of the opinion that we can't get around. Um, we had a small about. This was not a huge, huge issue, but? Any project in their Linux kernel we have. I forget 35 minutes. We have a lot of code. And that means that. We do have funds.

They, they're like daily occurrencies. This is not something shocking, and this should not really surprise anybody. And it used to be that we found bugs that were severity issues, and we would let people. By distributions. Now that, hey, you really need to upgrade, but we would not describe exactly what the security issue was, but being open source obviously meant that the fixes were all very public, but they were hard, quite often.

Subtle security issues are really hard to figure out.

In the timer when you have AI. You can just. It used to be that. We'd fix the bug. Um, we wouldn't tell people exactly what the problem was. We just tell them hey. We fixed the bike, please upgrade. Most of the time, nobody would figure out what happened. Last week.

We fix the vac. Within three hours, there was a blog post up about. Uh, the implications of that bug fix because security people love getting attention. They really, it's, I mean, don't get me wrong, we all do, but, but they often. Have their business. That's the way they make the name for themselves as they talk about security degrees.

If you're the first one to talk about it, it's news, so you get more more eyes on your blog posts. So there's a very really incentive. To be the first one and to run all these AI tools and to make a big splash announcement about how bugs happen. And I think this is just this is how it's going to be.

There is now nothing you really can do, and I don't think, for example, that the solution is to not do open source, because if you think that AI can't do reverse engineering on closed Source, you're in for a surprise, uh. I think most sergeants can be even worse in this respect because the AI can't help you fix the problems, but the AI sure can help find those problems in the first place.

You just set something very important because one of the things that I've noticed, especially with the more splashy ones in the last few weeks, is that these companies enjoy spending a lot of money and a lot of tokens on pointing out about, and strangely, none of these came with.

Even though all of these were in open source code. So, to me, there is, we're going back to the social responsibility and the it's kind of sad that you get all the attention from the of the genres for finding a bug, and you don't think you could get even more attention?

Hey, any journalists in the room, uh, you could get even more attention for them, existing well, and so to be fair, sometimes it is easier to find that effects so. I understand and, and don't get me wrong, this may sound negative to a lot of people, but I actually, I think it's all very good.

When AI finds a bug in any source code?

Is a short-term group. But long term is you found a bug. We fixed it, the the end result is better for it, so I'm actually this is part of why I actually really enjoy Ai. And again, I want to stress that the conflict is not that AI is bad.

The conflict is then that there are some social points and social pain points that that come with this new tool that we have 35 years of code that it's sometimes finds issues that we did not find. And it's going to take us some time to to just work through the the new issues, so I'm actually very positive about this whole thing.

I think finding bugs is great because? The real problem is all the bikes you didn't find. So we

[Speaker 2]
talked backstage about the impact all of this has on maintainers because they maintenance are already struggling with burnout before. And now, this flood of bug reports isn't really healthy. But are there any good tools that help you as a maintainer with code review with with understanding the patches that come in to help you with your work.

We have a I mean.

[Speaker 1]
We have a ton of tools for that, and I, I'd like to point out that Lance Cardinal is actually doing really well. We have every single release we have over a thousand people involved, and we have a solid cutter of maintenators that. Are there

[Speaker 2]
most of the time they get well paid for being there, too, and so we're doing well.

[Speaker 1]
Uh, all these problems that I've been talking about. I've been talking about the Linux kernels, because that's what I do, obviously. But think of all the? Tens of thousands of random projects that people maintain. That by not the Linens Carnival? And then maybe somebody's like pet project that they've been working on for a decade or more.

And they have one person or three people that are somewhere, so, and they get really burnt out when they get a flood of.

Um, sometimes obvious eai reports that just it's a bug report, and when you ask for more information, the person has done a drive-by and and doesn't even answer your questions anymore. So, so that's the the real burnout issues is, I think there. Uh, and now. Forgot what the actual question was?

That aside, I assumed there are AI told for that. Oh yeah, we we do use AI tools and and. I'd like to point out again. I actually work mostly with people. So, for me as a department maintainer, I don't do a lot of coding. I do coding on my toy projects on my guitar pedal on my like, I do coding for fun because I'm a programmer.

But my job is working with people, and I do not use AI to work with people. Thank you and I, I should suggest you don't do that either. But we do have a lot of auto paint tools, including AI, we have, like. Google, for example, set up this patch.

Tool thing that a lot of people are living. Looking at, I forget the name Shashiko. Uh, that Luke said all the patches that go to the mailing list and many. That's a review of them, and sometimes the review is not great.

But quite often it finds issues, and it asks questions and says, hey, what about this issue? Uh, and, uh, that's the public one. And there's a lot of companies working on private tooling for. Inside. Inside companies, but actually, these days, a lot of the. Main developers. Do local AI, which I actually would suggest.

Uh, everybody look into. You don't want to be entirely at the mercy of of the big companies that, at some point, decide. Oh, we need to make money to. So? You're showing your age because your your comment about tens of thousands of projects is really funny. This week, GitHub announced that they currently have 480 million repositories and, um, in a recent study.

Six hundred thousand projects were considered of important or critical use for Enterprise users of Open Source software, so it's literally hundreds of thousands and hundreds of millions. Overall, the the the space is so. Big it's. It's hard to wrap your mind around, but let's say this is a social issue.

We talk about working with people if you are at the beginning of your career right now, yes. And a lot of people do these Doom and Gloom. All code will be written by AI, and on the flip side, those of you who were here on Monday for just, you know, saws Jim's very optimistic note that that actually, we are creating a lot of jobs in the tech industry, and we're seeing hiring.

So, do you have something that you would tell someone at the beginning of their career? Here is where you should focus so. My opinion has always been that. Hey, AI is a great tool, but it's a tool and and when I see people saying hey, 99 of our code is written by AI.

I literally get angry because those same people I pretty much guarantee that 100 of their code is written by compilers.

[Speaker 2]
I grew up riding machine code, and when I say machine code, I don't mean Assembly Language, I need the numbers. And I mean, it leaves an imprint on you. I can. I still remember LDA is takes A9 on the 6502, right?

They took me a while to understand that writing down the numbers and calculating offsets for branches is kind of stupid, and people had come up with this tool called in December. Uh, and then later on, I figured out compilers are good, too. And these days, I'm thinking about AI tools are

[Speaker 1]
good, too. I'm still writing the code. I'm just, uh, doing it the same way I did, and when I was basically typing in numbers in data statements.

I, I personally 100 convinced that AI is changing programming, but it's not changing the fundamentals exactly the same way that you all use compilers to actually generate their code. You will all use well, not maybe all of you, but a lot of people will use AI to generate the code that the compilers use to generate the code, but the assemblers then use to generate the machine code.

Revolutionary in the same sense that we've seen revolutions before, and AI will increase her productivity by a factor of 10. I claim that compilers increase their productivity by a factor of that thousand. So, AI is great, but AI is not. Changing program. You may be changing other variants. Don't get me wrong, but I'm programmers.

I don't care. One of the things

[Speaker 2]
sorry, my voice is already fading. One of the things that I think has always been true when you look at the code written by developers. Good developers write good code. Other developers write code that then breaks,

[Speaker 1]
and the

[Speaker 3]
same will be true for the people, prompting the

[Speaker 2]
idol people who know what they're doing who understand systems will be able to prompt tools to write good code, and people who don't understand the complexity of systems will also. It will fail, and I think you do want to

[Speaker 1]
understand how it all works. In the end, I still like. I don't program your machine code anymore, but I still look at the generated code. So when I use a compiler, even when I use AI for my pet toy projects. I will use AI engineering code. I will look at that code.

I will actually still look at the assembly line, which end result because it's what I grew up with. It's kind of where my comfort zone and right now I'm playing with microcontrollers anyway, so. Want to actually look at the generated code and make sure? It's doing what you really wanted to do, so I think even when you use AI for coding.

If you do a project that you actually maintain long term. You need to understand, not just your prompts, but you need to understand the answer, too, because that's the only way you can maintain long term, and it's easy enough, and we see that all the time where you. Uh, basically generate a new project, and it's a throwaway project, and it's a one, one time, and it's over.

And, uh, AI is great for that, and I'm calling bytecoding. But if you want to make? Something serious. You're going to maintain it for. 35 years or something, and at that point, it's, it's a lot more than just writing the promise. To me, somebody else generate the code.

[Speaker 2]
Well, unfortunately, be out of time. I have a lot, no questions. I guess I'll have to ask them next year in Vancouver, when we'll do the same session. I hope you'll all be there. Thank you very much.

[Speaker 4]
I, I love the assembler compiler. Let's say that was a really good way to describe it, um.

[Speaker 1]
So, our next speaker is.