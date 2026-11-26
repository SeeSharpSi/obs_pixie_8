---
type: transcript
topic: work
---

[Speaker 1]
We'll start in one minute when the time kicks off. God, you're so straightforward, right? I know it's time fixation. Sorry. There's a reason I'm short driving distance to Boulder, Colorado.

Did you

[Speaker 2]
consult the economic Market? I don't need to because my cell phone is of course synced to the cell towers they care about time, even more than the atomic blocks. Do I think right? Welcome, everybody. It's day two of cdcon. We're delighted that you're here. For this first segment, we've got a panel discussion on

[Speaker 3]
agent agentic AI in production environments.

[Speaker 2]
Agents and production. And for me, that brings a lot of interesting questions that I think our pandeer is going to highlight for you. Jocelyn elect is our our facilitator. Jocelyn is here from Infosys. And.

[Speaker 4]
Sundeep from South Southwest Airlines.

[Speaker 2]
Fred Smith from SAS Institute that's SAS Institute, not the Special Air Service. So you, you should not feel any

[Speaker 3]
pressure you

[Speaker 2]
know on the Swedish Airline, right? It's the Assassin Street, North Carolina, and Steve Taylor from from deploy Hub. We're delighted to have him here. It's yours! Uh,

[Speaker 5]
thank you. Good morning, everyone. And Welcome to our final discussion on building an Enterprise or platform for for dictionary AI agents. I'm jotuna, and I'm working in Enterprise platform engineering, focusing mainly on, uh, scalable agentic AI systems, security governance, and also AI infrastructure. And today we are joined by excellent Bangle of experts from Southwest Airlines, SAS, and deploy Hub.

And I would like to, uh, ask them to introduce themselves. Thanks, Joseph. Hi, everyone. Good morning. My name is Sandeepopa. I work for Southwest Airlines as a Catholic Cloud devops engineer. Uh, some responsible for building large-scale. Csd platforms, as well as to include migrations. Basically, we have been investing more time on money on billionaire agents, uh, to make the developers life easy.

[Speaker 6]
Uh, so I'm Brett Smith. I work at zest, uh, SASA student Gary. We're a 50 year old analytics Ai and a machine learning company, um, I am currently leading the AI in the platform, uh, engineering space. I have previously been the security lead for all of r, d, and I might have put all the bodies where they are in the current pipeline.

I'm Steve Taylor, CTO of deploy Hub, uh, and the project lead for the articulous Open Source project. Um, deploy. How about success version of artelios and we are working on rolling out some mCP and llms to do auto remediation?

[Speaker 5]
Thanks for that. And yeah, it's a general question. Let's see that everyone is building today. Agents, like everyone. So, what do you think that if you want to move from a demo AI agent to Enterprise ready agent, what the agent does need actually?

[Speaker 4]
So, yeah, um, Enterprise ready agents. Agents works well in sandboxing, because, um. Let's get, uh, it's not really a production traffic. But when you move on to a person grade agent, it has so many different thresholds, different metrics, different logs. Um. And then customers in the live traffic. So it's, it's very hard to forget the traffic, so I think the number one thing I would.

I would look out for the production ready. Agent is accountability. That is the key, so if if an agent in production is making the decision, then it should have accountability, and it should have trace of white marination. What it may?

[Speaker 1]
Yeah, as you said about, it's like accountability like, and how should the organization should work on? Like how the agent is taking an action? What type of observability and traceability agent should have? Um, one of the things I look at when we look at. The accountability is first off.

You have to just scope the Privileges.

[Speaker 6]
Um, correctly. So, like Jennifer said yesterday, you know, Focus on baby steps? Read, only access for what the agent can do. But from there, like you said, uh, traceability is Big, you know, recording what the the prompts were recording, how it reasoned? Because one of the things that you want to be able to do over time is go back and do a replay of a prompt and see if it came up with the same reason or something similar, because then you can tell if the model's been poisoned or not at that level, so recording that that observability is very important.

I can add a little bit more to that. Um, so everything Steve said was true, um. One of

[Speaker 2]
the things that

[Speaker 6]
I've run into recently, um, is that I have started logging everything, like everything, including the stream content that comes back and forth from reasoning models. So, if a reasoning model is thinking and you want to see something unhinged to go read those logs. Um, the, uh, the and I'm working mostly with local inference and local models, because, um, I don't want to pay the co-pilot tax or the air profit tax for my company, I want to save us some money.

And a lot of times, I don't need that big L. I'm going to do that, but I do need to know everything that hysterical little model is doing so that I can go back. And, like, Steve said, review and fine-tune now, uh. Yesterday, I got put on the spot about checking prompts into git.

When you build an agent for production. The prompts are built into it, and so they are checking git and they are versioned, and but you need to be able to tweak them. And then, if you change models, you have to keep them again. And that's where the observability and the logging it becomes super important.

They, I

[Speaker 4]
don't know if you're

[Speaker 6]
running in Trace mode in production because I produce too much loss. But in the early days, when you're first deploying not being, you need to keep an eye on it, and you need to keep an eye on what it's doing. So, do you use AI to review the logs of the AI?

So, uh, no, I thought you'd take the laser way out, right? I

[Speaker 2]
might, uh, no, so there's a there's a mix here that you have to get to. There's a there's a spot where you can't cognitively read all of those blogs and understand everything that's going on. That's when you return to your unit experience. You start wrapping. And that's fine. Rep is awesome, uh, use it all the time.

Don't let your agent use it because it pulls the contact window to no Edge, um. But that's a different story for a different day. So, yes, I, um, if I run into something where hallucinate's really bad, like, um, I give it a ballistic repo, and I tell it, hey, tell me what's in that repo, and it tells me there's underwater technology in there.

I really probably have to go look myself, right? Because it's a grievous era, but if it's something smaller, there's a good shot. An llm will find the trace path where that you missed as a human because you just blew by it, right? So that's why I'm at, yeah, cool.

I just want to add on top of that.

[Speaker 4]
Now we have agents working together making decisions, so I think observability is more important than our innation is triggering an action, which is making, uh, the second agent to implement that action, so we, we should have like traceability and accountability built. And now that they are making decisions in the production environment as we've got the time, and I didn't Vlog all the stuff the sub agents were doing when I told the big age, and they could make sure it.

[Speaker 2]
Log everything. Log everything.

[Speaker 5]
Yeah, the first thing comes to our mind. Is security, uh, whenever you are giving enough any Asian autonomous action to take place with Enterprise systems. So, what do you think that? How should the governance should be in place like before giving the all the Enterprise systems to the AI agents.

[Speaker 2]
This goes back to sandboxing, and we said it once. We'll say it again. It's sandboxing, uh, in particular. One of the agents I have it has it creates a workspace with a unique identifier. It is not allowed to work outside of that space under new, no pretense. Now, your agent in your BS code or whatever floor IDE you're beating on, you can tell that, hey, you can do whatever you want, and you can just turn that switch into YOLO mode, and it can go out into the hard drive fast outside of your whatever working directory is.

Don't ever do that in production. Don't ever do that with even in development Cycles. Like, you want that thing to be. Have a very small sandbox that it works in and. Want to have very tight control on the tooling that is available to it. One of my things that I have.

Cut down very hard on is, uh, shell executions that they just don't okay. Write the tool is you're putting this in production, so you want to be very specific with what you're doing. You know what you need to do make a tool to do that thing, and only do that thing.

And then, don't let it. Don't give it excessive agency, which is just when we come down to yeah. Mcps are not that hard to create, so go off and create yourself an mCP to do that one specific thing. You know? Still skills that can often do everything in the world.

[Speaker 1]
Um, really tightly, same control, and you can have your AI create your MTV for you. It's not that hard.

[Speaker 4]
Agreed. So, um, I am rules would help like I would see. I would treat every agent differently like it has its own IM role and creative mind boundaries that it cannot copy on, uh, and take an action or trigger a Downstream event. So, it, it has gone. Where is that what it can do?

It only is focused on doing that. Yeah, and the I am.

[Speaker 2]
Just don't click give all.

Give it everything. Um, really, you got to get in for the fine tuning about. Yeah, hey, I am. I am, yeah, that's a good thing. Yeah, we should always give the leaps privilege to the agents.

[Speaker 5]
Yeah, and also like most of the Enterprises in any organization, depending on lot of Open Source AI Frameworks. And because recently also seen that there is an llm Gateway like llm, which has some incident has compromised. Version has been placed on the pipeline, so what type of action we should take before, uh, in, uh?

Taking any open source framework into the production?

[Speaker 2]
Okay, well, I want to run this thing, but um, so you don't need Frameworks anymore. Um, you've got AI. You can write for production things you don't need a framework. The and I'm not telling you not to use land graph not telling you not to use Lang chain, but what I'm telling you is, is that make a decision on why you're using it?

If you pick that particular framework and you tie yourself to it? There's a good shot. You will be tied to it where the life of that agent until you take the hit to remove it. Put another framework in, and if you wonder what it's like to maintain Frameworks, ask Mark what it's like to go from Spring Booth 5, spring boot 6, and when you see the pain in his eyes, you'll understand that you probably could have created a framework for yourself because you didn't have that many things you needed to do.

That is specific to what you're doing, and it wouldn't cost you more because you have the AI and write the framework. You also have to Pivot the framework every time you change the model because it acts different. And then, if we change my system prompt, it acts different. Having the flexibility to go, just redo all that stuff all the time is basically what you're doing when you're doing AI in production with agents you are just managing that harness over time.

And then, if you add Frameworks in and look, this is a hot take okay. If you've had Frameworks in, you're increasing overhead of I have to understand what this group over here thought that I should do with my agent and my models. Now, using the minimum pieces like I needed to be able to automatically download this model from a hugging face so I can.

Destroyed this whole area. I mean work on this thing. That's cool, right? But then, when you get in the deep of it, that's when you, you really should think about how much of that harness you need. And that's why it's sandboxing plays a power bottle

[Speaker 5]
role. Like, we have a member of vulnerability scanners available in the market. Where, where we stand off stage and? Don't give any production here. Don't deploy an agent that takes an action at 2 am in a night instead sandbox. And. Use vulnerability scanner so they can find out what vulnerabilities are in place.

Before deploying interaction.

[Speaker 4]
Yeah, once deployed to production, like how, how you, how should an organization should take care of the post, deployment scanning, or wall numbers scannings at all? Whatever exists in the code.

[Speaker 2]
Yeah, so you have, uh, two parts of it. One is the actual code. Um, like your python code and stuff like that that the agent, maybe um? Working from, but also then you have your your model itself. Both can be attacked. So, the vulnerability scan can happen for your python code pretty easy.

There's there's tools out there to do that, um. The vulnerability scanning of a llm isn't quite there yet. Um, the area of AI bomb is coming about. That's going to help with that. Um, but, and there's a couple open source projects out there that will help with prompt injection back door traps.

Those types of things, but? If you're using like clod or shadgbt, you're not going to be able to. You know, the hosted version, not your internal version? You're not going to be able to go in and do a lot of that, um. With those models, you can double check.

Uh, to make sure there wasn't a prompt injection, um. To verify this is what I had. I'm going to replay it. Make sure I got the the same result. Um, but overall, the tools are coming. They're just not quite there yet. Yeah, I can peek back on that one.

Yes, um, so, uh, I've been working with sneak, you know, free advertising with, you know, uh, working on their AI stuff, and I've been involved with their AI scanning since November. When we first became available to close the? The thing about that you need to know is this is.

An SCA scan or an FCA, a SAS scan permanently of an mCP server will not show you the vulnerabilities. Okay, the attack service in an mCP server is in the description and my favorite attack that I talked about. Every time I get a chance is the hidden ASCII characters that you can't see that they put underneath the description that execute?

Tell the llam to go execute something randomly. There's not a lot of scanners that will catch that, and so this is where you as a human need to go in and? Read the thing before you deploy it. We should talk about this with GitHub actions all the time. Don't go grab them off the marketplace, go pull them down, go through the code, and make sure it's not doing something silly, like exfiltrating all of your GitHub secrets to some random place in some random country.

Um, and so there's a due diligence you have to do here with those type of things that you're not used to doing. You're not used to looking for hidden ASCII characters. You're not used to looking for a a thing down at the bottom. That looks like just a timestamp and some stuff.

There's actually a set of instructions that the llm pickup and go. Oh yeah, I'll do that, and then you're cooked. Yeah, but those are the the, the prompt, inject the hidden prompt injections that will, uh. Really get you down the road and then like a backdoor attack is where it.

The llm was trained to look for certain keywords and then go off and do something. So, if all of a sudden, um, a developer types in some random string that matches that unleashes? The the Beast, uh, on your by accident. Good for those Nations.

[Speaker 5]
One size doesn't fit all. Every agent has its own. Your organization could develop an agent that does an entirely different thing, so it's important to shift the process left, um. Find our vulnerabilities very in advance, uh, during their development process, rather than waiting till your project requirements.

[Speaker 1]
Good thing. And, yeah, the main thing comes like scalability.

[Speaker 4]
So, the traditional software application scalability is entirely defined to the agentic AI scalability. So, what are the trade-offs between like the traditional scaling and the agentic scaling and how suitable we approach those?

[Speaker 2]
Why you need a lot of money? Yeah, um. So, for example, uh, if you want to?

Keep watch on a production LLM or agent. You have to have that observability, but also it gets into like running a shadow, uh llm, so the traffic comes in. It hits both the primary and the shadow. Not a shadow may not get all 100 of the traffic. It just be too costly, but it's going to give you, um.

Points in time that let you check to see if the primary was compromised in any way. Well, that means you need more money to run a second, LL, and all the gpus and stuff like that if you're doing self-hosting. So, it really comes out of a in my world, uh, money.

So, we've been talking about scalability because we're going, and we're going to try and do this with local influence. And, um, so I've got a VM in the basement icons and the associate software developer to add three gpus to it. I have three. Nobody has three, um. And then I fire up llama CBP with in router mode, which is, you know, beta, because you know the why not?

I'm going to put this in production. I'm going to use something that's not supported. And it fires up. And then I hit it, and it loads up one of my IBM Granite models that takes up three quarters of the B round. Um, and then I try and scale up.

I need another agent doing something over here, and it tries to fire up a smaller model, and then I whack bam, b-ram's gone. BM went down, everything's gone dead, and so to Steve's Point, I need more gpus. I need more VMS, so this traditional scaling technique, right? I've got this.

Agent is listed in the Kafka. I'm, like, oh hell, I'm gonna do this. Like, I've always done it. This thing's gonna put five of these things in a capture bird there around robin to pick up the the things they're supposed to do and? Get to the second one and reserve was.

And so there's money, money. Need more electricity?

[Speaker 4]
Yeah, that's a good one. Uh, yeah, and also like, what are the important layers of a platform engineering specific to agency care. Is there any extra layer which is needed explicitly good to add to the platform engineering level?

[Speaker 5]
Accountability, I think it's. It's a number one like, now, uh, we are no longer making decisions. AI is so building accountability around it and then building traceability and logging. Um, where I can use them to make decisions. It's more important than ever. So, I

[Speaker 2]
worry about the making decision piece because, traditionally, in. Regular software I could write. Evals did, like, you know, two, plus two, plus four, right, and I know that if I get too close to explore that, it's right. How do I check the Vibe coming back from an llm in picking mode and know that it hasn't run much?

And I don't have an answer for you. My answer, ask the question by staring right at you.

[Speaker 5]
Yeah, I mean it. It may not make decisions every single time. Not every production level decision like, you know, rolling back Productions, but it could make some decisions that would make life easier. I was going to say and the decision making.

[Speaker 2]
Um, you do have to go back to the sandbox and see because you've been watching the sandbox for a while, and you can see what decisions were being made. Now, you've rolled it out. The production you really need to compare the decision making between the sandbox and the production, and that gets back to.

Putting all your prompts and get yeah, and being able to run through those and and the results of those problems. What did it reason as because you need your Baseline, uh, to be able to say that this is what I'm comfortable with. I just spent six months looking at this model, uh, in the sandbox.

And I rolled out of production. Has it gone crazy on me or not? And that's what you need to really be able to measure. So, I'm going to give you guys a new term. You guys well heard of Asian harnesses. This is how you go and talk back and forth with the model we call tools.

Well, I've got a workflow harness and the workflow harness controls what happens and feeds the agent harness and tells it when it's time. The agent partners can go do something, and then when the agent harness comes back, it reviews what comes back, and if it is completely off the rails.

I catch it, and I throw a flag and the whole thing stops, and we open your issues. And humans have to go look at it right now. The workflow harness we have? Thought about much because you're always like, I'm just going to write an agent harness, and then we'll let the agent do all this stuff.

Seven deadly sins of A.I sin, number one, allowing the llm to run the workflow. Okay, I remember number one is expecting 100 accuracy. Sin number two is allowing the llm to run the workload. Don't let the LM run the workflow okay when you give it a decision, and it keeps giving them decisions.

But when you give it a decision, you give it two choices. You give it three choices. Do not let it make something up, cuz if it can't figure it out. Congratulation and confabulation is worse than um, uh, hallucination is he's hallucinating. I know he's hallucinations because I saw him take the mushrooms.

I come to you and tell you for a fact. The Minnesota Twins are the greatest baseball team ever, and they're going to win tonight. That's confabulation. I said it and believed it. Okay, but it might not be true. So it's different from a whole location, but it's the same.

And because ovulation can confuse Junior CIS admins, it can Infuse your your harness. All that kind of stuff. So the workflow harness is something that I've been very adamant about building out around my agent because I need the sandbox to be more than a Sandbox. Okay, it has to be bulletproof, and it has to be able to squash running them up.

Yeah, in a sandbox agent, mix um is entirely different to what it can do in production. It doesn't have the same color and tension Sh. You can release in the production.

[Speaker 4]
Yeah, that's a good one, uh. Coming to the accountability and traceability, I just want to ask one more thing like as we are logging everything, so we cannot control the images. What to ask my agent? So, how do we handle the PA data, uh, reduction? So if they may ask anything to the agent when you're logging everything.

So, how can we redact those PRI?

I'm not gonna take this one. So? That's

[Speaker 2]
going to be part of your your logging setup, um, masking that stuff. Now, of course, it's just going to be using prep. You know, how do I grab this stuff out? How do my casket and that's where it gets tricky, um? That there will be some stuff leak through.

Um, but like Jennifer said yesterday, better to leak it through on an internal. Um, ll, m. Instead of a public one, so if you're really concerned about that, uh, that that Pi you got to run it, uh, internal? Um, that's the only way it's not going to get out to the public.

Yeah, this is like where my plan is, is that? They'll be kubernetes. Deployment, uh, there'll be a psyllium underneath it, which uses evpf for Network policies. There'll be some ports sold. Asked to ride the Regal for the network policy is not it? Um, and you know, we'll just lock it down.

And that's where it runs, and it can only talk to what it needs to talk to, right? So, if the inference server is not running the inference server is running on the VM in the basement. That's one connection, right? If

[Speaker 1]
it,

[Speaker 2]
if it needs to read all the access to one database, right, then it gets read-only access to that one digit. And so those are the type of things where you have to. Already know how it's going to work, and you should probably know how it's going to work without Ai, and that's kind of what I've been meaning to is that, like, yeah, most of the stuff I'm writing.

I don't really need the AI. The AI is helping me with false positives. It's helping me with summaries. It's helping me with logs where it's like no human can go through this lines and lines and logs, so there's just some stuff that I've been working for. I think data should be redacted even before we send it to AI filter relaxed.

Yeah, I should not even have access to your pi data. Um, I mean, we can. We can let AI.

[Speaker 5]
To do a cost check like you can do in our schools like control panes to build markets around it, but it should not in it should not. Have you even have access to that data?

[Speaker 4]
As we should not send your data even the bi to the agent. So, what set of guidelines, uh, any Enterprise should take care of. Is it post Gallways or pre-gardways? I think that's where Oprah policies, uh, play a private role so you can write a radio, um. Local policy that creates a boundary on what data need to be Central agent.

[Speaker 5]
I guess

[Speaker 2]
I'll agree, well, I mean, you could use pyverno, but now you've got two problems you've got Rigo over here. You've got whatever 500 we did, no?

[Speaker 4]
Yeah, so last thing. I just want to say like what advice you want to do for any organization who want to build a platform for to build AI agents. So, what's the first thing and the foremost thing everyone should focus on? I

[Speaker 5]
would say start slow. Um, it's not because everyone is moving to AI. Everyone is billing agents, then you should do one as well. It's about doing it, right? Um, start slow, build an agent that makes your day-to-day life easy. Um, and then first learn how to draw boundaries. That's a new, actually productionizing agent.

Without that, you're not no longer even taking an agent in your direction.

[Speaker 2]
Yeah, I second that, um, it's, uh, again. Like, I said earlier, I mean, literally, most of my stuff will work without the agent, and so I'm using AI at the boundaries right now, because. It's better at summarizing than some code I can write. It's good for interfacing with humans when you want to tell them a report or some summary in particular.

It's better at finding false positive and regex, um, you know, because if you add a regex, you know you've got two problems you've got Ai and a regex? And so there's things that you can use it for, but, but use it responsibly. Just because your management came down and said, hey, it's Steve.

I've got this AI Hammer. Can you go bang that screw in? Don't just just resist and and realize that there are use cases. And there are not use cases, and if you can solve a deterministically and get it right, 100% of the time. Why waste tokens? Right? Exactly. So, the two things I would say is start with least privilege.

Always got to start with police privilege. And learn what it's doing and not doing by looking at the logs and in the prompts and stuff like that. So least privilege is very important to start out that gate, uh. With that, now, on the the reason inside, yeah, if you ever try to to do math?

With the llm, it sucks. It,

[Speaker 7]
it does not. It's had to deterministic.

[Speaker 2]
Math, and it just doesn't. And, uh, literally, so you have to put AI in the right place. You have to figure out I need a reasoning problem to solve. There. There's three parts to to that. I break down, uh, A. One is the the inputs, you know, what are?

What are going to be my signals? From that, I need a reason on those signals, and then, when I want to act on those on what the reasoning is, I want to do that, uh, external to the online. I don't want that llm doing the acting. I want to have it reason and tell me what it should do.

And then you go off to like an mCP or another. Um, process could be just regular deterministic workflow or something, and that that then has the hard boundaries. What can, what can it do? Right. So, like, let me go back to the agent harness where you built these tools, that which are similar to what mCP does so.

MCP gives you the way to take external tools and present them to your agent, but your agent should have purpose-built rules and the purpose-built tools. How things like you're not allowed to run rm-rf slash asterisk unless you're database indeed, um? And then the model. You tell the model that you're a masterful AI developer, whose name is sorry, look this.

I'm going to do this. Don't let me hear yourself, um, anyway. So the, uh, that's kind of what we're talking about there, though. Is that, like, you've got Purpose Driven tools, so you got to do math. Write a tool to do the math. Timestamps are my favorite cut off date for your model was January 1, 2026.

Why are all these pit timestamps in January 1, 2026? It's April. You got it right at times down tool. These are just things you're going to run into that will get you.

[Speaker 4]
Yeah, I agree with that. So, most of the arguments these days are involving agents where they are not actually needed. So, what's your best solution that what use cases area is like if the max needed we need to specify to write a tools for that not asking an llm to do this.

Data engineering pipeline or wasteland, necessarily the tokens and all. So, yeah, with that, uh, I'll conclude this thing, I think, uh. Thanks for, uh, all your valuable suggestions and the tips. What? Ever, you have given? So, um?

[Speaker 2]
I'm sorry, I lost my train a lot.

[Speaker 5]
I hope you've run out of time.

[Speaker 2]
Okay, so if anybody has any questions, um, we'll be wandering around, um. We're going to be here in this room pretty much all day in and out for lunch. So, stop by, grab us. Um. Anything else? That's it. Thank you very much.

[Speaker 1]
Okay, sure.

[Speaker 7]
All trying.

[Speaker 8]
What would you say would be the smallest, easiest to like, come to people to justify? You know what I mean to bridge the two gaps. We'd love to have something in-house. Oh yeah, but that's ten thousand twenty thousand dollars.

[Speaker 9]
So, that's one of the interesting things because they've added not only tickets.

[Speaker 3]
Get away with a smaller ball, right? And so, like, what I've done is, you want to get away with the smallest model you can get away with. It still gets riding,

[Speaker 8]
right? I'm with you.

[Speaker 3]
So, if you wanted to go like the stuff you've got at home! Great! Oops, sorry. That's

[Speaker 1]
not gonna

[Speaker 3]
help when you get users, right? It's okay, when it's your, um, check. Imagine if your work and you've got a hundred people that want to hit this. And then it works out, right? You gotta get so like a minimum, right? You want a VM with? Like, you know, big processors, 64 rounds of RAM, and at least one a100.

What do you think sure? And then you go with Cuda, right, yeah, and then you pay late. Currently, we're getting the most success out of blm

[Speaker 8]
as the service

[Speaker 3]
now, but with that,

[Speaker 8]
you can only serve up one

[Speaker 3]
multi, so you have to know which model you're going to serve up. And that's the work, right? Uh, with llama CPP?

[Speaker 2]
It's the same way you get the best performance when you pick a model and you serve it up,

[Speaker 1]
right? But you can pick which four you can serve it up on. So, if you've got enough, uh, vram, right, you can limit like one to like three quarters of the B round, I know, and you can fire up another one on a different boat with a different model right?

And now you've got, you've got two places you can hit you. Have you know two different top models all the different types of results out there. And if you've got enough, you go to three experimental router feature. He does this in the background. Yeah, um. And when I say it's experimental, you get to keep all the pieces when you break this.

Um, it's Cutting Edge, and you get to believe this is how bad it is. I've been trying to get to it works great with the IBM brand and models. I've been here very, very purposeful business type models. They have business type thinking things like, like, a business person, so they're good for what I'm using it for, but I wanted to get Gamma 44.

Yeah, so that I could have something he was thinking and doing something creative, and that has gone really boredly. Every time I have tried it, and I am literally on head of llama CPP, and every day I pull whatever they pushed last night, and I build it and try to run it to get camera, right?

What?

[Speaker 10]
What inference are you using CPP? That's the repo that you're the CTV

[Speaker 1]
is the inference engine? Got it, got it, got it. And I literally have it. And I build it every morning to see if I get it. Yeah, because it's like. Yeah, yeah, yeah. And then there's another one that is, uh, split off of that, um, called, i, t, i, k, llama, CBP.

Now, if you have three children that don't have n v left, right? So, I've got three l40s this in my box. And while that's cute, I got three gpus. They are not mechanically connected, like your 390. So, yep, and they're not the no envy. So, it has to be done in software.

So, i? T, uh. To see has a method of using a graph to spread the model across the threes. The three

[Speaker 10]
really, yeah, and

[Speaker 1]
so llama CB can only do row or layer okay, and then ik has gone. Hey Rick, should we grab okay and put it across all and you get a lot better performance out of it. You're not

[Speaker 10]
restrained by the pcie lanes and them talking to one another. You are

[Speaker 1]
New York okay, because you're not going to get better then. Okay, and it's not like he's got three a100.00.

[Speaker 10]
Okay, yeah. But the price tag, whoa. And tricking the senior

[Speaker 1]
associate to put them under your outside of the process of requesting the part. Yeah, um, and so that's what you're up against. It's like, but you, you're looking at, like, like a, an l40, or an a100, you're looking at five grand, and then you need whatever hypervisor type stuff you do.

I'm, like, we're using, uh, because? And what they've done to VMware. Yeah, but um, if you heat

[Speaker 10]
your hands on, yeah, that's the hypervisor open status. That's where we're running the VMS open stop.

[Speaker 1]
Steph. Yeah, now you want something that's going to go haywire on you and cost you a 14 day Chef. We'll do that for you okay, but it's distributed file system. Um, and you need a team to manage the open stock in the cell because you can do that yourself.

You're not gonna have time to work on the AI, cuz you're going to be babysitting that thing all the time. So, Mama CPP, OpenStack e f f now I?

[Speaker 7]
Write rust.

[Speaker 1]
So anyway, the the thing, though, is, is that, um, oh, the BLM is written in Python, but there's oh, developing costs. And so, it seems to stay up to date really, really well, and what Llama CPP is trying to do is be. Like, a production grade super fast inference server in C plus, right?

Like, if you get? If you take an older model, it works fine, but the new model drops and llama CP takes a while to get it working. I did Gina 4 when it dropped in. Yeah, but but BLM, they're like, oh, we already had that. Yeah,

[Speaker 10]
and we already tested

[Speaker 1]
on it. And oh, here it is, they dropped the model. They dropped the fix, you know, and you work right, right? Like, if you're not gonna do stupid jobs like, I'm going to try and do where I'm going to take and fine tune small miles into piles, and I need to be able to serve them up on the same machine.

And you don't need the routers.

[Speaker 10]
I got you, I got you. If

[Speaker 1]
you don't need the water pump, use the route. I hear you because what llama does? It's got an API on top and it's got open AI API and then in the background it spawns off the command line for itself, so it's like double pork, uh, it's a pork itself, and then it uses the model.

If you've got model presets, it uses those presets based on the module, and it runs. And, like, I was telling you like that version, one you're cool. I got plenty of vram. I got plenty of space, and then that second one, the other one hasn't shut down yet. You're like, boom.

[Speaker 9]
Yeah, and then you get

[Speaker 1]
in the slots where you're like, okay, I'm gonna solve this a different way. I'm going to have three instances of this brand model, and I'm going to give them, you know, it's got a 500 something Mega K, uh, context window, and you fired up with three slots. And then you realized that it did the math.

Then you got 128, 120, 128, and then you blow the complex window out on all three of them. Yeah. Have you noticed a performance difference between the?

[Speaker 10]
Really can't?

[Speaker 1]
Can't tell the difference. But now, in router mode, while mine's got to load those tensors and spread them out, and so

[Speaker 10]
it takes longer that the first, the first one is, got it like everybody was

[Speaker 1]
just being so slow. Give it a second and hit it again, and then they hit it the second time. Now, llama P comes with its own UI for a child, so once you fire it up if you build it within the UI, you can have a nice UI for Chad and you can control the model one.

Flip it in and out with different models. Cool, sure.

[Speaker 9]
Kind of on the same subject, which is General Vibe. As far as smaller models, because Gemma four dropped and was like, I can just run this on my laptop, and it's

[Speaker 3]
pretty good for that. So I got I got Yama 4 e4b running in a llama on. A 24 gig M4 MacBook Pro.

[Speaker 1]
Um, and as long as I'm not doing something stupid, like having, you know, lots of stuff open? Yeah,

[Speaker 2]
I got

[Speaker 1]
it to write python.

[Speaker 9]
Yeah, yeah,

[Speaker 1]
literally. Write a python program that worked fantastic. My

[Speaker 9]
yeah, and I'm asking more because I've done that with, like, even 26b8, because I've one of the higher, um, enforce Network. And what do you think? Do you think Enterprise will move more towards that kind of thing where people just have it on their laptop. Or do you think that's just

[Speaker 1]
so type dream? So I don't know what the rest of the world's doing because this, I. Was expecting this conference to come in and be like, damn it, behind eight ball again. And I'm not, and so that means the Enterprise is in the same shock I was in last year, where I didn't know what we're going to do.

But last year, I got up on stage, and I said. I think in production small models fine-tuned to the job they're supposed to do to how we're going to solve this right and using a giant llm Frontier model to search jira, it's like using the Mack truck. Because it's your f****** mail, right?

Not only that, there's a SQL query you can run in an API with a curl College that will do and find the tickets you lost without AI. Okay, and then I proceeded to write a blog post where, like, uh, in 2015, I can tell you all the capital letters and the string, you know, one line of?

And now I have to contact anthropic right approach and then send it the text. Tell me all the

[Speaker 3]
and there's

[Speaker 1]
two letters in strawberry,

[Speaker 8]
yeah, yeah,

[Speaker 10]
right, yeah, yeah, so,

[Speaker 8]
yeah,

[Speaker 1]
so the the, that's what I was trying to get out up there, is that you need to think about what your job uses for, right? Like the thing that, like, I didn't have anything, any reason to put it in production, except for two things, uh, going through, uh, crash logs, where we had deployment where?

Island test, and something blew the hell up, and the logs were too big for humans. Yeah, and then the other one I have is my lawyer. We have an open source onboarding process where you have to say, hey, I want to use this open source library, and it goes to SME.

That's right, you got a technical review. You got a security review. You got legal review, and then you've got a, uh, export restriction company. Okay, I got three lawyers and one open source guy. Okay, we're backed up 8, 000 libraries. Each of those 8, 000 operators are five jira tickets.

That's cool now! This is a good use for AR, yeah,

[Speaker 7]
because I'm gonna go blast through all those 8 000 tickets with AI, and I'm only going to leave the ones open if the humans need to work at. Yeah, if I go and look at a repo and go. No, this repo's fine, right, with much static analysis. And then I box it to the AI and go.

Hey. Tell me if you got false positives, and then if you see something suspicious, follow the trail into the other files. Use your tools to go find the files briefly, and he come back to me with confidence. Score on this thing, and if the confidence scores one we know it's bad.

If it's 100, we know it's good, and if it's 50, we leave the jira issue.

[Speaker 1]
It's human years. Yeah, so that's you can use. That's small model. For that, is that what you're saying? Oh yeah, I'm using. I'm using. I'm using granite for actually.

[Speaker 4]
Or whatever.

[Speaker 1]
Whatever, right? There's so many of them that my head spirits, right? And then you go, and like a lot of the guys are doing a, uh, been fine-tuning quantized models, and they're using Q Lore to do it. Yeah, and so you, you fine-tune a base model with the answers it needs, and then it gets even more

[Speaker 10]
reliable. But what fine-tuning, uh, repo? Would you point me towards? No, no, no, no, no, no. You wanted to work? You can curate that data. Okay, fair. You are now a data scientist.

[Speaker 1]
Use, use the packages and understand how they work. Like, create my own. I never like data science was never on my list of things I hate sure, and now it is understood, because I'm not a data scientist, but you need to be able to write the prompt and give it the answer and tell it.

This is what you wanted to see, right? And you do that in Jsonelle until you've got 8 000 and of these entries, right, right? And then, at least. And then there's a point where the training data is is too much and not focused enough, but still and curious to test.

Yeah, and then the one thing I always tell you is that synthetic data leaves the bias, and so if you think you're going to go and tell Claude to generate your training.

[Speaker 10]
Yeah,

[Speaker 1]
no. Send me an email. Tell me how it went. Yeah, I'll tell you, I told you so, so I can tell you, I told you something, yeah, exactly, and IBM's

[Speaker 9]
getting good results, not just getting like making sure that the date whatever data you have is the highest quality data. So,

[Speaker 10]
you have

[Speaker 1]
to make sure that it's super super clean, right, garbage, and garbage out.

[Speaker 10]
Exactly like,

[Speaker 9]
yeah, they

[Speaker 1]
just did it announcement, they said. Here's an older model that we we retrain.

[Speaker 9]
It's got fewer parameters, but it's outperforming the higher parameter model

[Speaker 1]
just because we spend more time,

[Speaker 8]
right? Yeah,

[Speaker 9]
uh.

[Speaker 8]
I'm Daniel, I'm

[Speaker 10]
I'm Paul. Hi, Daniel. Yeah, yeah, you took the picture, right? Yeah, let's learn more about MCP. Nice to read.

[Speaker 3]
Walk to this guy, I guess.