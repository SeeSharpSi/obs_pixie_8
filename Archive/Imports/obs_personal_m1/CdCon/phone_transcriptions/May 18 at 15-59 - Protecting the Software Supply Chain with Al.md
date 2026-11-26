---
type: transcript
topic: work
---


The software supply chain and AI. Um, I have a really a distinguished panel here. Over here.

[Speaker 1]
He's a senior distinguished engineer at Capital One with a passion for empowering teens and driving Innovation, a firm believer influencing without Authority repair, has successfully balanced technical contributions with strategic leadership with over 15 years of experience in Cloud engineering. Devops and postdoc development is an instrumental in transforming vaping through technology.

[Speaker 2]
Jennifer Mulford. I don't think I have to introduce her again, but I will. She's a senior platform security engineer with a background in devops and a focus on cloud security and automation. She holds certificate certifications including cissp and CKA cka, and focuses on securing and automating modern pipelines, including the evolving role in Ai and software delivery and process automation.

She is an active member of the cyber security community and is passionate about.

[Speaker 1]
Ai, while staying grounded in strong security principles.

[Speaker 2]
Rio sugarhara is a technology leader and open source Advocate at NTT data

[Speaker 1]
with expertise in software delivery, devops Cloud native Technologies.

[Speaker 2]
And.

And English is not his first language, so we're going to give him some time. And we really are happy that he decided to sit up here on this panel. All right. So, this first question I'm going to direct him here?

So, we've seen, we've spent years securing human driven cicd pipelines. But what changes were the develop is making where the developer is making decision? Is an AI coding agent that can be manipulated through prompts, comments, documentation, or hallucinated dependencies, something that we learned about from Jennifer just before our break.

What new attack Services

[Speaker 3]
were? Where do the AI system development workflows?

Uh, I, I could think of.

[Speaker 4]
Four, four of them. I, I think like context, is one of them, which is what, I think, uh, Jake will cover it a bit, uh, problem rejection is, is, like, real thing agents when, uh, when, when kind of they start cooperating in this world, they? Instruction set is what is, uh, becoming an execution?

Uh, kind of inspection set for that meaning, uh, if you have a readme, and if the readme is poison, you basically have an attack surface over there, uh, if there's a comment. So, when comparing us humans to any eye, someone write something in the comment on a piece of code on a method saying, like, hey, don't touch this XY CDs and whatever the air is probably going to read the same thing, but it may act differently than a human will.

Fix it because it's always fine. Hey, thanks! So, context is one.

[Speaker 2]
The next one that everything of is tool usage, because now these agents are making their own decisions. They're trying to kind of run tools. Bash is the most common one with badge. They get access to

[Speaker 1]
Kerr, they call apis they.

[Speaker 2]
Um, I mean, you can write clients. They can modify things they can modify workflows, probably, which is scary. Uh, so again that that's another third Vector or kind of what I see. Third, one is permissions because. Well, as humans, you need human access control with AI agents. You basically are giving them access to whatever runtime environment they are in.

Uh, then there's an act. There's a possibility of privileged escalation, because, like, you know, we are not considering, like, with humans, we have an identity. The agents probably won't. Unless we provide that as the government where the agents are kind of having their own independent identities. And then we do the whole nine yards of security and commission management with them, and then the last one is, uh, context leakage, which.

To me, is like expert risk for sensitive data that's in the code base, and I think tensor again interest on this notification. A little bit where? And the idea piece of code, but then that piece of code if it has sensitive logic in it. There's a there's an opportunity for.

Rogue agent to kind of write that down somewhere or publish a blog or something, like if, and again, it goes back to the previous one, which is like how, how permissive the agent is in order for it to take action?

[Speaker 1]
So, we have to ask Jennifer to follow up on that because, you know, I think what I would be my side eye when he said

[Speaker 3]
that it wouldn't have its own identity. I'm like, is it? Yeah, an agent has to have an identity. How

[Speaker 1]
is that happening, and I think I've since, um, some startups, some companies talking about, uh, digital, a digital ID ID for an agent. How far away are that? And should we be waiting until that happens? It's, it's really hard to I, I.

[Speaker 2]
Decisions to be take myself out of my company, you know, not here to promote my company. So it's very hard to answer these questions, but I will say that if you do some research around auth xero and Ai and identity that you will find some good answers there that there's a lot of good work being done in that in that realm, um, there.

There are third-party tools to help you with. With building out your agents and giving them their own specific identity.

[Speaker 1]
So look Octo might be doing something. I, we should be watching.

[Speaker 2]
I'm I'm not at sales, right? I'm an engineer, but I do, you know, I do pay attention. So,

[Speaker 1]
and should we, should we wait! Should that be part of our um pipeline, uh, interagenic kind of workflow? Shouldn't we be waiting until that happens if you're, if you're not in a position

[Speaker 2]
where you yourself, can you know, um? Manage your. Manage your own agents in-house and have the security layers to make sure that you're giving them proper identities. Then, absolutely. I would say to keep, you know, keep on the app enough to do the research speed, who's offering that and and use a company that is experienced like OCTA auth0 in providing that identity security absolutely.

And no, don't, you know, definitely don't, um? Don't go into that realm where you're really giving your AI a lot of permissions. If you're not able to make sure it has its only spillage, because if it's just adopting, like, let's say, you know, you're the the CEO, and you're using AI.

If it's using your identity. I mean, it's allowed to do everything, so you don't want that.

[Speaker 1]
Rio, I know. Recently, you wrote an article we're going to talk about in a little bit, but do you have any comments on agents, and how secure they should be before we start using agentic in our cicd pipelines.

First, first question.

[Speaker 4]
Is so difficult, difficult problems.

We have a lot of projects started to agent degree AI, but most of the project.

But today always said it's an internal use. I don't think it's so sexual, so if. Someone.

The people who intended to taken the criminal, so the security he is same as nothing, not really dangerous situation. Easy to make, so?

[Speaker 2]
So anybody from the audience. Do you have any questions you'd like to ask the panel on this particular topic?

[Speaker 1]
Thank you! Um, so we talked a lot about controlling the access and making sure that these.

[Speaker 3]
Ai agents are able to do things that they're not supposed to. Like, you mentioned read-only access, is that something that would need to be configured on every endpoint device. We're talking about the OS or the app level, or is this something you could maybe control at the llm or the mcp tool.

Functions like, what's the best control point for this question? Okay,

[Speaker 1]
oh yeah.

[Speaker 2]
So, so I believe what he's asking is, if you're going to say, give it read only. Where you're going to put those where those controls are going to live, right? Yeah, so, um, so, he said, you know, should it be at the llm, or should it be at the as the tools that it might be possibly accessing.

And I'm saying both, which is why having its own identity is so important, because if your AI has its own identity, then you can, you know, block it from AWS. You can block it from, you know this tool, or that tool or say, you know, it can only execute this if, yeah.

People say it's okay, you know, so maybe everybody can use Claude. For example, everybody can use it, but only, uh. Senior engineer is allowed to. Give it that prompt that says, yeah, you can push this code, you know? So, yeah, they would be in all locations, just like your own identity, you know your company?

You've got SSO. You have your permissions that are listed on you, but also the tool itself, you know, there's going to be, uh, permissions on that as well.

Any other questions on this topic? It's kind of an important one, and I think we've got the right panel here to answer them.

[Speaker 3]
Yeah, I think it's good. I just had one thing towards, Jennifer said. I think, uh, because we are in this multi-agent ecosystem, each agent would have a different set of permissions. And it's, it's customary for you to not think of an agent who is implementing code may have access to writer code, but any agent that is just doing reviews.

It should not have access to write code. Uh, so think of it this way, like you're planning something, the plan isn't, doesn't need right access. The implementation needs right access, but doesn't need access to deploy. The deploy agent would need access to deploy, and all of these are governed through and a permission control plane or something that I think word telephone measure.

I think there's there's a question.

[Speaker 5]
Can you maybe describe the distinguished or distinguish distinguish between agents that are running on some kind of hosted infrastructure, whether that be in your company or? Through a third party versus you know me on my laptop with Claude and does the like, I workload Asian identity issue. Is it equal on both environments or as one environment?

It's maybe more important versus the other. Can you, um? Can you elaborate on that just a little bit, like, I mean so? So, for example, if I've got like Claude running locally? But when it's making calls to either mCP tools, third-party Services if it has access to my credentials and it, it can act as me when I maybe don't necessarily want it to be me versus on a hosted environment where?

[Speaker 3]
Maybe I do the

[Speaker 5]
bad thing, and I give it my personal access token. There's two things.

[Speaker 3]
Oh

[Speaker 5]
sorry, was

[Speaker 2]
everybody able to hear that question or the recording? Oh, the recorded one. Oh, okay, I understand. Okay, so, so the question is, if your um, if you're working on quad or your AI agent from your personal laptop and you're asking questions, and it's, uh, putting that information out, putting an API call to a third party location, um, how you're securing that, is it?

Yes, yeah, yeah. Joy to? Paraphrase or summarize a little bit there. Um, so there's there's a couple different answers

[Speaker 1]
to that question, and I, I covered a couple of these in my talk earlier, uh. One thing is, is that if you have data, that um is?

[Speaker 2]
Sensitive, then you. Don't you want to be hosting in-house hosting your agents? Um, because you don't want to be running that risk, right? But if you are like on your personal laptop and you're using Clyde or something then, um? It's, it's very important that you keep that mind that you are sending that to a third party and and that that it that information is not really secure.

You can limit things by having its own identity, so even if you're using a third-party agent, if your identity or Claude is is held in-house, then you can control what it's sending to that third party a API. Um, and you can use tools that flag, what type of information it is.

Like, uh, you know, we may have a tool that, um, I forget what they're called. I'm sure everybody here has used one, but where it, uh, stops your employees from sitting certain information out, right, because it the AI itself will recognize what that information is. So, if you're going to use third-party, definitely set up those controls properly.

Did I answer your question? Yeah, no,

[Speaker 5]
I think that helps. So, okay, continuing along that question here, um, you know? We used to think of platform engineering or building golden pass for developers.

[Speaker 1]
Now, these same platforms are being asked to govern AI agents models prompts. I asked about that earlier workflows and autonomous actions. How do we get started on doing that? I mean, it's to me, that's one of the most primary questions we should all be asking, it's not just how do we use AI to make our pipelines go faster, or are our jobs be more efficient?

But how do we start incorporating? Applications that use AI technology into the pipeline. And how do we start securing them? I will pass that question to Jennifer first. Sorry.

[Speaker 2]
Okay, so this uh, kind of Falls in line with the article that you sent me right, how did? Platform engineering role is kind of morphing, and some of us might have been worried about whether or not they were going to lose our jobs. But for this reason, we won't be.

Uh, because AI is starting to become that platform engineer role, but platform Engineers are starting to become the, uh, the monitors and controllers and Architects of that, where that AI lives and how that AI is distributed throughout the company and then. And that's a very important position to be in to to my to be the one making sure that all of those identities are set up correctly.

But all of those guard rail? Correctly and and to be the pilot basically, who's overseeing all of that autopilot work? And

[Speaker 1]
are you aware of any work that's being done around managing prompts or versioning prompts?

[Speaker 3]
Um, but how can you elaborate on that question? You know what we version code and brand code?

[Speaker 1]
Just prompts are just another version. Another yeah. It's still code, but we're not checking in prompts. You know

[Speaker 3]
there, there is some where, oh

[Speaker 4]
my God,

[Speaker 6]
because they have an AI agent. They have an AI piece to them where they talk to an L and we version the prompts because. Well, the first three prongs hallucinated all the time. Fourth, prom didn't. Everything is, everything is code treated. All the same Version Control, please, please.

[Speaker 3]
By 5 AI with AI, so our new, um, our new chair of the AI worker group, has just pointed out.

[Speaker 1]
Yeah, that does stupid version prompt, since uh might be something we should all be thinking about,

[Speaker 7]
but isn't a prompt injection attack that was described exactly a result of versioning a problem right completely. If I submit a pull request that versions the readme, that's the problem? Well, guess what? I just got them, and you execute my my mobile class. I just got controlled, but you forgot the hidden ASCII code that I did.

[Speaker 5]
Minutes, you pull a an AI review. Do you want to play this game?

[Speaker 4]
There are all my source.

[Speaker 3]
Page. If they're not on my source page, then let me know. I actually think that I, there are some tools being worked on in that in exactly that realm, too.

[Speaker 1]
And I'm going to ask Roxanne, who manages the CDF website to reach out to Jennifer and do a bit of a Blog on her talk and to publish her Resource page. So, look for that because I know that those were. There was a lot on there, and I wanted to see them like myself, so I'll get Roxanne to reach out to you to.

To put that together, I put my slides up, too. Maria, do you have any comments on? Do you have any comments on versioning prompts or?

[Speaker 2]
Yeah, actually, my company. You didn't happen to write to the, uh, PR

[Speaker 4]
and issues. It's just a trying way to protect, but uh, we happened to or found, and you go to solution or. The effective way to reduce? The very cost. So, yeah, but? I mentioned that my session.

Well on that, uh, Rio. You know, we have spent years, you know, protecting our source code repositories and our CD pipelines?

[Speaker 1]
Um, but on the topic of AI versus AI defending against AI accelerated threats. Um, you know? Can attackers extract, uh, you know, get sensitive data through all these prompts that we're going to be managing and our Defenders realistically keeping Pace with AI enabled attackers. Are we able to do that right now?

Well, basically, I could be it's my opinion.

[Speaker 2]
Different

[Speaker 4]
to, I guess, to everything, so? Oh, should also.

[Speaker 2]
This card exploit and expiry to release will accelerate, I believe so.

To analyze out of data so? Oh, you, you already discovered parameters such as chibi is could impact their own system. So, by analyzing by AI and notice the for the operators and operators can? Ai report, so that is a possible to keep peace support accelerated.

[Speaker 1]
I wonder if we're gonna have a new class of cve's, then that are specific to Ai, and what kind of what, what kinds of vulnerabilities will be listed as a cve? Like, right now, we think of cve. As you know something you found in a package for the most part, but will there be cves that are listed for llms?

[Speaker 4]
Great! So. And does that come from an AI bomb?

[Speaker 3]
Right, the next

[Speaker 1]
time you're right, literally. The next logical question is, if we are trying to keep up with attackers through AI, you know? I think that. Recently, there was Steve, you were mentioning on. A package cve at high risk. I think the it was attacked in six hours, something like that.

We were used to say that a CBE could be attacked in about 10 days, but AI is teaching us how to attack faster right and how to defend faster too, if we know it's out there. Yeah, if we know that we have an endpoint that's running up to the package, however too.

Yeah, that's how, yeah, so? Nist has started announcing what they believe should be part of AI bombs. Um. More than just the license. Um, so to this panel. Have you looked at the AI bombs? Do you think that they're useful? We've had many discussions about as farms are not accurate yet.

How far away are we from actually using an AI bomb to defend software from AI that's attacking?

[Speaker 2]
I, I can. I can share my cards. I mean out slightly different perspective. Uh, as bombs air bombs, they keep getting better. While that is the case. Defending is not always protecting and fixing. It could also be prioritizing if I really need to fix if there are other controls, other guard rails.

For example, if this is an internal app that's not exposed to the internet, the vulnerable? Cve, or the way the CV is written. The exploit is not exploitable in the

[Speaker 4]
realm

[Speaker 2]
of where it is sitting right now. Then you may not replace it. That's, that's. Like, you know, again, it's an offensive defense kind of thing because you are letting, uh. The guardrail of saying, like, hey, that is not reachable. And I think we're talking about it during the State of the Union, a town hall that you were doing earlier.

If something is not reachable, would you spend engineering cycles and tokens and effort trying to fix it right at that moment versus taking the time to know what other attack factors could potentially happen and then fix it. So, I think that's. That's just like, not necessarily saying, like, you should not fix it.

It's just at the point in time if there's a CVE, which is critical. And you know, that's an attack with? Like, oh, it's an internet reading API that we host. Yes, that becomes the priority, not something that's important. Risk acceptance is what your risk acceptance based on? The analysis of, like, you know, the, the possibility, or the probability of something getting compromised behind, like four layers, is still low as compared to something that's like on layer Z, yeah, okay, so I'm gonna just bring up one, uh?

But from that, um? If indeed you have a?

[Speaker 1]
Package that's running on an endpoint, so your threat landscape has a critical vulnerability out there. But you determine it's not reachable. Do you deep load it? If it's not reachable, why do you have it out there? Well, uh, it depends right. If there are, for example? And again, it's probably a bad example.

Like, if I have a package? Used for let's say Json parsing.

[Speaker 2]
By example, right? But that package is not directly integrated with an API. It's just doing some file parsing sitting somewhere, running a bad job doing its thing. Then, it's not necessarily directly imposed. So, in that case, yes. And again, I'm not saying that we should not remove that package.

I am saying, like, if I have 10 things to do? I'll do that number three on the list rather than number one, but I will get to that. It's just that, because the attack attack attackers are now being extremely. Powerful with AI, and we can exploit something in six hours, maybe minutes, right?

Who knows? Then, with that amount of things like the, the over alertness to responding to every vulnerability could cause other issues. See, meaning, like, you know, you can have any stability issues because you're trying to fix something where the fix itself is not available. You're just trying to patch it yourself.

Um, that?

[Speaker 3]
Did they have found an opening that they can expose something that was meant to be internal that you know that? That's a that there's a back door there, so it's important that we consider that when we say, oh, well, nobody can reach this. So, we're not going to fix it, but somebody being able to reach it when they're not supposed to might be the vulnerability, and that is where AI is extremely useful because AI can't review that that vulnerability.

And so, if you'll read it, trying to read a. Documents and think about what packages you have using AI to to read what the vulnerability is compared to what packages you have and what kind of access you are or what way you're accessing and say, okay, is this even relevant?

And so, I think that can be really helpful in that. Yeah,

[Speaker 2]
absolutely. And I think what you're kind of been leading to is the? Uh, scoring context, like,

[Speaker 1]
how do

[Speaker 2]
you score the risk based on these factors? Not, just like, hey, it's reachable or not, but all of these factors combined, then have a score, which then says, like, yeah, cvs S9 versus CBS at 7.5 in the context of the risk of that application, right? I just want to point out solarwinds was not reachable.

[Speaker 1]
Okay, so I think we only have a few minutes left. We'll go leave it to the audience for questions. I see Steve, thank you on most supply chain impacts are not reachable. So, the point wasn't, but many of the supply chain attacks are not much.

Yes, so we're talking about, like AI, defending against Ai among Ai and all these different parts. Um.

[Speaker 8]
My question is like if you're in a smaller AI has a cost right, and if you're in a smaller company, where would you prioritize

[Speaker 9]
applying and you could pick only one one place to start? So, the question is, if you're a smaller company resource constrained? Where is the best place to apply AI?

[Speaker 1]
I would say 100 in encoding, um, oh yes, absolutely. Secure coding, um? And I wouldn't just use one model. I, I think it makes a huge difference when you compare what Claude says versus what Chad GPT is saying. The difference?

Difference in what I can make that do within 30 minutes versus you know now. It would have taken me months right and broke an operational perspective. The cost of your employees time is gonna outweigh most things. Yeah, I guess

[Speaker 6]
my point is. On the flip side we're talking about, like the only way you can keep up with vulnerabilities, is to use AI. Yeah, so which?

[Speaker 1]
Yes, not necessarily, not necessarily you could there. There are, there's ways to to keep up with sort of critical and high risk at least, right? We're going to talk more tomorrow as security day. We're going to talk a lot about that. If you were talking about a huge company?

I definitely would say in security, but if you're a small company and you're not making a lot of outbound API calls and things like that, then you can monitor that without a bi late.

[Speaker 2]
Okay, I. I want to thank everybody on the panel for this. It's been great. Um.

[Speaker 1]
We have a lot more to talk about on this topic of security, so more on this tomorrow and platform engineering and some of the questions do relate to building this Golden Pass, and what do you got to put in it? So, thank you! Thank you to all of you!