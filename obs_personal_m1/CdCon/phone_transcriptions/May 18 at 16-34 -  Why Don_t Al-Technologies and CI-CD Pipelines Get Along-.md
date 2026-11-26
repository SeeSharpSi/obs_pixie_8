---
type: transcript
topic: work
---


Uh, hi, everyone.

[Speaker 1]
Welcome to cdcon 2026 again, I think. Uh, my name is Vivo. I'm a Siri Foundation Ambassador. I work for Capital One. Um, today. I mean, I've talked about the glucose tax earlier, and I was in a great panel managed by a moderated by Tracy. Thank you so much for that opportunity.

I, I wanted to talk about something that is, um, like, very relevant, or I, I feel this is going to be very relevant in the coming days. Uh, as the AI. Revolution explosion in whatever you call it is happening right, right in front of your eyes. I assume, like, you know, the the days where we would primarily assume that deterministrate pipelines which we have today, meaning, like, if the pipeline fails, something's broken, and the pipeline passes everything's great.

Might not be relevant as yours, right? So we would need a combination of something that's domestic in nature, but also you need to have some sort of a progressive nature of the pipeline, and that's why. They thought I, I kind of name it as the organistic pipeline, so we'll explore, uh, look beyond the binary logic of fast failure and.

How we can architect AI driven risk? Uh, assessment of the pipeline that would kind of be more relevant in the in in the coming days. Um, so? Most pipelines are like, excellent rule followers. You, you put Declarative pipelines you put like logic in the pipelines, and the pipelines are going to go follow the process as is.

Without fail. If it is having an issue, it's gonna prompt it. If it is going to pass, it's gonna go through it. But, uh, that's where the the challenge starts because? Uh, you don't necessarily. And like how many of us just show off hand? The pipelines pass. The deployment is done, but then after like, some time, you start seeing an issue.

If I'm playing fast, should not see anything. Um. But, but that is, that is exactly the the nature of things that would get exponentially harder to do when we have this evolution of AI. Um. So? Um. Green is not always safe. Is what I kind of started thinking about, but my my challenge is like?

Whoever, like, you know, things of the deterministic scene like, yes, the pipeline was built. Uh, we have those texts. We have Uber policies that govern rules, policies, things like that. But ultimately, we're kind of putting the same rigor for, uh, one line HTML change. Versus a thousand line. Core Business logic change?

Uh, and what we're trying to do there is like, you know, the pipeline passed for both of them. But the rigor of risk is not the same. The rigger has to be higher for something that's touching, like a core component of an application. Like, if you're changing like an auth model on an app that's?

We've been back security that's going to impact. The experience has to be weighted higher in risk versus like a real me update. Well, readers don't necessarily need to trigger release, but still. And like, you know, the gates, the static Gates that we have today are blind to that because they don't understand the nature of the change.

But they were never intended to because a human was always. Doing that while we are going towards this agentic framework of AI is now. Making decisions, thinking of like writing code, obviously. But then, oh, I want to pick this package, and I want to use this framework, and I want to kind of.

Review it this way. Uh, it's very hard for us to kind of see this happening, where more and more context will get lost as humans start getting like 5000 light years. And I just had. A very difficult conversation with a junior engineer on my team about, like, hey. He put a 4600 IPR with, like, eight comments in it.

[Speaker 2]
We have a lot to talk about that, but what ended

[Speaker 1]
up happening was like, you know, and and his justification was the AI did it. Oh yeah. Point was, like, dude, it's okay, like, I understand. Yeah, I did it, but. You need to put garments. You need to tell AI to do smaller, iterative years. Because it's a nightmare for me to do.

4600 like here. Even if there are rate comets, it's like 600 800 lines a comment still harder. Um, but, but that's, that's the context blindness that we would be more and more exposed to as they are start doing more and more development.

[Speaker 3]
And, and that's why I, I don't think, and again, or take probably pass is not safe.

[Speaker 1]
And that simply means that, yeah, configured pipelines ran. Everything worked. But, well, guess what? I don't know if there was a major operational risk that we are tracking in in the release that you are trying to do, right? So?

[Speaker 3]
What is the generation shape?

[Speaker 1]
So, we need to now start thinking about the code logic, because more or less like, yeah, it's. If then else? Try, catch whatever. There's a Bayesian risk in inference that we need to considering multiple factors. Uh, we need to start thinking about the outcome where, uh? Like swapping the binary pass fail to something that is based on a risk score or a confidence score of.

Hey, this is the reason for why the confidence score is high or low, and we need explainability for it? And, and on top of that, we need like getting like specific rigid. Getting that existed in the past. We were like, hey, if the human doesn't? Like, have 80 coverage.

I'm going to fail the pipeline. Yeah, we don't want to get rid of it. Uh, but we want to have those in addition to being flexible where there are Dynamic. Kind of basic profiles.

Something that is, like, glorious. Is still okay if there are dark rails and then you determine why the lowest speed is okay to go. But if something is medium. We need someone to look at it. All you need to bake for some time, things like that, right. So, focusing on, uh, like?

How to evolve from this checkbox compliance to how we strategically think about respondigation? I think that's where this generationship needs to happen. The goal is not to have software governance. I think it's to have more precise government. It's more accurate or well. State probabilistic in nature, but get more closer to the risk assessment aspect of it, rather than saying a pass and a fail, will determine all the pipelines going.

So? To be thinking a lot about this and the entire framework is driven by the AI risk in search engine. Uh, my underlying understanding or thesis is. Uh, like machine learning models. Can. There is on an actual change. Uh, nice, manly, uh, to evaluate the bite app like it.

It happens to be sitting it, but to generate an accurate or close to accurate score, where the engine constantly ingests data. From like distinct signals, I mean, I I, there's four of them, but there could be n number of them. This is not exhausted by any means, so culture means, like, hey, how big of a change is it?

Uh, is the structural complexity of the code change, meaning. To give an example. If it's a honorable? I don't know. 700, 000 likes of food.

Uh, where you're affecting like three modules in a PR. In that case, you need to have some sort of nast graph of the change to identify if you are touching a node that's having like tens of dependencies or it's like a god. Function, or something which basically would break the other right.

You need to have the understanding and the complexity analysis of that while you are reviewing the code. Um, so you need to to take into consideration the code chain or the code aspect of, like, how is this change kind of been made? Uh, system health is another one, like.

If you're trying to make a change to a service that was deployed, but had an incident recently. Is this like going to add more to it? Was there, uh, memory contention issue, or was there some sort of an infra issue, or was, was there like a logic issue that got rolled back?

Some of these factors help with more curated insights into stability of the service, which then translates into some sort of risk score that we say, hey, be careful like as a human being when we would have an outage when we would have some sort of incident. You will definitely think of that, like, hey, this service broke.

Like, last week, I want to be sure, like, you know, my changes are not going to add more to it or something. I, I think you can't translate that into. Sort of logic, but you can base that on factors into some sort of a score. That kind of gets translated into the risk inference.

Um, other context is another one, like domain familiarity. Like, if I am a new developer on on the team or on a project? I might not have enough familiarity with all the aspects of the code. While AI tools helped me on board faster, understanding the flow, understanding that the logic and things like that.

But still, I'm not familiar with the code base as as innately as I would want to be. That becomes a factor again. It's not a red flag, but it's like a yellow flag saying, like, hey, this person doesn't have enough experience on the code base. So, let's be sure to put more rigor in the reviews, right?

Uh, additionally, you should be like, hey, this is a season developer. They do PR reviews. Their PRS have gone out like number of times. People have given very few comments on their reviews. That means they are like seasoned enough, and they know the score. Might the confidence score might be high as compared to someone who's branding?

Like file screens, like it checks if these files are kind of incident hotspots or. Uh, like, there are flaky tests that run on these files like, it's just another way of to think of, like, hey, this could cause issues, and then ultimately the risk inference engine could potentially give out like a confidence score or a risk score.

And along with that, we need an explanation on how is it kind of? Why is it related that? What is the main like? Driver of that risk. Like, uh, for example, let's say the portion gave it like 45%. Uh. Like, you know, plus 45 percent of risk, that means it found something that it thinks that this could cause issues.

Then, we need to translate that into human readable aspect of, like, yeah, I, I think this is higher risk because I was touching the art models, for example, right, or hey, this, like, there are like these lines of code that I have issues with? Like, I don't think this logic is better or covered in test or whatever.

That's the explainability that you need in order for us to be okay with the risk inference engine and the probabilistic nature of. So? Once we have the risk, like, how do you kind of balance the? Deployment frequency. You are the speed at which you want to least keeping it is out there.

And I came up with the feeling area. It's like. If the score is less than 20, which is the risk score, then you're not going to release it. It, like, oh sorry, you, you are going to release it because, well, uh. Guess what? This is your fast track Lane, like an express lane, uh, the like, you know?

It's a minor tweak. It's a dependency update or where the dependency update doesn't necessarily have any backward compatibility issue. It's a minor version of it. Small things right doesn't necessarily need. Heavy betting can be an automated Canary kind of deployment, ensuring that there are like Gates and auto rollback capabilities built in becomes fluorous.

Uh, a medium risk could be like, hey, this is your standard change. You are integrating a new API into your ecosystem. Uh, it has only test coverage. Everything seems good, but this is the first time you're integrating with the third party API. You have not seen the latency you're not seeing some of the non-functional aspects.

Maybe the risk is slightly higher than like, you know, slammed up, right? So then you basically like, hey, let's do a focus peer review. On this before it goes. And then it's good to work. The highest one is, again, the system Flags it, uh, saying, like, hey, this seems like a bar function, core authorization change, or some sort of a core capability that is very crucial for the application to run is getting changed.

With other factors like, you know, Junior developer doing it or something, like, uh oh, there was an incident, or like, some of the factors were like, you know, we see some hot spots. We want to have a deeper architectural review or the architectural review in in the agentic, world itself finds that, like, hey, this is not the convention that we've followed before.

This is a new pattern that you're introducing, or you're digressing from your architectural standards. Let's do a deeper, maybe in that aspect. It's like, you know, Canadian is fine, but would you want to kind of have like a soap time for this release where you deployed it with a human, always monitoring it.

And then, with the confidence you kind of move faster, like, you know, it rate a week versus now. Uh, so again like fast lanes are more or less like they're earned through trust and the risk inferences, but the the slower lanes are like, you know, the high risk Lanes basically are something that are to protect you from bad things to happen right.

And again, it's not going to be like, you know. Of, like, always right, and whatnot. But again, it's, it's the step towards having more grounded risk perspective on releases instead of. Uh, like, you know, just doing it with the past and okay? Um, so one of the patterns that I'm sure, like, you know, everyone said about predictive test, uh, selection.

And there are number of tools out there. Expensive model work that has happened on, like, hey, how do you find? The best is tests to learn in the smallest time possible to get the most, uh, you know, most most passive outcomes for releases? Uh, it is the same philosophy as such like, you know you.

The starting point is, like, right now. Uh, like, you know, full fluid regression runs painfully slow and expensive. So, let's try to optimize it like, you know, I don't have 45 to 60 minutes to spend on this full sea ice week. When I'm only touching one module, so I need to only run some things that are specific to that one, right?

And that's where, like, you know, models? Instead of running the whole Suite, the EI passes like, hey, these, this model got updated. These files have changed. These tests are impacted. Let me go run that. And, and then you, you run it. Um, while you still are expected to run end-to-end integration tasks.

Periodically to ensure the sanity of the regression Suite. But in the realm of the decision making, you are kind of still trusting like, you know, the model update, or the whatever the small change you're making is thoroughly tested? Uh, the outcome is you. You not only save time, but you save on compute.

You save on capacity that is needed to run the full suite versus, uh, the. The smaller subset of this? In this case, we are not kind of skipping the quality. We're just looking at the prioritizing signal of risk, right? This is like, again, um, I'm, I'm sure. Like, you know, a matter with a white paper or published a white paper on how ML based predictive tests are being used in meta for, like, you know, not only optimizing, but uh, also, like, you know, improved, uh?

Like regressions? Effectiveness. After the fact, when the change has gone up. Um, so how do you kind of do this like? I, I won't trust. There is inference engine right off the back, so it has to be a process where you're letting an AI model automatically route based on our our kind of, uh.

Like, trigger that we have put in. But then, how do you kind of? Just the the system that you are trying to eventually. Put your money on, so I I came up with this, uh? Four-Step process, where the foundational sequence is let the model run. Uh, watch you your system for.

A period of time few days, weeks, months. And then the next step. We start providing insights. To the user saying, like, hey, this would have been low risk and see if the user disagrees or agrees with it if the user disagrees. You put that as well back into the model to see why the user disabled.

And if the user agreed, but if it broke. Then, why did it break? And where do we need to tune? So it's, it's like the full feedback that needs to happen. You predict by analyzing the risk. Of, like, you know, an incoming change, and then we simulate the deployment phase by mapping out what Lane it's going to go.

And then we observe how the system is behaving when the human is in the loop, and then eventually it's going to start acting as like a co-pilot or someone who's just supplementing human inside with there is, uh, specification. And then, eventually, when we trust it enough. When we have seen enough iterations, we can then tune to kind of start using that as the primary and human being the second.

Um. And, and like, you know, again, confidence without a black box, I mean, any explainability at the core of this. We cannot have, uh, like, you know? And yeah, I say, like, yeah, this is Norris. Go, go do it, but we need every single generated risk. Uh, like, risk score we bought, uh?

Expose the Y of why it thinks that is the reason of whatever the risks were, but also the characteristics on which it invasing the risk. Why, what triggered it to Mark that as as like, low risk versus highest, like, we need to have explainability in? Uh, in the teams that that's governed, and it could be both sides.

It could be like it's flagging something that's very low risk as high risk, which then causes a lot of. Addition and reduce, and more time that is being spent versus, hey, it was not risk, but it actually should have been high risk. Um, and then the the hot flow here is like.

In regulatory compliance, open source license scanning secrets detection. There are any ways, like our deterministic rules, they need to be followed.

This is not fan option option. Ability to like, hey, whatever you are doing, doing the pipeline shifting left, like, scanning, and like, you know, doing, uh, like 150 checks and all that that still needs to happen. This is just. In addition to this now, the one question that keeps coming to my mind is.

How do we think this is going to kind of help with CV and music learning? Would, could this be a kind of a trigger towards like, hey, this is! This gives me confidence to be full CD versus a human in the loop approval. Manual reviews things like that, right?

Uh, and should this happen while the pi is in place versus post merge like, there are all these questions I have as well, but my my point was to bring them up. I would love to hear, uh, any thoughts people have? I'll take one minute to just show like a simulation of how this would eventually look like.

So, just give me one second.

So, I again, this is just a generated payload of like, you know, something that would get fed into the risk inference engine. In this case, it's. Like, you know, it's it's this author.py. And then, uh, the domain familiarity score is 0.44. Past access rate is 0.6, meaning there's some issue in the past.

The cyclomatic complexity is 2.56. Now, these are again. These are all calculated Upstream, meaning there are different models calculating these scores, and then that is what is getting injected in the risk inference engine, and then it kind of says, like, hey, I is hundred percent. Well, uh. A bad example, probably, but nevertheless, like, you know, you have the event flow, which takes the event, and then the context manager kind of envisses the context.

The inference engine provide like passes the four signals that we, uh, put in, and then the router kind of routes to the IRS, and then here's the the Baseline like, you know, the Baseline risk before routing signals are applied. The culture. Like, you know, 120 lines change, but it was touching that Arts.

Py added, like, you know, 25? Um, the system is because there was a. Clinical environment with three open incidents in the last several days. Um, and that kind of visited in, like all of these kind of, resulted in. Like that is called being. And then, like how scores are built.

So, just something to kind of look at? The domain familiarity. The past access rate change lines like this. This is, this is just something conceptual at this point, but this can easily, uh, be integrated into, uh, into our models, and so on and so forth, but I think I have 2 minutes so.

Thank you so much.