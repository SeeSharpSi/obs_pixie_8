---
type: transcript
topic: work
---


Yeah,

[Speaker 1]
I need the second screen for.

What is that right?

[Speaker 2]
So, while

[Speaker 3]
Brett's getting ready?

[Speaker 4]
We're going to do this talk. Then we go to lunch break, encourage you to come back, grab your food, and come on back because we've got an open ssf.

[Speaker 3]
What would you call we better if I were right?

[Speaker 4]
Town hall thank you. That was the phrasing I was looking for, so we'll, we'll, we'll have a a conversation over the lunch hour in this room about security. Open SSF is going to to be here, and that will begin our afternoon a security box. I'll focus for the rest of this day, so your lunch is a great chance to come back and join us as we have these conversations question and answer discussions with.

Representatives from Northern SSO.

[Speaker 3]
The production model. I don't know a joke about production from you. Okay, so everybody know about the joke that starts having is a production problem.

[Speaker 5]
It's a, it's a the bargain is not in the soccer. It's a problem with the the connection between the seat and the keyboard.

[Speaker 2]
All right, so thanks very much.

[Speaker 6]
Brett Brett Smith, presenting for us from SAS Institute, right? Go ahead, William Mark, uh, so we're gonna talk about platform engineering today. I apologize if you guys work on devops, something to make for me. What is platform engineering?

[Speaker 3]
All right, fine, oh, that's fine. So, platform engineering is a discipline that focuses on building and maintaining internal platforms to streamline software development operations. It aims to create self-service environments for developers, enabling them to deploy, manage scale applications efficiently while abstracting away the complexities of the infrastructure management.

[Speaker 1]
That's the official definition.

[Speaker 3]
I have been accused of talking about electric cheap a lot. If you've ever read Android to dream of electric sheep, that's where it comes from. We're the digital Shepherds and the electric sheep are the products that we built. Um, the artifacts, containers, and deployments, uh, following through our pipelines at all hours and the question I have is, how do we manage the sprawl, chaos, and bad decisions?

Uh, with compliance and security. Devops. Um. So, devops is a cultural methodology that it unifies development and operations to improve collaboration, Automation, and continuous delivery. It's excellent. It also stops scaling at about a 27 mile startup, and so when you get to 3000 developers, devops is probably not the best idea.

Um, if you want unicorns, this is how you get unicorns. Um, not that I have anything against unicorns, but this is how you get unicorns where each development team has its own idea of how it's going to go to do something, um. And so the problem is that unicorns are clever, okay, and you know, I'm not using clever as a compliment.

Uh, they may be good at producing things fast, but they're not good at compliance, security, or governance. The thing is, is that? No two are alike. It makes them hard to hurt. Also devops, um, the fact about unicorns. They're not good at documentation, uh, this makes onboarding new developers a devops, uh, process challenging, uh, this can lead to confusion frustration for new developers, which can slow the development process.

Uh, they were very proud of the custom shell script they wrote 15 years ago that still works in production. Um, and again, this is how you get unicorns. Not that I have a thing against unicorns, but I just don't want them in my pipelines, platform engineering is the antidote, uh, instead of every team Reinventing the wheel or Worse, Reinventing the entire vehicle and changing the wheels while they're driving it down the road.

You build a platform and handles common problems once correctly and at scale. And, um. I just like to ask, can you please stop beating your sheet to the sarlacc pit? So, what is platform engineering? Yeah, you see how nice and uniform these guys are. There's no one Wings. There's no three Wings, you know, what the one wings do they?

They fly around in a circle, so anyway, platform and engineering is how you hurt the cats, eliminate the unicorns, and eradicate the chaos from your supply chain. More precisely. Platform engineering is the practice of building and maintaining an internal developer platform. Uh, a set of tools and services that help develop teams, build tests, deploy software without ticket Ops, uh, a prayer or a direct line to somebody who knows how the pipeline works does not call me.

I'm not answering my phone. Um. So, so back to purple a lot more. A little sheep on this side? Um, so the internal developer platform? Uh, is the teams, uh, the platform team engineering team's product. Um, I think everyone who's taking all the devop ideas that and you build a self-service platform with developers can click a button instead of battling Cloud Giants.

The the idea here is that just because? They're unicorns doesn't mean they're wrong. It means that we want to figure out the best General way to do this for all of the teams, and we want to make it easy for them so they can go write software and not spend their time working on Ops.

So, this comes to.

[Speaker 1]
Basically, it's just centralized tooling that improves and development velocity. And the real answer, though, for the platform engineering team for the industry for the company is consistency. Okay, I no longer have Mark going off and running and building something on subject and server that's been out there for 12 years that nobody's updated and nobody knows how to work on, except for Mark.

So, um?

I don't have a lot of time, right? So, who benefits from the IEP? Okay, uh, development teams get compliance and security out of the box, uh, I don't know if you guys know this, but developers aren't really good at security compliance, um? And so they don't need infrastructure. I don't need to be infrastructure experts because I don't know if you know this, but they're not really good at deploying the VMS and installing stuff on.

Some of them are some of them are um, and by using the platform. The developers are securely applied by default, and they stop maintaining pipelines. Start maintaining the actual product and a self-service IDP eliminates ticket opts. How many of you guys have opened your issue and asked it to go fix something?

Now, how many of you got it done in half an hour? That's what I thought. So, the idea here is that you want to remove this soul-crushing practice of creating tickets and waiting two weeks for it to be pulled into a Sprint and then creating a new ticket because the requirements change while you're waiting for that other ticket to get pulled in the spring.

Click the button now. I don't normally say click the button if you guys know me. I am an API first guy. I don't want to click your button, but developers want to be able to go and say I need a new go project. Click the button, and they get a

[Speaker 3]
new go project, and it's got their pipeline, their tests, the framework's done. Security team gets standard, uh, gets automated and standardized enforcement. Security checks, standardized policies, and pre-approved configurations are embedded in the platform itself. No longer does a developer have to go? How do I run mass scans. You don't okay,

[Speaker 1]
you

[Speaker 3]
make your PR. The automation runs the sca, scan the SAS scan, and creates the odds bomb. All that stuff. They get it for free. It's in your GitHub actions. You didn't have to pay for it. Follow the rules, right? Um, and then the platform team. You have to focus on the platform because you know

[Speaker 1]
all the

[Speaker 3]
platform guys are downloaded from our platform. And you know, that's all we care about, but we don't care about what Mark's working on we care about the platform, which is another thing we need to work on later, but the idea is that the Enterprise gets consistency without, uh, which sounds boring, but you consider the alternative IDP stops digital sprawl of curl pipe bash Shenanigans.

You guys know me why? And the five different versions of build tools and the one off Jenkins job. Nobody maintains those pretty much um, and developers use the same tools to build the products as they used to build the platform and use test and deploy it. So, now you're getting closer to I'm developing, building and testing in a production-like environment that my customers gotta run, right?

[Speaker 1]
All right, uh, the frequently overlooked benefit is that you get consistent and timely updates for tooling. So, I've got a new tool. I've got a new version of, uh, CLI that I need to put out. I put it in the Dev container or the build container that runs in the pipeline and all of you get the new version, and it only breaks three of you because you were doing something silly, and then guess what you go fix it wrong with it?

Everybody's out, um, and it breaks the team where the pattern where the developers defer updates and security patches.

[Speaker 4]
Time when you come after them with a baseball bat that says Neo comply at 14028 on it. I've got one of those mouths. Um, so the next thing we want to talk about is Chef left. It's an overused term. But if you automate, right? Then shift left works a lot better, so certain people do not need to know how to run their FCA or SAS scans.

They just need to know that they've got three vulnerabilities. They need to go back, so if you automate the running of the security scans, the audit of the security scans. Creation of the giraffe issue. They love that.

[Speaker 1]
Then they just do push to PR and all that stuff gets done for them. And then, oh, I got an email because I have three CBDs and we blocked your merged the pr because you have three criticals you introduced with this. Um, that is,

[Speaker 4]
uh, they love that, like developers, really lovely block them or something. Um, and then after you get an exception, but that's a different story. The idea, though, is that you create transparency on the right, and you make it very simple for the developer to do what they want to do, which is hold.

[Speaker 3]
Push their PR beg one of their friends to review it. Well, I have another person who rubber stabbed it and burned right. And if you protected yourself from all of those things, I just said, because all the compliance my security things ran automatically during that process.

[Speaker 1]
F-Bombs. They're really cool. You just make them, um. The thing we need to know about s-bombs is that one of the things about platform engineering is you want to know where everything is in your platform. The way to know where everything is in your platform is to make. A data model of everything that's in your platform.

In particular, like, my system is all data driven, so the developers love this whole thing. They've got this yaml file in the repo. It tells them, tells me everything I need to know when it's pipeline. And I go, and it gets routed in the right tree goes through the right things.

We

[Speaker 3]
create an s-bomb, and then I know all third-party packages that you did not go get approval for because they're in the s-bomb and they're rifle through it. Found them all went and looked up what we had approved when we hadn't approved, and I come back. And I created the issues for approvals, and then our smes go and do the approvals.

The developers didn't have to take the 200 go, develop dependencies they had, and made sure issues for each of them. Right.

[Speaker 1]
We automated it with the F-bomb, so if you're ever wondering how you can use a nest bomb internally, this is one of the ways log for J. If you had s-bombs, you'd know where it is a medium.

[Speaker 3]
Uh, so this is the type of thing, um. External sharing. That's a little different, not a lot of teams run into this. A lot of guys are, like, I'm software service. What do I care? Well, I just gave you the internal use case for us, uh, in the highly regulated parts of our stuff is highly regulated when I have to sell to a government country like, we're going to have self-cross.

The bank of Australia, uh, Bank of Austria, which I give you sometimes because they sound the same. They both have the same regulations. They won't deploy our software without an S Bomb. That's 10 million dollar contract. Didn't get deployed because I couldn't give them enough. I give them that one.

That.

[Speaker 1]
Is going to use AI to go do the subject matter. Expert reviews of the third party repositories so that my lawyers can do lawyer stuff instead of rifling through repositories. Compliance, so platform engineering. Back to the F-bomb. You've got all this data now. Now you can start talking about compliance, right?

You get automated evidence collection. Um, and let's be honest, like your bosses are, like, yeah, platform engineering. That's cheap. Go play with that outside, and you're like all of a sudden, the audit comes right, and the audit lands the regulatory requirements, the executive orders, and the Enterprise security standards.

Name your poison, um, and in the organizations, um, are like. That platform engineering thing. How fast can we do that? And well, not fast, you should have let me do it two years ago, but anyway. Um, so the? With platform, you get, uh, coherent IDP that can gather the evidence, generate the outside stations, and demonstrate control.

Um, organizations with one one. Spend the next several weeks. I won't spend the next several weeks walking logs trying to figure out what happened now? You're generating this compliance as you're building, right? If you're doing this right, it's event driven, meaning that when you create a PR. I go and create all the stuff for this now.

When that PR is merged, now we're in production. That's a release candidate. I have all of the data and all of the things I need for that particular product to be compliant when it goes out. The door that doesn't make it out. So, what I did the work you rebuild it again?

I get it again, so automating that type of stuff is really important. I'm sorry if you're a salsa maintainer because I'm pretty comment below through this.

[Speaker 2]
Um,

[Speaker 1]
salsa is the supply level levels for software artifacts pronounced salsa, and it's a security framework for ensuring the Integrity of software Supply chains throughout the entire life cycle. Now, I could read you the rest of this, but I'm going to tell you what salsa did for me. So, when the executive order dropped not long afterwards, Google dropped the first version of salsa, which is 0.1, and it was a brutal set of rules on how to make your pipeline your software delivery software supply chain as, uh.

Possibly be, and we went. I went through and detailed it and mapped out all of the different levels to where my stuff was in my supply chain, and that's when I realized the guy who built the slide chain. He didn't care about security, but he wasn't really. He just, he was bad.

So, I talked to my. Uh, past self, and I told him he was really bad at this. And then I realized that I had to go fix all the problems that I had caused and salsa was the way I did it. Now, you're, like, okay, well, what about the nest?

What about? Uh, I said 27001 27 with the two. If you meet the salsa requirements at the highest levels right now, then cover almost all of those regulations. And if they don't, they come close enough that you won't have a few small jumps to make now. The AI, uh, addendums to nists are not covered by salsa yet, so go.

Read the AI addendums to the nest. There's a lot of stuff you have to do around model security, data security, and all that other stuff. But I got to get on to the next subject. Which we've talked about. Its policy is code.

Policy code is a methodology of defining, managing, and forcing policies through code rather than through documentation. Meetings and optimism policy, uh, integrate. Policies integrate directly in the development pipeline to enable continuous automated proportionment across infrastructure deployment, supply chain security, and Cloud access. Now, some for Soul has to write that Regal.

Um, make sure it's on you, but basically with, like something like open policy agent. You can go right, Rigo. We've done this. I didn't do it. I got it interns to work on it, and then we, you know, reviewed it, um.

[Speaker 2]
So, anyway, the whole the whole idea. The first line here is all you really need to remember. Is that security is codified, automated, open, and accessible. Also, now that last part of that sentence, you're like, what do you mean? Okay, what you need is stakeholders. Now, one of the things we make in the state now, the platform engineered, is look, it's my platform.

You can't play in it. That's a bad idea. You are generating framework. You need the security professionals to come in and help you tweak the policies and then you trick them into writing verita, and then the developers who are like, well, I don't like the way that works. Hey, that's nice, Mr.

Unicorn, you can tell, right? And then they help with the policies, and then they feel like they have, you know, buy-in, but you didn't have to do it right, okay? And

[Speaker 1]
so it

[Speaker 2]
works out pretty well, right? Um, again, it improves collaboration. That's something you should take away from the slide, even even. So, shift down security.

[Speaker 1]
Got a guess of this.

[Speaker 2]
The guys at kubernetes have stolen all the really cool terms. They coin shift down security. It's not mine, but basically, you are pushing your security checks down into the platform. All right, your compliance is there. If you are a developer, you click the button. I give you a pipeline that pipeline meets compliance out of the box.

I don't have to talk about it, and if you're, uh, and I saw 80 of the problem all right, and so when you're doing platform engineering, solve our 80 of the problems. Okay, find the general thing. Go to the next 10 and ask them why they're not compliant and then use that 80.

Force them in clients, and then when you get to the last 10 the real unicorns, you ask them how much money they make, and you make exceptions based on the amount of zeros they bring in. Okay, because bonuses or what matter, not anything else, like, my bonus? It. So, where do you start, um?

One.

What am I up to? You're over potential pitfalls. Outliers complexity over engineering that one's really bad, um? Benderlochen, lack of product, and it's like your platform is the product.

[Speaker 1]
Uh, ignoring feedback. Okay, I'm pointing that one out. Talk to your developers. Talk to your security people. Make sure they're in the loop if they're not in the loop. They're going to hate you. Don't want them to hate you. You want them the right way.

Sorry, this. Your steps anyway. So, is platform engineering right for you? Okay, so remember, in the beginning, when I said devops doesn't scale? Um, devouts is the right. Answer your 27 match start, and there's only one dude. He wears security hot, the offs hat, and the other Hawks and wide attacks.

Um, when you get the 3000 developers, platform engineering might be the way you want to go. So only time. I'm Smitty, I'm afraid of robots. And questions.

[Speaker 2]
Platform engineering team to your Enterprise to actually implement. Seven years. I've been working on the stupid thing for seven. I spent the first three years building the most insecure thing you've ever seen in your entire life that burned through and built things in a million miles an hour, and I put the next two and a half years securing it, and now they're telling me I gotta eat AI.

[Speaker 4]
Are you building golden house that support teams using age 11?

[Speaker 1]
My ml Ops teams are the first devops slide. The guys working on the models are all unicorns, and I'm trying to fight them get them in line. Again, if we are advertising, the large vendor has some tooling we're using for hugging face models, and we've been, oh, I proxy everything through something you are not allowed to curl.

Pipe bashed up off the internet, and this particular thing I'll say it because they had me out give you lots of wine jfrog artifactory. We priority everything through our Factory. You even vendor the models that you use so, and then jfrog's got a whole security piece that goes with it, um.

Also New Jersey that? Like, it's a bit of the Wild Wild West. We have the the pressure from the management to you must do AI right now, and I've got teams that are, like, cool. We're gonna just wrap some stuff off hugging face and make a product and send it out.

And then I go, and I call the lawyer. I'm, like, John, um. What are we gonna do here? This is GPL, and I have no way talking. He's like, put in a separate container, and then they. When they deploy it, they have to mount the model into our code because it can't be next to our code because it's GPL and you're like.

[Speaker 2]
That's not gonna scale. John, so these are the type of things you're I'm running into. I, I don't have good answers. Maybe next year. If I come back, I will have better answers, uh, or I won't. Another question.

[Speaker 1]
Yeah,

[Speaker 4]
do you build out your own IDP, or are you running backstage or something?

[Speaker 1]
So I've tried boxes three times, um, and I've had four other people try backstage and try and figure it out, and we've all come back together. And after we got done crying. We were like, this is stupid. We're not doing this, but backstage is probably the. Most popular answer.

Uh, there's a particular company called harness. They're built all on top of backstage. You saw in my slide where I said vendor lock-in the question you asked harnesses is if I buy a U harness and I go and build out all this stuff. What happens when I want to move off of you, and they're, like, oh, we're still backwards compliant with backstage right now.

You get into, like, what's where? My developers worth, how big are we? You know, if you've got 5,000 developers and your your platform, engineering team is 150. You could probably do backstage. Tokens. You could probably do backstage, but every time I've tried backstage, it has gone. Yeah, not.

[Speaker 2]
Well,

[Speaker 1]
so it's

[Speaker 4]
what we found

[Speaker 1]
our IDP is very ugly. It is, uh, use a template, clone the GitHub repo, and then fill out the yaml file and try not to mess it up. And then you're done. Yes, do you even need a backstage or an IDP if you are going to go agency interface anyways?

I don't know. I've been struggling with that. There's been a lot of different we've had. We've kicked around. So many ideas of, like, I've lost track. I've got a giant markdown vowel, somewhere with all the ideas we've had on what we're going to do moving forward. Um, personally, I like the system we have now because it causes a bit over pain, and I, you know, enjoy that.

[Speaker 2]
Any other questions?

[Speaker 1]
Yes, maybe one question, but um, there aren't the dumb questions they're smart. Let's say you're, uh, you set up these pipelines, which, um? Are breaking the compliance standpoint, but?

[Speaker 4]
I ended today with Prides down CIS. Admin hasn't religions onto the box and just does it completely bypassing the entire workflow that you view, set up, what? Yeah,

[Speaker 1]
not possible, not possible. It's not possible, just lock it down. No, no, no, no, no, no, there's one door in to build the system.

[Speaker 4]
It's a pipeline. The pipeline has one door in literally one door in, and then you can't run the pipe lock.

[Speaker 1]
2 can't run the pipeline by hand. Now, we've gotten all Lymphony and a couple of the guys that worked on it, and we scared ourselves. And we went walk down some more stuff, but? You can't push stuff through with, like, force it through. As an admin, we have a process you.

If you, for some reason, can't pass your security gauge and you can't pass your testing gates and you absolutely have to go out. You can go make a jira issue and get our CTO to sign off on it, right? And then we'll promote your stuff up by hand, but in general.

No, don't. Yeah, no, there is no, there is no side path. That's the whole point of platform engineering you built this end platform. Well enough that it does not fail. It runs 24, 7, and it never goes down until it rips the rug out from on you. It wasn't your fault to begin with.

Ask me about that story later. Um, and then there's only one path. And then, so mine's event driven. If you failed somewhere in the middle horribly, I might tell you just go rebuild your package and it'll go push back through again because it's all of it, and so there's no manual.

There's no humans that touch it once you merge your PR.

That was great, right? Go on. That was that. I thought you wouldn't appreciate it.

[Speaker 2]
I'm the one I love talking about. Actually, there's plenty to talk to me like that. That's great. Anybody else, anyone else? No good. Yeah, don't go into platform engineering. Kids don't let the kids put more in there. I find another job.

[Speaker 4]
Thanks very much, Brett. I have made a mistake. We've got kids shame for in five minutes. Lunch starts at 12, 30 from here. So my apologies for my estate and Kimberly got you here yet. I'm not sure if I seen it. Oh

[Speaker 1]
yes,

[Speaker 4]
very good. Okay, so let's get you connected with my dad,

[Speaker 5]
uh, sorry, did? I, uh, hilarious mistakes. Okay, okay.