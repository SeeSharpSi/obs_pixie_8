---
type: transcript
topic: work
---


All of that we talked about in the previous session 10 minutes ago to make sure we made that conversation going so.

[Speaker 1]
As promised, this session right is, what are these projects many of you have come into this room because you're, like, hey, there's so many of these different projects under openssf. So, what we're going to do now? Is, we are going to put, uh, the project maintainers in the hot seat, and they are going to give you their three minute pitch.

Their tldr think of this as rapid fire speed dating. And hey, does this work for you? Are you a

[Speaker 2]
match? Do you want to learn more cool thing about this? As the project maintainers go through, you know, their

[Speaker 1]
Spiel, please break down your notes, uh, we probably won't have time to get to everybody's questions about it, but here's the great thing. The hallway track is right outside, so um, we will make sure the maintainers unless you have a, you know? A talk next, but we'll make sure they stick around outside so you can ask those questions.

[Speaker 3]
Our talk is called security things, and it's a play on stranger things.

[Speaker 4]
But all we have is the opening, and these are the names of the people who will be presenting their projects to you. So we set up this cheesy intro for, uh, for fun. Oh yeah, there you go.

[Speaker 5]
There we go. Yeah, so those are all the people that are going to be presenting their projects to you.

[Speaker 3]
We're gonna have a little puzzle of this. That's okay.

I will be the person in the audience and I will pass it off. Let me know what's happening, so you want to start off.

[Speaker 6]
So we, we had an hour of basically open conversations between. Containers and us, and we have a great time. We surfaced a lot of really interesting conversations among us s-bomb accuracy, right? How do you use all of these tools together? Is there one one, um? Process to rule them all, or does it always just depend on who's asking?

[Speaker 4]
So we, we serviced a lot of things, but we want to take this opportunity to do a few things, right, what one we're going to bring up some maintainers to walk through their projects really quickly so they can give you a quick and dirty rundown about what their projects even are, where it fits in to your process, your pipelines.

Uh, and then we'll and maybe address some of the questions. Yeah, we're concerns that were from last session, right? Many, many of them were in the last session, so they heard you and they heard the people that were in in that session earlier. So, we're gonna, we're gonna get some some good, uh, information from them.

That's pretty much it. And we probably need to get started. We don't have very much time for this one. Um, so I, I don't know who might be ready first, but the first slide that I have? Is, get off, Patrick? Are you ready? Yeah, why not okay? So, go ahead and introduce yourself, and then you can.

Awesome! Okay. Hi, buddy. I'm Patrick. I'm one. Maintainers get tough.

[Speaker 3]
You all have probably seen the world get security at some level. For example, let's say Mulchers can make it to push the repository. There's been firewall vendor that had a commit that introduced that door right, and they didn't know how it got into their git repository. You've probably seen Branch protection on GitHub.

You've probably seen other things. Protective branches references that kind of thing. What we do with GitHub is we focus on your good security on your gear repository itself. So, for example, let's say, right now, you have to trust GitHub, yeah. Get lap, you have to trust a single point of view, right?

And you know, these products are good, but let's say, for example, it's a back door, or there's a malicious person that's an Insider something like that. What we do with GitHub is, if you know, git commit signatures. We have a talk on that on Tuesday. I mean that on Thursday, please go see it.

Did?

Some random commitment, its way through you can use, gets off

[Speaker 6]
or Central. You can verify

[Speaker 3]
it on your own.

[Speaker 6]
As a maintainer, I know our tool is still. It's an incubating stage. We're really trying to make it usable, but people I know there was a comment last time.

[Speaker 3]
On the last session about, you know, making it invisible, we're really trying to do work on that. Please come see our talk on Thursday and get together, I believe it's not room at the moment. We'll probably do some fun to get there to tell you about why you should use GitHub.

We are available in Homebrew, wingat on Glenn's package managers. If you have any questions, please come see me out floating around with the guy with the camera from NYU. Um, yeah. If you have any questions, please let me know. We would love to hear anything that you have. So, yeah, thank you.

Yeah, we can go ahead and take questions. Yeah,

[Speaker 7]
will the presentation be recorded on Twitter because I won't be here? Uh, yeah, right, wait, you got it! Great, great! Awesome! Thank you, everybody! Thank you.

You want to plug in or in demo, yeah? We're gonna try our demo. I haven't prepared at all.

[Speaker 5]
When I'm nervous so?

[Speaker 6]
Stephen, do you recognize me?

[Speaker 5]
Oh my God. Okay, yeah, we'll, we'll talk afterwards. Oh my God. Uh, thank you display.

[Speaker 2]
Okay, so. I'll, I will start through it.

Your time starts now three minutes, okay?

Right now.

Cool.

[Speaker 4]
So that is scorecard, um, really quickly. Uh, so scorecard is, uh, it started off as a tool. Or is is currently a tool that allows you to kind of view various security heuristics around your, uh, Repository, um, so you can see dangerous workflows whether or not you're doing really good things with um, with your GitHub action workflows or insert workflows here.

What vulnerabilities are on the project. So, I've run the scorecard report against scorecard's project itself. We're doing kind of okay, uh. Whether or not you've got like taking permissions and then and the the whether or not you're like using dependency update tools, uh, how well your project is maintained, so a lot of the different things that kind of take us through all of the different conversations we've been having in the previous sessions and conversations that you might be having about security in general for your projects.

We are working on the if you've heard of the osps Baseline that open source project security Baseline from the last talk. I mentioned that it is a. Uh, sorry, extended for anything. Um, so I mentioned that it is a. A framework, basically a control framework that that decomposes a bunch of different security, uh, security.

Regulatory concerns into things that are mappable and tractable for open source maintainers. So, my screen is playing with me. I won't be able to show you everything. What I will say is that if you're using scorecard today as anyone using scorecard today shut up fast. Ooh, I like these ants.

Okay, um, what I would say is don't use scorecard. Uh,

[Speaker 2]
if

[Speaker 4]
you've ever heard of All Star, uh, and you're on GitHub. I think this is very specifically for people who are on, uh, using GitHub as a court code Forge. Um, if you were, if you've never heard of All-Star All-Star is our um Alzheimer's, our GitHub app, um, and I've actually been working on some workflows and make it easier for you to basically use All-Star and use the, uh, this code and security, uh, scanning, uh, dashboard within GitHub to feed your scorecard results directly in.

Instead of running scorecard ad hoc one at a time across and repos, you can run this on the organizational level with, uh, with a GitHub workflow, and I can talk through that. If I can show you all the demo stuff, but no, it's okay, I think I'm almost out of time anyway.

We can talk about it afterwards. I would say you if you are on GitHub. Use All-Star instead. I've recently Rewritten all the instructions and have, and it has a grab and go copy and paste, uh, GitHub workflow that'll get you started. So, that is, I think it's a bit better in terms of like the end to end.

Want to have to deploy this one at a time. I want this on my entire org, and I want actionable insights for my maintainers. Thank you.

[Speaker 2]
All right, so welcome Banks, um.

[Speaker 8]
So, I think the the main problem that makes that tries to solve is what will serve is sturdier. Like, you have the very taste, but sometimes those vulnerabilities will not affect your code depending on how they're used. Um, and sometimes when you run a scan, you will find vulnerabilities.

Sometimes, they're yours. They're in your code. You have to own them with example. Most of the time, they'll never be surfacing in. Reacts will come from your dependencies and then.

[Speaker 9]
Uh, if this is something that it keeps regularly coming, uh, on when you do the scans, you can start texting them, and openvix is a format is one of the flavors of picks, which means vulnerability exploitability exchange. It was a project, uh, invented by the 17 managed the S1 working groups in CSA.

Um, and what it does is that it allows you to experience exploitability. So when you have a vulnerability in your product, you can issue effects. Um, to say to tell people that you're not affected by it. Uh, the working group handles the tooling to work with the format, doesn't really handle the generation of the information.

We handle the tool to the stake and the tool for the program. So here, it's something that you're interested in, based on not join us every early one day. Did you take a question?

[Speaker 8]
All right, and security vendors consuming backs so that they'll stop giving me false positive

[Speaker 2]
as well. It depends on the on the on the scanner that you use, so open vex is integrated in.

[Speaker 9]
Uh, Dr Scouts in great in Trinity, and I don't know, I mean, they don't record to us. Those are the ones that we've been in Spanish as well as other pencils. Also, thank you. Thank you.

[Speaker 2]
Exchange. Let's see.

Alrighty, uh, my name is James Blausberry. I'm a software engineer at Google where I work on.

[Speaker 3]
Um, the sex store product, uh. Today, we're going to be showing a real quick demo about this. So, um, a real quick, high level. What is Sig Store?

[Speaker 8]
Sixor is open source tooling to simplify signing and verification. One of the big parts of Sig Store is that we don't want developers to manage their own signing keys. What developers already have they have? Credentials they can authenticate with GitHub with Google with Microsoft.

[Speaker 5]
And as we've heard in some of the talks today, a

[Speaker 8]
number of CI providers also have support for identities so associated with workflows. So, what this ends up giving us is a really easy way to sign and verify content. Um, so what I'm going to show is a quick demo of using, uh, one of the core utilities of six store, uh, called cosine.

I'm gonna real quick talk through some of the metadata that gets generated, but as I was saying in the the last presentation, my goal here is, is all of this should really be invisible to you if possible, and that signing should just happen automatically? And ideally, verification is also happening automatically.

[Speaker 6]
Okay, um? So, uh, what are we gonna do? So, the first thing is? We are going to sign some file, so I just have here a. What biome? There's nothing there, but that's all right. Um, and then we're going to.

[Speaker 8]
Sign that file.

All right, so. Um, what's gonna happen when we do this, uh, a few things? Um, first, we're gonna cool.

All right. So what's happening on the other screen that you can't see right now is I'm authenticating with some open ID connect providers. So for me, I have a Google identity, so I'm just gonna get, uh, login Google.

Now, what's going to happen here is it's going to finish signing and then what we're going to get is a signature, but that signature is going to have a bunch of extra metadata. Now, again, my goal here is that you don't need to understand all of this metadata. Um, you really shouldn't have to think about all of this, but there are, I guess, maybe a few key things to quickly mention.

There is a certificate which I will show you real quick. So? I mentioned here identities. Here's my email. Here's who the identity provider is, um, what this means is, instead of managing some team you're managing and identity, uh, that gets associated with some signature. All the rest of the metadata here is other stuff.

Just make sure it verifies correctly. One of the other

[Speaker 4]
big things I even talked on

[Speaker 8]
this! Yesterday is the transparency component of this. That is what is here, called a, uh t log entry. It's this basically means that you're able to monitor when anybody is using your identity to those signs or something. I'm being told I must stop talking, so I will say one of the things that you also managed to.

You can also use this. Um, I will be around. Happy talking about this or other people.

[Speaker 5]
Um, yeah, salsa. So, apparently, South has one of the best branded projects that we have. It's a software-led software supply chain levels for software artifacts. Um, originally, the idea was, can we provide a way of improving your security step by step so that you start DC and then start making all of hard improvements later?

Um, as of now, salsa has been broken into different tracks. What we were mentioning earlier, so the most mature and the most established one, is salsaville, which establishes.

[Speaker 7]
That gives you another system that guarantees that your software was built with several security conditions in place. Uh, so whenever you handed a piece of software. You can verify that at the station that tells you that it was built currently, so to speak. Now, we're standing. We've expanded it to, uh, to salsa source, which protects your uh pressure control system and your platform.

And there's solar track cellular development, like the environment track, and. I've been dependency truck, um.

[Speaker 5]
We have tooling. We have actions for you to do, uh, and and tools that take care of security repository.

[Speaker 6]
And ask them questions.

This might better. Yeah,

[Speaker 9]
greetings. I'm Alex heale. I'm the head of Open Now development at control point, uh, open now is an open source Secrets manager, so you're familiar with hashicote vault? We started as that reported to do DSL re-licensing. This is a centralized Secrets manager, so if you're familiar with things like stops.

[Speaker 8]
Subs is like encrypted files. This is more centralized, you run it once for your organization. Your developers can then.

[Speaker 10]
On board to that platform and create secrets, and then do things past what you know, get. Secrets to GitHub secrets are static secrets, except the ones in your repository, and you access them open. Balance you to do Dynamic secrets so you can get a fresh a service account that you can buy into the lifetime of the pipeline level and access that.

Do your workflow, and then it will be revoked afterwards, so you don't have any risk of it leaking it. Leaks, but that doesn't matter. You can then also then use every one-time sequence as well, so you can deploy that. For your applications built against openval pull Secrets from it at runtime.

Do things like PKI do things like KMS.

Push this at the open SSF Booth who's coming and check them out there. Next is zarf? Come on!

[Speaker 6]
All right, Andre Keller, maintenance art. This art is a secure software delivery and deployment tool. Particularly, we've been known as the yoga package manager for kubernetes.

[Speaker 7]
Um, and was our souls for is, how do we package up all the software that you want to take to an environment in such a way that it is no longer reliant upon any external dependencies so

[Speaker 9]
you can package up one-to-many applications into his art package the images, Helm, charts, binaries, manifest, Etc all that comes into a single carball. That tarball will also contain your s-bombs like Fireball can then also be signed. That package can be signed so that it can be verified in any environment, and it can be verified entirely offline.

Could take that package. Take it to an interact environment and deploy it, and it has everything it needs to run offline. Uh, and yeah. Awesome! Thank you.

[Speaker 6]
Did I sand here holding my creators off so you can? Thank you. Sorry for the focus on before I was wearing too many hats.

[Speaker 7]
So, it's me. Hi, I'm a trainer. I'm trainer model and, well, I need a center of the proper window. Almost not quite. No, I take my.

[Speaker 3]
Sorry about this. Everything is broken.

[Speaker 6]
Okay, think about this. I'm gonna just put it. Sorry so, uh, basically,

[Speaker 7]
what I think is a way to sign your MLR defect to make sure that there are no headers in there, and they don't compromise the model after you play it. Or even during training, people can compromise the checkpoint and then you take because your training job to crash. And when you started from the last checkpoint, that's a compromise checkpoint, and then everything Downstream

[Speaker 6]
is broken. And

[Speaker 7]
we're also working on using the same model signing tool to sign data sets to sign.

[Speaker 5]
Uh, anal artifacts like water cards, 800 cards like productive development and City servers, and so on. And the demo are supposed to also show you how to redo this with six tool and how this is integrated into Cardinal. Uh, you can see the sermons of that, or if you go to the model signing Repository, you'll find the Jupiter notebook that goes for the same demo.

And since recently, apology model signing is also a part of Nissan SFO storage, so you can just instalitaries, because therefore it's using mix.

Andrew. Are you a nerd? Yeah, OSS CRS. All right. Are you gonna try to plug in as well?

[Speaker 1]
There we go, all right. Uh, so, yeah, um, my name's Andrew chin. I'm from Georgia Tech, um, and this is Oasis CRS, um.

[Speaker 5]
This is derived from, uh, the Northland AI cyber challenge, uh, we're a cyber reasoning systems are ejectic systems slash, traditional security tooling, or hybrid Olympic 2 that can both find bugs in your repository, as well as provide patches to pixels books. Um, so, uh, this is sort of the interface.

Um, don't get to ball go down by off the, uh, command line stuff I have. Every single CRS is called to use these exact three commands. It's all consistent, uh, the first one specifying which series you want to use. I'm just using a codex CLI, but the second one is the project you want to Target.

Uh, this sort of looks like, uh, a project integrated, um, style. Manner, where you provide a Docker environment and some perfect purchases and a build script. Oh, spoilers. And then, finally, you run it for the cicd case. We have this nice diff. Cli option to provide a gift of, for example, a pure that you want the agent to focus its analysis on.

And this is what the result of the bug fighting is going to look like. We actually see that against my AIXC semi-finals project of NJ. Next, we found a POP, but let me just run this so that we can see the thing running. It's going to take some time, so let's move on to the patching side of things where we provide a patch for the particular bug we found and actually the input to this is the POV found by my previous agent.

Um, this similarly runs in that sort of fashion. Thank.

[Speaker 6]
We wanted to talk just a little bit about

[Speaker 2]
s bombs. John, would you like to come up because we there was? There were questions about? Well, I'm going to call it frustrations about s-bombs, so if you could address those for us?

[Speaker 3]
Uh, so I don't have anything to hook up because I didn't know I was going to talk about this, uh, but is a project in openssf that helps to create accurate s-bombs by leveraging a total attestations to do so, and so there's actually two different parts of it. One is creating the attestation for the build process, um, when it comes to s-coms.

I like to say, build time is the best time. Uh, that's when you actually can understand and see what dependencies are being pulled in. What's actually going, uh, into? Piler, and then the resulting binary that's produced or whatever the output artifact is. And so, with witness, which is a cncf project, we actually do down to the syscall level tracing of the build process itself.

There's also a man in the middle proxy that captures network traffic. So, if you're going out to Pi, Pi, or npm to pull down packages, do you know where you got that package from and then you read out those files on disk if the compiler. Those files in. We see that as well.

So this way you get an asphalt that's accurate. According to that, the sort of traffic and interactions that

[Speaker 6]
we see.

[Speaker 3]
And then there's a package resolution part, which is what s vomit itself does so you pass in. You have to station is generated 2s vomit, and then it can generate, and it's using things like protobomb underneath it to be able to go back and forth between spdx, cyclo, and DX.

Things like

[Speaker 6]
that, um, can I ask you a question? Yeah,

[Speaker 9]
um.

[Speaker 8]
Um, do you have the ability to turn off, like, uh, top level to transitive level dependency packages for your um output?

[Speaker 9]
We do not today, but we, we accept the requests. So, is this the top level dependency? No, no, it will. It will capture everything. Oh, it does. Oh yeah, yeah, okay, cool. Thank you. Anybody else?

[Speaker 7]
So, I just wanted to say that brother, one pass, a graph APA to work with the the defense tree, and then you can do exactly that in EQ.

[Speaker 2]
Nice to meet you. Um, if we, if we don't have any less questions, I would ask.

[Speaker 6]
Just a couple minutes, and I wanted to again raise something that came up in our previous session. And that's maybe the most important question here is.

[Speaker 2]
Where, how do I start? Where do I start? And I wonder

[Speaker 6]
it

[Speaker 2]
again, since we have all these maintainers here. If we could pose it really quickly, and maybe go back through. But what knowing nothing about me if I ask you that question, what are you going to ask me? And then, what are you going to tell me?

[Speaker 6]
Yeah,

[Speaker 4]
um, what's your current problem, like the like? Let's start with your actual problems, like tie, tie it back to deliverables, okrs, whatever the current threat in internally and then, and then we can guide you across the Personas.

[Speaker 5]
I would say, take a look at today's time based on. We'll want to help you understand their journey and whatever makes sense in that Journey. So thereforement?

[Speaker 9]
I think

[Speaker 3]
it would be. Look at where you are involved with software. Are you adjusting Upstream software and pulling it into how you deploy software? Are you building software, and both of those are going to add different constraints around which tools are most applicable. What else did I?

[Speaker 6]
Uh, use the tool that you already have. So, if you're using it for sequence, you might as well keep doing. So, let's go over there.

Uh, I'll add on to the rest of where everyone said, um, if you

[Speaker 3]
have some time to spare, definitely attend some of the meetings for all. Great people here.

[Speaker 8]
Love the thing for Saturdays!

[Speaker 7]
Um, that has talked to us in the hallway. I'm sure everyone here would love to hear and talk about more. What?

[Speaker 3]
What problems you're facing and what you know, how we can help you, how all the tools together can help.

[Speaker 6]
And the area of Luke is working on

[Speaker 3]
AI's empty enabled security, so we're going to come to you with AI tooling that can access the unnecessary projects and give it information. The prioritized list to secure projects. So, if you keep a reach out first.

[Speaker 10]
Amazing! Thank

[Speaker 6]
you in the future! We're living in the future of Kevin. So, yeah, we're living in the future. It is terrifying and exciting.

[Speaker 2]
I think I think we're pretty much good unless there's one more to wake member one more question. Okay.

[Speaker 6]
All right. So, was this helpful? These last two sessions was this helpful on both sides? How about the CD people? Was it helpful? Few hands. How do you see young people are left? People that are today that are here, okay?

[Speaker 8]
So, um, if we did this next year, would it be? Would you want to see this again? Okay, great. All right. Thank you. Thanks, everybody.