---
type: transcript
topic: work
---


Cbcon. We're looking at the AI segment of cdcon right now, and the lightsaber keynote speaker here. I'm thrilled to introduce Jennifer mulford. She's fearful October.

[Speaker 1]
All right, that says something. When a security company comes to talk about continuous delivery, doesn't it? What a delete. And I'm pleased to note that Jennifer is also a former Harley Ryan, so there's some interesting and fun here. We're gonna let her get herself ready, and then we'll get it started.

And we got more more seeds here there. At least three or four through if you'd like to not solve zero.

[Speaker 2]
Um, so it was kind of something wrong with what you're saying, like.

I'm in the I'm in the programming world. I don't know much about cyber and all that stuff so, but my company cares about that because we do some, like, dod stuff.

[Speaker 3]
A lot. There's a lot of like doom and Gloom right now. About, like AI, being able to find vulnerabilities and use them? Would you say a lot of that is from not AI being specially creative? It's just faster at finding things that we should have done in the first place.

Okay, that's

[Speaker 2]
the key right there.

[Speaker 3]
Okay, that makes sense.

[Speaker 2]
It's exploiting. Yeah, what we've done poorly before, so it's essentially like, you were kind of saying we should just put more weight into the security. It's not like we're doing anything new, just more of it.

Is that kind of just?

[Speaker 4]
You know, I think it would almost be a faster to create a new code that's that has, like, not static credentials, and things like that.

[Speaker 3]
Okay, I

[Speaker 2]
think it would

[Speaker 4]
actually be. I'm really for getting rid of my garbage code. I mean, almost starting on

[Speaker 3]
it. Quite frankly, I'm probably sounds crazy. Well, that makes sense. Yeah, yeah, I mean, I see a lot of f****** fixing it. Sometimes, it's just.

[Speaker 2]
Unless you can get it to treat that as a second Monitor and put your notes on one Monitor and the other on the other monitor.

There we go.

Hi, everybody. Um, this is my first time speaking here. So very good.

All right,

[Speaker 5]
AIS, being out of the cicd pipelines everywhere right now. But many teams haven't figured out where it shouldn't go. AI is powerful. But are your environments ready for it? Are you putting it in places where you can't afford to make mistakes? My name is Jennifer molker. I work at platform security at Octa, where my job is making sure the systems that we build and the tools that we introduce don't quietly undermine the security and reliability that our customers depend on.

And what I found is that AI is incredibly useful in our pipeline, but we have to be very intentional about where it lives and how it's configured.

So, we're gonna think of AI as our new team member and I really liked the puppy. The training the puppies was good for me. I'm using the construction worker.

[Speaker 4]
Uh, new team members very capable, but he's also very new. Who doesn't quite understand what sacred yet? And doesn't really have that experience knowledge, you know, understand how to handle situations that you only understand what the hands-on experience?

[Speaker 2]
We've all heard the hype, right?

[Speaker 4]
AI is Magic. AI is the answer to everything. Resistance is useless, and if you're not already using AI everywhere, then you're behind. The implied conclusion is to throw AI into your pipeline and just let it figure it out. This is exactly the framing that I want to push back on today.

Speed is not a substitute for judgment. It was very hard to say that when you ask that question earlier. Um, cicd is one of the worst places to move fast and brighten things. So, what actually goes wrong when you skip that judgment step? Ai is, in many ways, a yes machine.

Whatever you ask it to do, even if what you're asking is wrong, it's going to execute it completely and confidently. It doesn't push back the way a senior engineer might, and there's a second problem that gets underappreciated. Does your AI agent even know who it should specifically be taking its?

Because if it's reading PR comments, commit messages, or log output content that can be written by anyone, then you have a serious vulnerability on your hands. Ai as a team member is extremely bright and useful. It can often be quite green, though. I think many of you probably know how I feel when I talk about this, but sometimes I feel like I'm trying to build and lemonade stand, and the AI agent is offering me instructions on how to make a sandwich.

So? In a production pipeline, a confident, wrong answer doesn't just waste time. It can cause real harm. When we talk about AI in our pipelines, we should talk about it from the perspective of someone who owns the consequences. That person is you, the the platform engineer, the lead who approves the integration, the security engineer who

[Speaker 6]
configured all of the controls.

[Speaker 4]
You're the one on the hook when something goes wrong. AI needs proper training and fear boundaries because the cost of a mistake in a CI CD pipeline isn't just a bad draft email, it's a compromise bow, it's vulnerabilities, it's deployments, breaking and waking your team up at two in the morning.

The answer is not to avoid AI. It's to scope it and configure it and build trust deliberately. I want to share something from a Forbes article that I read by Bob Naseem, who wrote about exactly this challenge. She identifies four steps to closing what she calls the AI trust Gap.

And one of those four steps is to equip your teams with the right tools from the outset, not as a bolt-on after systems are live. We need to ensure that AI knows how to handle everything that could be thrown at it. We need to monitor its actions,

[Speaker 2]
require approvals.

[Speaker 4]
Guard our elevated privileges and manage our new team member. I'm about to do that. And manage our new team member with the same guardrails that we would any other newbie. Before we get into patterns and guardrails, I want to make sure we're grounded on an important thing. AI thinks very differently from humans.

Humans have reason, life experience, judgment, imagination, whereas AI has patterns, predictions, prompts, and output, and can confidently produce incorrect answers. What I have up right now is some differences in how humans and AI think. It's important to consider these differences and keep them in mind when you're configuring controls and teaching your AI agents.

This is the tension at the center of this whole talk, AI optimizes for generating useful output quickly. Your

[Speaker 3]
pipeline optimizes for a reproducibility and safety. These aren't incompatible, but you have to be very intentional about how they coexist. The mental model that resolves this tension is the copilot model, and that's where we're growing this. Ai's job is to make you faster and better informed not to make decisions.

Autopilot exists on planes because of Decades of testing, redundancy, and Regulatory oversight. And still, they keep a human pilot on board in case something goes wrong.

So we don't start with autonomy. We start with Pope pilot.

This is the lowest risk, highest value entry point that I've seen. The AI reads the diff summarizes what changed, what it might affect, and flags anything that looks unusual with within seconds. The reviewer still reads the code, but now they have contents before they start. If the summary's wrong, the review process will catch it.

Nothing bad happens. In addition, you can have test suggestions and or have the AI perform some tests as well. If you have a secure enough setup to do so. There are tools out there to help you with set up this secure environment and detect abuse as well. Without making any specific mention, I have some sources at the end of my.

[Speaker 2]
Presentation. The rubber ducky pattern. Named by me. But

[Speaker 3]
this is where the first day I generates code or a summary. The second AI reviews that output and questions it looking for gaps, edge cases, logical errors, the result surfaces to a human reviewer who makes the final call, the AI never pushes code. It never merges. It generates a suggestion that a human reviews and decides whether to include.

[Speaker 7]
The Dual AI review adds a layer of automated skepticism that catches what the primary model misses while keeping humans firmly in the decision seat still. This is one I've been using for a long time, even before we were using AI on my job. I use it in my personal life.

I, if I ask a question, I don't trust chat gbt to give me the answer to everything I asked. Chad GBT, I asked Gronk. I asked, even Claude can answer some questions.

Engineer.

Reviews the suggestion and decides if the change should be made. The pattern AI reads, AI explains. Human decides and applies the time savings are real, and the pattern is especially useful for on-call situations where getting to the root cause quickly is everything. Alert fatigue. It's a genuine crisis. Teams stop paying attention to findings because they're too many.

They're often duplicated across tickets, and most turn out to be noise for their specific use case. Ai can help dramatically by reducing false positives and duplicates and adding context. But the humans still decides what to act on. Ai doesn't close the tickets. It helps you understand them faster. These are tools mentioned in the source articles and that there are tools mentioned in the source articles that can help you with this as well.

Now, let's look at what all four of these patterns have in common. Every one of them shares these properties read only access to pipeline content. The output Services as information, not action human gate before anything changes. This is also your checklist when you're evaluating any proposed AI integration. If those properties aren't present, then you need to ask questions before proceeding.

I want to shift gears now and talk about what happens when your pipeline itself becomes the target. Because Azure pipelines get more capable, more automated, and more trusted, they also become more valuable to attackers. Let's talk about why the stakes are so high with a real example. In late March 2026, Axis, one of the most widely dependent upon npm packages in the in the entire ecosystem with approximately 100 million weekly downloads was compromised.

The attacker compromised a maintainer account and published backdoor versions that delivered across platform remote access Trojan to Mac OS, Windows, and Linux systems. Not by breaking into a server, not by a sophisticated zero day. All it took was an npm install. If your cicd ran npm install and you were on a version range that included the malicious release.

You were compromised automatically without a human decision. This is the world our pipelines live in now. So, here's how it works. The attacker gains control of the MPM account belonging to one of the Project's primary maintainers and published two backdoor versions within a 39-minute window. Rather than injecting malicious code directly into axios, which would have

[Speaker 2]
been more visible in a dip.

[Speaker 7]
They added a single Phantom dependency. That package declared a post install hook, which was, which is code that executes automatically the moment you run npm install. You can see more about this in the source articles that I've included, but you get the general idea. This attack chain compromised install execute exfiltration completed itself without anyone clicking anything malicious.

The pipeline did the work for the attacker. Now, here's the part that directly connects with everything that we've been talking about today. This attack was caught by a security researcher who built a proof of concept monitoring tool of using AI to read package diffs in real time. He ran it from his laptop.

The AI flagged the malicious dependency within hours of publication. And they were able to catch it. AI used carefully deliberately in a read-only analysis. Only pattern is also how we detect attacks like this. That's the balance we're trying to strike. So, we've established now that the pipelines are the target not could become a Target someday right now.

Actively pipelines are being attacked. Cicd systems sit at an extraordinary intersection of access. They can read your source code, your secrets, your credentials, and in many cases, they have the ability to push to production. From an attacker's perspective, compromising a pipeline is better than compromising an endpoint. You get everything automatically every time a build runs.

Cicd environments are high value targets. Ai that creates logs, dip dips, and commit messages. Is a new attack service. We're adding a new surface area that didn't exist before an AI integration that reads content author authorized by anyone in the ecosystem is an AI integration that an attacker can influence.

Prompt injection is the SQL injection of the AI erum. If your AI integration rates content from PRS issues or commit messages, commit messages that content can be written by anyone you have a prompt ejection service. An attacker opens a PR where hidden instruction in a comment the AR read it, and that's what it says.

This is why AI output has never been directly responded, always validate, always gain. Before you integrate any AI tooling, ask what exactly is being sent in the prompt? If the answer is the full diff or the CI logs, you need to audit what's in those environment variables and those and where those logs are sent verbatim to an external.

Oh, I'm sorry. There have been cases where logs contained an exposed environmental variables, and those logs were sent verbatim to an external API. You need to manage this risk with self-hosted models or carefully scope prompts that strip sensitive content. This is a mindset shift that's easy to State and hard to internalize.

We're used to trusting our tools if the linter says it's fine. It's probably fine. AI is different. It's confidently fluently wrong, sometimes. Your pipeline can't tell the difference between a good AI suggestion and a plausible sounding bad one. Treat it like, you treat a PR from someone you have never worked with before.

Review it, build a culture, and a process that expects verification, not blind trust.

There's no Universal, right? Answer here, but it's a decision that deserts to be made deliberately rather than by default? Third-Party apis are easier to get started with, but if your data lives in your environment. Self-Hosted, or were open source models give you much more control at the cost of operational overhead.

The right answer depends on what's in your prompts and how you classify your data. If you're a startup without sensitive proprietary code, but third-party apis are a reasonable starting point. If you're in healthcare with strict data residency requirements, self-hosted is worth the investment. And with the added security of a managed identity provider, you can self-host your model and still rely on industry proven authentication, authorization, and security best practices.

Also included info on the on my source page. Now, let's move on to the guardrails. The level of severity may look a little different depending on what your company is doing. But the general concept is the same. Treat your agent like the new team member that they are with limited trust and limited blast radius.

Limited ability to break things.

Give your AI integration read access to repos, logs, and metadata. Do not give it right. Access merch permissions or deploy trigger, not at first start, read only and stay there until trust is established. Here's the thing, if your a can, if your AI can only read things, the worst case is, it reads something it shouldn't.

Which is bad, but recoverable if it can write, merge, or deploy. The blast radius is dramatically larger, start read, only earn the right to expand from there.

The human review step has to be explicit and traceable. A human looked at. This needs to be the first class artifact in your process, not an applied assumption. This is both the safety mechanism and an audit Trail when something goes wrong and eventually something. Will you want to know exactly what the AI suggested and exactly who approved it, and we don't want to lose sight of what's going in and out.

Make the review visible, make it required. Don't let it be optional.

This should feel very familiar. It's a standard security practice applied to a new type of integration, but I want to make it concrete and AI terms because there are some new wrinkles. In another Forbes article by Bob nasing, she says tomorrow's Enterprise won't just manage human users. It will manage a network of digital agents acting on their behalf.

And just as every employee needs a digital identity, every AI agent needs a non-human identity. So, every action is traceable and governed without a clear identity. For each AI agent, you can't manage access, enforce controls, or understand whose credentials are being used.

[Speaker 2]
Mr AI

[Speaker 7]
service account gets exactly the permissions it needs to do, its job, and nothing more. We must also think critically about agent to agent Communications and secure token vaults. The axias attacker gains everything they needed through one compromised npm account. You'll eventually have an incident where AI was involved. When you do, you'll want to know exactly what it was asked and what it said, build that logging now.

Stream every prompt. Every tool information, every file, access every API call in real time when those agents can execute shell commands, free API calls, refiles, and interact with in internal systems. You need real-time observab. To support that threat detection, incident response, and compliance, I call this like fight AI.

With AI, you need you need monetary tools that can keep up with what you're adding into your pipeline. Retain it long enough to investigate. Incidents include AI interactions in your post incident reviews, and this logging also helps you improve your improve over time. You can identify where the AI was wrong and.

Refine your prompts accordingly. Elastic samphosec team published a practical guide on exactly this and not included in my source page as well. When someone on your team proposes an AI integration and they will run it through this checklist, it's not about saying, no, it's about understanding what you're agreeing to.

Understand. Who has access and what security controls are in place? Ensure your platforms provide built-in observability and auditability. And require fine-grained authorization. So, each AI agent or user can access only the data and actions they're explicitly allowed to. All of these are foundational to building AI the right way.

A no on any item isn't. A blocker is a conversation. What would it take to get to a yes?

The construction worker analogy holds all the way through. On week one, they get a clipboard and a hard hat on week four. Maybe they're operating small equipment with supervision on month six with a track record. You have a conversation about the keys to the crane. It's the same with AI in your pipeline.

The goal isn't to keep it constrained forever is to securely expand its scope based on evidence and not enthusiasm. The supply chain monitoring tool that caught the axias attack is a great example of this progression. In practice, it started as a proof of concept on a laptop. Run and fully read only mode alerting to slap.

It proved its value then. It was open source, so others could build on it. That's the pattern, start scoped, measure outcomes, expand based on evidence, not enthusiasm. The goal isn't to keep AI constrained forever. The goal is to earn to trust. If you remember nothing else, remember these, the hype will keep coming.

Your job is to be the engineer in the room who asks the right questions not to block progress, but to make sure the progress is real, sustainable, and secure.

I've included several Source links on this slide. All are publicly available and worth reading. If you want to go deeper. A huge thank you to the open source Summit organizers, the Linux foundation, for creating a platform where we can share, learn, and move this community forward together.

[Speaker 2]
Any

[Speaker 7]
questions wasn't that awesome? Yeah!

[Speaker 2]
Any questions? Yes. You know that I can, I can just yell, um.

[Speaker 7]
And um?

[Speaker 4]
Um, it's still vulnerable. It's not a human. It doesn't like, learn, like an intern, does not to do dumb things.

[Speaker 7]
Yes, and no. Um AI is artificial artificial intelligence and machine learning and all that kind of goes hand in hand and and what I personally seen is. Um, let's use chat gbt as an example, and I'm going to do that because working in secure, you have to be very careful about what I talk about in my day-to-day work, so I'm going to use personal examples, but you know, use your imagination so?

My GBT agent. Although each session we have might be a new question or an from me in the new conversation? I've told it things as I'm going along, right? Like, I don't like it when you answer it this way or don't include.

[Speaker 5]
Political views. When you're responding to me or?

[Speaker 7]
Really need a drink of water? Sorry!

[Speaker 2]
I've been talking a lot. Okay, so.

[Speaker 7]
If you're setting up the secure identities and the guard rails with your AI, which you know as you're building it like from a corporation perspective. It should be okay, you're not allowed to do this. You're not allowed to do that. You know you're not allowed to take these actions without the the human saying yes, etc, etc with that Foundation.

Then, on top of that, if you're allowing it to remember your instructions where you're building out separate agents for different types of. Of actions, then you can configure that agent for what it is that you want. Like, you can build a claude agent that is specifically for doing this type of action.

And as you think of more, you know information that you want to build on that, then that's where the trust is built. But when you don't think of all those scenarios right, the first time you use it, you don't think, well, if I tell it to do this, it might act this way you don't think above.

First, you don't. You want to give it read-only, access it first, but? The trust is both ways, right? Once you start to understand how it's reacting to your prompts as well, then you can say, okay, I know that I can. I can let it take this action, right? Um, I can let it correct this typo or or something like that, but?

Um, yeah. So, so basically, you're building it to

[Speaker 8]
retain that information. It's not

[Speaker 7]
the same as, um, you know, just like random AI tool on the internet. This is, you know, your in-house, you're you're arming it. Ai agent does that make sense? Did I answer your question? Did I understand the question properly and answer it properly? Yeah, okay.

[Speaker 2]
Okay, my question is very similar. Um, so you talked about moving ahead based on evidence and not enthusiasm. What sorts of evidence are there metrics we should be looking at? Um, but how do we qualify that? Yeah, definitely. Um, I think it's just like, it's just like anything else right.

Like, when we first started, um? When we all first started adopting the cloud?

[Speaker 7]
We, it took time for us to build that trust, and that evidence that it was going to be a reliable environment so. That the evidence is the same as like a POC or a deaf environment, you know, which I would highly recommend, you know, start using it first in your in your Dev environment and and monitor how?

How does it react to this? How? How is it reacting to that. What do we? What guardrails should we add that we didn't think of from the beginning before you go using it in something that can touch production, which I would be nervous to do ever. But, you know, I know we'll eventually get there, right?

What?

What guard rails to happen? Did

[Speaker 3]
everybody hear his question? Okay, yeah, it's a small room. That's good, right? Yeah, I absolutely. A lot of that is training your own employees. And honestly, yesterday, I started thinking and kicking myself that I didn't add about training your team in here, um. At OCTA, they have. We've we've all had to get certifications, and we've all had to learn how we're going to prompt A.

And to secure ways of saying things. And what can we tell it? What can we not tell it the? Yeah, that's definitely very important, I.

[Speaker 5]
You mentioned not being too chatty with it about your architectures. Yeah,

[Speaker 8]
where I work, we've got certain things like. This is built on an Amazon VM, the whole everybody there can know it. We don't care. This VM is on this IP address. Only a more limited set of people get to know that, so we've got kind of private architecture and public architecture.

Do you feel like maybe that same ballpark of what you'd let everybody know versus what you would keep to a small team might be about the border of what you would tell to an AI, or do you have a ballpark for what you consider architecture as sensitive versus architecture as whatever?

[Speaker 3]
I will say that first before I say anything else did. That also highly depends on whether or not this is your own in in-house agent being ran on, you know, on your own equipment and everything you know if you're, if you're in that situation, then you can tell it whatever you want, right?

Because it's not sending it out to an API somewhere. So, so that first of all is a big thing, um? I would say that, um. You know, giving, giving access. Like, if you're not using something in-house, you don't want access to to conflones and to this, and to that, and where it can put this big picture together.

But if you're, if your agents are completely separate, right? So, like, we've, you know, if we've got this, set up where? Um, for any given team they can, they can build out their own clawed agent, and you've got this team that only works on this piece of the architecture, then it's not going to matter, right?

Because it's not the whole picture going into into one thing, or I shouldn't say, it's not going to matter, but it's not going to matter as

[Speaker 2]
much,

[Speaker 3]
because it's not your entire. Ecosystem being fed into a one agent that is reaching out to an external API, so it's kind of, um. Maybe just using your own judgment, but always always err on the side of how much does this need to know and least privilege and least information as well.

Thank you! Let's do one of my question we have, uh, gentleman, yeah. Which one, one behind? Okay. So, let's go.

[Speaker 9]
Like this thing. So, how, how, and right now? Yeah, I find my goodness. I can understand, but maybe a couple years from now, maybe it may be better that. So after it, they can anymore.

[Speaker 3]
I really think of AI as a junior engineer right now. So, so it's almost like one in the same. Um, there's definitely. Um. It's definitely more dangerous to give over permissions to an AI than it is to a junior engineer. Because a human has that reasoning and that? Um, that epic reasoning like, oh, if I do this dumb thing, I'm gonna lose my job, right?

So, so you're definitely or go to jail. If I do this bad thing, um, so you, you definitely would secure, you know, or you would, uh, give what, maybe more permission to a junior engineer and in, if if you're questioning it all whether or not to have the junior engineer overseeing the AI.

I would say, yeah, don't do that. Not a good idea. But. That's, that's a lot of responsibility. And a very powerful tool to, you know, to be given to them. But again, it's all about earning that trust. And if you reach a point where you, you know, you're, like, oh, okay, well, I know.

I know, this machine's gonna do this, uh, I think the auto pilot example is a really good one, right? We still have Pilots and co-pilots, even though there's autopilot on the plane and the pilot, it's going to be the one who makes those hard dec. And maybe the co-pilot.

Can, you know, can press the buttons. Or, you know, do some things and and train up like a junior engineer. Would you still want to oversee what's going on? Did that answer your question? Okay, we are bringing Jennifer back at four o'clock. She is on a panel, so we'll hop hide and she'll please to ask her questions during that panel.

We take a question from the audience, so please ask your questions and also at six o'clock or 5 30 down in the seasons area, which is down that kind of diagonal Corridor, uh, we're having a vacation, um, reception, uh, we'll have drinks. Find me for a ticket. Apparently, I'm gonna have a roll of ticket stand out for the drinks.

Please come, and will you be there. Yes, I will. You can ask your questions there, too. So I, I want to thank Jennifer for doing that amazing presentation.