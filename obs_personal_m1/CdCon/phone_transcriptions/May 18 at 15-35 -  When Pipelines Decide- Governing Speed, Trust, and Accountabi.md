---
type: transcript
topic: work
---


The guidelines they developed in terms of dealing with pipelines in a world of AI and AI making choices.

Go ahead.

[Speaker 1]
Good afternoon, everyone for more than a decade. The software industry optimize relentlessly for Speed. Fast deployments. Faster automation, shorter delivery times, and continued in the scale. And the transformation fundamentally changed how software is built and operated. But something else is now happening beneath the surface. Increasingly. The beginning to participate in operational decisions.

[Speaker 2]
So, for the positive here, software has been mostly about executing the instructions. But now, they're taking care of operational decisions. Um, and that creates an entirely new challenge for engineering organizations. Because. One systems began making decisions. The problem is no longer an automation alone. The problem becomes governance. How do we maintain control?

Accountability and trust in systems that can increasingly act autonomously. I'm Sandeep Papa. I work as tackling Cloud devops engineer for Southwest Airlines. And joining me is.

[Speaker 1]
Who brings deep expertise in Cloud security and governance from leading organizations? Together, we want to explore what happens when pipelines stop being execution engines and start becoming operational Edition Frameworks. So, your pipeline no longer waits for you. Few years ago, CD pipelines would like to be deterministic systems. You define explicit Works, workflows runnable, run a test, deploy the release, and run a smoke test.

Pipeline executed. What exactly humans resigning to do? Operational decisions still remain largely external to the system itself. But modern development environments are evolving rapidly. Today. Delivery systems increasingly evaluate runtime Telemetry in real time. So, you are producing billions of rocks every minute, and then the decisions are based on the on the locks itself.

Um. They correlate deployment Health signals. Suppressing transient failures, adjust rollout Behavior dynamically, and promoting bills from one environment to another automatically. And what happens when something goes wrong? Trigger roll back and remediation workflows. Based on life operating conditions. Not based on? Predeterministic rules that humans work. And the change is the operation model entirely.

Because. The pipeline is no longer functioning only as execution mechanism. It is functioning as. Um, influencing system behavior directly. At the same time, engineering organizations still optimize around some same core operational metrics. Meantime, recovery deployment, frequency change, failure rate. Andel rivenos. Those metrics still drive business value. But now Kia is helping to compress the operational latency behind them.

Analysis, validation, decision making. And previously required significant human. Effort. It is increasingly happened in real time with AI. And that compression fundamentally changes how software delivery systems behave under continuous change. Uh, the shift speed has always been the goal. Now, it has a co-pilot. First, uh, the combination realistics and intersects intersection of three, four forces speed control and accountability.

First, the speed, as I mentioned before. A compress operational analysis and radiation Cycles dramatically. Analysis that once required human walkthroughs. Several thousands of rocks, metrics, and events. Can now happen in seconds. Validation process increasingly use runtime Telemetry. And remediation workflows previously dependent on Engineers assembling. Uh, incident context. How many incidents are there?

What is what each incident did, and how did someone resolve it? Is all automated, more adaptive as well, and second control policies. So, who we have used Opa policies in their pipelines? Hi, Scott, um. Yeah, Boba policies policies, uh? It implies as confidence thresholds and candle gets defined operational boundaries.

[Speaker 2]
I'm doubt

[Speaker 1]
accountability. This is the most important topic of this talk. Even when execution becomes autonomous, accountability remains humans. Now, you have AI one of your pipelines making decisions. To deploy something into production. And something went wrong in the production, and we decided to go back now.

Is it a? No, it's human who built the agent? So, when Asian pullbacks at 2 am, human owns the outcome. And how do you own that outcome? Uh, by developing control pins. Human is still at the Forefront when it comes to production deployments and making any decisions. Then, ensuring both simultaneously.

How does a pipeline actually looks now? So you have you have pipelines that executed bills? Use Maven Gradle to build artifacts, then to run tests using selenia. And then, uh.

And how pipeline is actually changing with AI, so the core components are layer autonomy. An operational autonomy expands progressively across lower scandals, so you can always take a risk, right? You are deploying something in Dev environment, so nothing is impacted. Customers are not affected, so you could. You could use AI as a strict analysis.

Uh, policy enforcement camera deployment. Uh, in the layer economy. Agents operate more freely and lower risk environments because of the because of the reason risk is low. And signed audit Trail, so every autonomous position that AI agents are making part of the pipeline are signed. By using an old tray, an audit Trail that you can reference, you can use it for your compliance Frameworks.

Um, and I'm confident gated. Get actions from uncertainty increases. Agents escalates rather than improvise. The goal is in promoting humans. It's reducing operational noise while preserving governance. So, the floor looks like someone committing and creating a PR. Um. Agent automatically adds a card, adds adds a comment in the Mr, and once the comments are addressed by human.

[Speaker 2]
Until now, we just use pipelines to measure coverage. Now, air agents will look at your coverage. And read the features that you have added and adds those test cases for you. And then run those test cases, part of the same pipeline. And then policy Gates. Open policy Gates helps you write the policies.

And then finally can be deployed. And right, at the moment when you are going to deploy the production. That's where you make human approval, and we're in a safe state because we have OPA policies that is guarding all rails like. Uh, all the quadrants are in place. Constraints that let agents more safely.

So, one is policy has code using Reger. You can write over policies version control alongside your application. Um, and an agent evaluates them at runtime, and policy changes go through PR review, not tickets. This brings a privileged execution. Each python agent gets its own scope ion role. So today, how your pipeline looks like every pipeline will have same access.

Um, uses the same robotic ID to run the pipeline. So, when agent is making decisions, each agent will have its own IM role so we can maintain the audit rail. And no self-escalation. An agent that deploys cannot modify its own policy doesn't have powers beyond what you gave it.

Last previous caps, so you can always set caps. What agents could do? Example, Max. Five percent of the fleet Max. 10 percent traffic ship in some of the decisions. You could let the agents make. Fail loud, not silent, so low confidence decisions. Do not Auto proceed or silently Escape.

And score the score, the rest, and take a recommended action. This is where security, accountability, and operational governance. Become fundamental parts of the delivery system itself. With that, I am going to hand over Mada. She'd walk in through the governments and security side of autonomous children. So? Hello everyone, every organization adopting autonomous delivery needs a clear ownership Matrix, which is like defining an agent.

What it has to do when it can escalate and? What decisions it can take and where the human in the loop is exactly needed. Uh, so for example, agents May retry failures automatically pause deployments or roll back on healthy canaries, so, but we have to be really careful how the production wide upwards and security exceptions.

They minor human decisions, so the keying principle here is simple Define ownership before the audition or during the post model. So, one of the biggest shifts that is happening today is the security is no longer an afterthought in the industries. So, it is being Blended in every stage of the pipeline, which is good.

[Speaker 1]
Just so, like, we are, you know, today, in a situation that, like, from the organizations thinking that, why do we even need a security team to we can develop and build the agents securely, so that's a proud moment. Today, further security Engineers. Patterns for the teams to take away here from this talk is map the autonomous actions already happening in your pipeline.

Today, most organizations discover they already have more operational autonomy than they have realized. But like, they don't realize what happens when an Asian Bridge happens that, like autonomously, taking its own decisions, aggressively processing the commands and doing the things which it doesn't have to write. So, that is a scary part.

And finally, uh, so these These are not the future state of concert anymore, but they are rapidly becoming fundamental operational requirements today. So, at the end of the day, the challenge is not simply building faster delivery systems, but it's building all the resistance team organizations like famous. So? So?

Out my security research and the current attach credits and defenses that are happening. And I will hand over to summit now. Forever announcement on a degrees. All right. Thanks everyone. So these are, uh, profiles. Feel free to connect, uh, like Nara said. She posts regularly on security. I post regularly on.

[Speaker 2]
So I can. I work as an adoptions here. All my life? Um, so I started this newsletter to share my insights on on the happenings in the market, so you all can follow along. So today, we're going to take this opportunity to. To reveal an upcoming book. Um, so Mania, so these books, uh, this book follow along the same topic that we have discussed today.

So, it explores how cicd can be used as a control system rather than just running, uh, billing and billing and testing and deploying the artifacts. So cookies in production state. It's not available in the market yet, but yeah, keep an eye. Thanks everyone! What are you doing a self-restrialance right now to manage?

The AI applications. You know how? Are you doing anything to version? Llms, are you doing anything to manage prompts? If that is, that discussion started at all in terms of adding something into the pipeline that helps student helps that process. Yes, we hadn't. We haven't expected one because of our AI and AI governments.

[Speaker 1]
Us and the automation part is like, we have built a custom control player, the control plane that is located like the actions right from someone is proposing an agent to what, what actions does it execute to? What vulnerabilities that it has? Um, so a control panel helps us to go through and do all the check marks before finally going on the agent.

[Speaker 2]
But no tooling yet specifically

[Speaker 1]
in that in the pipeline itself in the pipeline. Like, currently, we are using over policies. Um, that's a gig, and we have some custom build agents that we are admitted part of the pipeline. We are like big hero zero users, so we have built so many agents that are part of pipeline, like the checks for multiple companies.

Get on, rolls back introduction, not yet. But what's your question about AI? How do you roll back then? Oh well.

[Speaker 2]
I think I think that's right. That's that's evolving phase. We're still exposing who are exploring what is right. Like, you know, I work in an application. That is a cash register for Southwest, so you know, still, can't experiment that?

[Speaker 1]
Um, yeah, so you were explaining this process of how your?

[Speaker 3]
Uh, Engineers are helped by AI as they go through the submission of code that the AI suggests test. For them, you know, to expand that. So my question is, why are you not injecting that at the beginning of the process to have acceptance tests for the features that you're about to apply?

[Speaker 1]
Yeah, we do have agents. Um, the developers can use before they check in the code. They still have that opportunity,

[Speaker 4]
and the clients are making sure, yeah, in the

[Speaker 5]
planning phase. When you're planning the feature, you have the AI say. Here are the tests that, should you know, you've already got it in your code base, right? And

[Speaker 1]
if you

[Speaker 5]
know what the feature is, and you're talking about it and you're planning out the features and you're at the table. Where are you like? Are there plans to use that in more of a tdd fashion where you're saying like, here are the tests that are the acceptance tests just.

Free start to open up that conversation and to build that. You know, graph of like, what's happening as you bring it through the process? That's my question, yeah. So

[Speaker 1]
the process is always shifted left, so the agents are writing the tests right right before they check in the code. Okay, but the process I mentioned part of the pipeline is ensure in that there is 100 touch coverage, and AI is fitting any gaps like you can build agent

[Speaker 4]
right? You can tell a human hey, use area agent to write. Write your test cases,

[Speaker 1]
right? But how do you make sure?

[Speaker 4]
So if

[Speaker 1]
I the agent in the pipeline is making sure it is engineering?

[Speaker 3]
Okay, just to

[Speaker 1]
fill all the gaps.

[Speaker 3]
Yeah, but it's filling the gaps, but it's not filling it up front before they start writing the code. Yeah, here's the thing. That's what I'm trying to get. Okay, all right.

[Speaker 4]
But so I, in uni, I studied the control system work as a theory of women hearing, and I just looked up that this details are doing, and he, the website explains that in this book, we actually died deep into.

[Speaker 1]
So we have we have taken just just normal control groups. Yeah, as an example combined with cicd, and then we do, right? It's an experiment, so really looking forward for the feedback. Thank you for the acknowledging that, yeah. You mentioned that you're

[Speaker 5]
having AI, right, like unit tests and stuff, or go through the test cases. How do you make sure that you can trust its test, because I guess when, when I was trained with coding and stuff, the test is meant to capture error on whoever's coding. So, in this case, the agent, if the agent's doing both, how do you make sure the tests are good?

Does that make sense? Yeah.

[Speaker 1]
Like in a development workflow. If a user install a big feature and then the feature feature, pipeline grants and AI agent adds the test cases, you still have to create an Mr and go through the Mr processor. Okay, that makes sense. Okay, I appreciate it.

[Speaker 2]
All right. Thank you.