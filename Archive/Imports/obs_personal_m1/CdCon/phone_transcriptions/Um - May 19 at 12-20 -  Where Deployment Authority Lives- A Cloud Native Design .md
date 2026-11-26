---
type: transcript
topic: work
---


Almost red.

[Speaker 1]
Hey, good afternoon, um. So, as you know, uh, yes, with enough time and effort, I can actually get basic effect for, um.

[Speaker 2]
What'll here talk about today? Is the fact that Bitox has become one of the most influential form models about native infrastructure? It gives us a really clean way. The reason about the desired State reconciliation and automation? And because of that, a lot of things to standardize on GitHubs, because the way to deploy kumatic workloads.

My name is Kim Shaffer. I'm a CF devops engineer at game plan Tech and pretty much I spend all my time working with get off space platforms and environments for some of these assumptions. Start to matter a while. But there's a subtle architectural assumption hiding inside many get Ops implementations.

And most of the time, we don't even realize we're making them. That assumption is about where deployment Authority actually lives.

Get out skips a very powerful promise. It becomes the source of truth. You define the desired state of your system and get, and the controller continuously reconciles your cluster to match that state. So, instead of pushing changes into the cluster, the cluster constant length is Poland. We get. In many environments, a get merged directly triggers deployment.

Someone opens a pull request. It gets reviewed, and it gets merged. And seconds later. That change is running in production. For small teams or simple environments. This works extremely well. It's simple, it's fast, and it's easy to reason about. And importantly, it feels big. But safety depends on some assumptions.

Systems don't stay simple, simple from all. As platforms grow, environments start to diverge. You now have development environments, production environments, and sometimes for strict or regulated environments. And those environments don't always share the same trust model. The system where changes are proposed is not always a system where changes are allowed to be deployed.

If you've ever heard something and immediately thought, well, I guess that goes into production now. That's this model in actually. Once that separation appears, the simple GitHubs model starts to break down. Not because Gibbons get Ops is wrong, but because withoutgrown the assumptions behind it.

In many GitHub systems, a simple event, the merge finally becomes three different things. First, it proposes a change. Seven. It implicitly approves that change. And third, the system immediately enforces it. Let's make that concrete. The developer opens pull requests. Someone reviews it. Maybe it gets merged and then seconds later that changes running in production?

No additional decision point, no separate authorization step. That one merge just did three jobs proposal approval and enforcement. And because it feels so natural, we stop questioning. On the left. This is, how many get off systems behave today? It is not just proposing changes, it's effectively acting as a place where deployment Authority list.

Emerge becomes both the proposal in the authorization. If you think about your own environment for a second? That's probably true there too. If something gets merged, it gets deployed. Now, on the right, we separate those concerns. Get proposes changes. The platform explicitly decides whether those changes are authorized. And only then does the control Workforcement.

Same tools, same workflows. But a very different architectural model. The different difference comes down to one question. Where does Authority actually lift? This becomes important when you introduce trust boundaries and some organizations, the environment that proposes the change lives in the commercial plot. While the environment where it may operate under is entirely different, has parameter security constraints.

Um, I think especially in government systems or highly regulated environments. Now you have a separation between where the changes are defined. And where they are allowed to run. But if the git merge automatically becomes a deployment authorization? That boundary disappears. The commercial system is now implicitly deciding what runs in the restricted environment.

And at that point, if you start running into some really uncomfortable questions. Who actually approved the diploma? Was it the reviewer? The person who merged the system itself. And more importantly, what

[Speaker 1]
system had the authority to make that decision?

[Speaker 2]
Declutter architectural model separates these three responsibilities. Proposal approval and enforcement. Gives excellent aproposit. That's what it's designed for. Controllers from excellent ad enforcement. They continuously reconcile State. But authorization is different. Authorization is a decision. And the search was long on the platform, not hidden inside merger. And importantly, that decision should live with the system that forces them.

Not necessarily with the system that proposes them. Because those aren't always the same place. Once you make that separation explicit, the system becomes much easier to reason about.

So, in summary, getoffs works best when responsibilities are clear. Proposal approval enforcement. You can absolutely remain the source of Truth.

[Speaker 1]
But it shouldn't quietly become the source of authority.

[Speaker 2]
So you can find my contact information on the slide, and I'm also happy to take any questions either now or after the call. Thank you.

[Speaker 1]
Good, good. Finally, everybody say, Brett, say, Mark first. I love you, but?

[Speaker 3]
All right. So, so what have you found as viable sources of authority if git is not the thing, or do you do you end up layering something over git that becomes source of

[Speaker 1]
authority. Yeah, so, and

[Speaker 2]
that's again. I think if I didn't have time to go into all day. How do we actually do it, but the short answer is, we still use, get? We use Argos CD. But in our restricted environment. We also have a controller that we refer to as the approval gate.

So, it's the same Argo setup that you know and love. We just add this extra piece that gives us the authability, and we know exactly what happened on the secure side, so we basically can look at that. We know who actually did that final approval who had the authorization in the secure environment?

What it gives us is the ability to have all of our developers working in that commercial environment, so

[Speaker 1]
it

[Speaker 2]
really gives Mexicans and onboard people get things going, keep things moving fast. But when it comes time to actually deploy into the restricted environment, we have that extra control so I can have all of my developers out there, but a very small subset has the ability to that final approval insecure system.

Now, Brad you, yeah, Frank. I think you, you actually kind of the question I was gonna ask. Now, the one thing I will say is that? Um, we've expanded our use to get out because I believe everything along we get. We need some sort of sort of control too.

Have you thought about, like?

[Speaker 4]
Documentation in here. Have you thought about, uh, your Regal policies in yet? Have you thought about your, uh, all the other things I mean, we've got the same Hardware set up without the extra step, you know, we don't care. We didn't do it. Um, but the, but we have very similar, but I've expanded the definition of get off how everything goes, and you get tests stop everything, especially not.

And so, for us, uh, everything doesn't get, um, so a couple things you know? Everything's in get everything's documented.

[Speaker 2]
Everything is cooked, not just infrastructure. Everything is code, and if it can be automated, it is automated. Um, I can work myself out of the job, I would be quite happy,

[Speaker 1]
right?

[Speaker 4]
The whole job of us as platform Engineers is good. Our coach people out of jobs, we cook ourselves so well someone out of a job.

[Speaker 2]
And to be fair, I can tell my boss that I'm not doing anything,

[Speaker 1]
but yes, that's curious. Basically, I guess, yeah, with the how fast things are moving. There's always going to be something. Do some new way that we get better and faster, especially as you start writing.

[Speaker 2]
You know different models and play different AI into play, so I'm not really concerned. I'm going to lose my job because I automated it too much. I'm just going to solve a lot of the headaches that the developers have, and therefore they end my way so that things are much happier.

And everyone has been wonderful. What? Securely because we can't have any random persons going

[Speaker 1]
on the sphere side?

[Speaker 5]
Um, I loved what he said about getting being a source of Truth. Um, are you saying that then git would be or what what I heard he's saying is the head revision on the main branch, perspectively, reflect what is in production. At that point, are we pulling from what's in Prad, or are you saying that you could still go through the pr like that?

The control plane would be in some external system.

[Speaker 2]
Yeah, so everything is basically the same. Um, the difference is. Familiar with Argo. Typically, Argo will just pick up those changes that happen and get that was merged to me, and it's just going to automatically deploy. Um, there is a button that you can flip that says, oh, no, don't want to do it.

I'll click the button myself and do it, but it's awesome. That's secure. How do I know who flipped the button? How do I know that no one unflook the button? Um, so the approval date makes it where you have to go through the approval process in the secure side, so everything stays.

The same is what you would normally see in an Argo CD style, except there's this controller that before it will actually merge um and deploy on the or sorry. It will emerge, but before, actually, it's deployed in your secure system. Someone has to go in, who has authorization to begin?

That system has the authority to actually make that final decision. And actually do it there.

[Speaker 5]
I'm sorry, can I ask? So if you are merging, then how is it still the sourcing true? Because if you completed the merge, but it's not really then. How do you know what hazard has it before? Um, good question, um, so one. You know, we do it as kind of a proposal, so there really is very limited time between when someone merges, and it should be very quickly take place that someone goes into the secure system and approves it.

So you're right, there is that difference, but we know that all the code is there all the documentations there. The only thing that could possibly be running is what's in that repo. Um, but you're right, there is going to be that delay, cuz it's not the the. That can happen.

Um, but you know, typically, I don't think most people would be what I do. And I said, you know, or go to Saint get like 10 second intervals, but I can't wait three minutes. Um, so normally there's going to be a little bit of a gap there anyway, but it is coordinated.

Um, but again, this is where it wouldn't necessarily work for every type of environment. But for Crossing that trust boundary, but you want the benefit of having one repo. So for us, the option is we set up, and we copy all that code over for every deployment we copied over to the secure system.

Um, you can just automatically see where that gets really, really, bad, really fast. So, there's only one repo with our code. Um, it's all right there. The only difference is, there's an extra approval on the secure side.

When you implemented that, what kind of a

[Speaker 1]
pushback did you get from developers? Did they care, um,

[Speaker 2]
they don't care at all, because from their point of view, they do their thing. They, you know, you know, say, hey, you pass off, you know, the python passes all the tests? Um, it gets merged. They're happy. Um, it's more. My team is the one that goes in, and does that final approval?

Um, but the developers don't see any difference from their point of views? Scale in your environment.

[Speaker 3]
Um, as I guess to how you define the way developers and development.

[Speaker 2]
Um, my developers are,

[Speaker 3]
thanks! Um,

[Speaker 2]
so, yeah, so it's not the tens of thousands or thousands. Just

[Speaker 3]
folks understand what was, right? Exactly

[Speaker 4]
right. Yeah,

[Speaker 1]
yeah. So, yeah, I know we have a thousands so, but you know, would it still, I would say, yes, um?

[Speaker 4]
So, I'll take that answer. Yes, it does.

[Speaker 2]
Um, in your Camp. How many uh key lace you have or the developers to the government and the testing part? Um, so we do not have separate keywords. Um, so our developers have the player of writing their test, and they will write their tests and the test will pass, or it will not get deployed.

But yeah, we don't actually have a separate qxt. I was expecting the answer. So, how do you handle? Let's say I'm a developer. I build this.

[Speaker 6]
Imagen and try to make the best pass like the criteria. They used to separate that, you know, not making

[Speaker 5]
dance fast. And so, yeah, I guess Parker comes down to. As a company, you have to build a culture, um. That, you know, to do what you're talking about and just pretending that the test pass and pretend that

[Speaker 1]
we have tests. That's just not acceptable.

[Speaker 5]
Um, so you have to hire the right people training the right people and have a true no-blind culture. So, if you, you know, have a deadline, and you say, hey, the tests aren't passing. That's okay, um, yeah, we would rather take more time to get the test passed than to pretend that the test practice.

But you'd have to have a culture that supports that and not have people running around pointing fingers and trying to blame each other. So, it it's not a technical issue. It is a people watching. Thank you. Thanks very much.

[Speaker 3]
All right, lunch, break, and come back.

Stacy Potter, Catherine Brookman, Katie McKee.