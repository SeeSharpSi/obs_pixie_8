---
type: transcript
topic: work
---


Move along here from work.

[Speaker 1]
Uh, I'm Steve Taylor. Like I mentioned earlier on with deploy Hub and also the? Primary leader of the artilios project. Um, so today we're going to talk about ortilius and just give you a little bit of background about myself. I've been on the the CDF GOC for a couple years.

It finally rolled off. Let somebody else take a take a stab at it. I help bring. The CDF into existence and also. Um or Julius project as part of the Linux Foundation. Um. I specialize in supply chain security. I would consider my when I, when I introduce myself, I'm like, platform engineer and deaf psychops.

So, I try to cover. And then devops as well. So I put all those in my business card, uh, just to stay covered on all those fronts. Um. So? What we're going to talk about today is how we look at the vulnerability world and how we look at what's really important.

When we talk about vulnerability cves. Um. Artillius is focusing on post-deployment vulnerability detection and remediation. So, one of the things that we look at is s-pops. Uh, as bombs are very important to us, even though that we know that they're not perfect. Uh, it's a starting point. So, the starting point that we look at when we're talking like about Jenkins earlier?

Yes, there's Mia s-bomb for the the war file. But also there can be another s-bomb for probably some of the type scripture JavaScript. Um, there's going to be other s-bombs for not only the core product, but also for each plug-in. It's going to have s-pom. We take all those s-bombs together and aggregate them into what we call an application.

Um, that is where we use that s-bomb to create what we call a digital twin. And that digital twin is where we can do interrogation, uh, about the vulnerabilities against the digital twin, instead of having to go out and rescan things. So, basically, what the digital twin we actually mapped, the digital twin to the runtime environment?

Now, in some cases, a lot of the open source projects you don't necessarily have a runtime application. You're delivering just a a package, you know, going module or a python package? Um, we still want to track that because it's important, but your run time isn't going to necessarily be a kubernetes cluster for that open source project team.

But if you're at a company where you're actually deploying out the live environments? We're able to map that live environment so that as bomb back to the repo and then we can do interrogation on that information.

So this is just another view of what we're talking about. Uh, the in on the left side are are going to be our our inputs. Our s-bombs, um, we have a way to go ahead and and gather information from your kubernetes cluster. So when you actually deploy to kubernetes, the kubernetes itself will go ahead and especially in gke and AWS.

It'll kick things out to the log file and say, I'm deploying this pod. Container to this pod and stuff like that. That's one of our other import inputs. The cicd evidence that's important because, as Ava ever tried to take a Docker image. Uh, that's running summer and figure out where the source code is.

There's no link between the two. Unless you really specifically go in and put into your your Docker build file, uh, information. There's no link or into this is able to to create that link when we link in when we hook into the the CI CD pipeline. Third, bring in information from osvdaf.

Your artifact repositories opens a scorecard. All those inputs we aggregate together, and now we can tell you exactly. Where things are are happening. Where, where is my vulnerabilities? Which endpoints do I have to worry about? So, one of the first questions we we ask is that we get people ask us.

There's a there's cyber risk out there. Uh, in my in my posture, where is that? What is the Cyber risk? So, what this is showing? This is our dashboard, and it's showing us in this example that we have 71 post deployment vulnerabilities. And what we mean. By that is, we deployed two weeks ago, and I just found this in the kubernetes cluster the other day by accident.

We deploy and we're on gke and we were looking at our our vulnerability report in Google. Post-Deployment vulnerabilities in the cube proxy. So they've deployed, but they haven't patched yet. So, I have high critical vulnerabilities that have shown up since my last deployment of gpb. And that's important because I now I have to understand.

What do I have to do to remediate that risk? Uh, do I have to do a kubernetes upgrade if it's available? Do I have to do some routing things on the load balancer? What is my mitigation steps, uh? And then, this also is going to show how fast things are going to be remediated.

Um, each one of the little barely visible like little blue hyperlinks corresponds over to the nist. Um, a security guidelines. So, when we get there, we have to say, what are my vulnerable packages and where are they running? So, in this case, we could see Alpine has a couple critical, and what's the third one down there?

I can't read it from here. Orango has another. Orango has a couple higher critical vulnerabilities, so with this information, we can really focus on. What's my critical vulnerability stance for production? Rainbow rainbow sit pretty simple. I can upgrade our rain, goes for my my home deployment, go bump the version, uh, and get my remediation done on my next deployment.

And that's where we're headed. Next is, how are we going to go ahead and neutralize this threat? One of the things that the team's working on are open. Source team is AI Auto remediation, so everybody, um. He knows what you know. When you build your software, you have your package dependencies, uh, a pythonous requirements that text.

Uh, node.js is your package your package file. A lot of times, the the simple remediation is bumping to the fixed version. And we're actually working on an mCP and an llm that will actually go into the into your repo, clone it. Look at your package dependencies to say, oh, I just have the bump to this next version.

That's great. Is this going to be a breaking change, though everybody's always worried about that. Am I going to break something? So, part of the AI, um? A remediation with mCP is actually going to Branch the code, go off, and make the package, uh, dependency, change, and then go ahead and submit the the build to go and see if it's actually going to work.

And if it does. We go through the MCD part and open up a polar crust or merge request. For the back of dependency change. From there, they your developers are going to go ahead and again review and approve or deny it if they approve it. Then it moves through the regular pipeline and just as normal.

We're not trying to take the developer out of the pipeline, not trying to take the human out of the loop. What we're trying to do is make things happen faster. And as part of that. When we look at making things faster? Um. We, we want to make sure that when things are going fast that we're not bombarding with noise, does anybody ever use Nick?

Um. Cystig. Those type of things? So?

So, we are seeking, um, some more contributors and adopters. Um, we do have an up and running version on the playups websites. If you go to app.app.deployhab.com. You can go up there and sign up. We also have. If you want to contribute? Uh, the code base right now, uh, we did a bunch of rework, so it's a node.

Next, react next, goaling some python and the the ml, the AI piece, I think right now, is in Python. So please come out and join us! Like I said, we do, um, like beer Donuts. So, uh, go out there. And the website will have all the the meeting times on it.

Mondays. Uh, every other week at 9 30 mountain time and Thursdays every other week 9, 30 mountain time. Um, I will be around, uh tonight, if you want to ask me any questions about that. And let's see what else we got. I don't think Mark will give me my three minutes left.

So, uh, that's it. Just a quick thing and reach out to me on LinkedIn. Or, um, my emails, uh, real simple, just Steve deployhub.com. So, thank you everybody. And if you have any questions I'll be around?