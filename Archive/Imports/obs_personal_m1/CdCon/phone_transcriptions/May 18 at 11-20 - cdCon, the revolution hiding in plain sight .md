---
type: transcript
topic: work
---


Hello, everybody! It's very nice to see you guys! Thank you so much for coming off today! Um, I just want to take a moment and thank Tracy Reagan and the program committee.

[Speaker 1]
For everything they did. If you looked at our schedule this year, it's amazing. You guys did a wonderful job of selecting everything, and I just want to thank you so much on behalf of CDOS and the entire Community, right? Love what I handle Applause for our professionals?

So before I get into my talk? Is it? Is it going to let me get asked by top?

[Speaker 2]
All right, cool.

[Speaker 1]
Before I get into the talk guys, I got a quick question. Is, is anybody in this room not know where to build this? Like, raise your hand if you don't know where it goes. All right, cool, just checking all right. Um, can anyone tell me what this is? Yeah, okay, awesome, so you got one large?

Yeah, now what if I were to call it a Taza? Would I be wrong? No pause on it.

Right?

[Speaker 3]
Two words. One thing, okay, built. Everyone knows what a build is, but um, who can tell me what a build is? Anyone? Well, just tell me what a build is in your opinion. Sir, region of Artisans, all right. Awesome, anybody got a different answer? Awesome. So we have build that has more than one meeting.

An object that has two words.

[Speaker 1]
So, that's what the revolution is based on. That's, that's what we're going to be talking about today, um. So?

All right. So? What if you've already stated what the problem is? What have you've already said it? What of the work that we're doing all the integration work? The blue code that just one more web hook? To link systems. What if we wanted to look at that problem that we've been looking at, over and over again and figure out why we just have to do it.

Why doesn't this language hear us? I'm not here today to teach you something new. I want to just show you what we've already know what we've already built. And show you that some of the things that we do. We can just say once and move that forward. Your tools are connected.

I'm going to be honest with you. You already know that. Um, if you work at any reasonable size organization. Like, you probably already have give help talking to Jenkins, um? Talking to jira, talking to slack, talking to data dog? Everything's connected, right? Everything's integrated. We already have this. It's already done.

So, let me ask you a question. Why does it feel like that?

So? That's not the real problem. But connection itself. It is an understanding all right, you

[Speaker 3]
can wire two things together. They'll pass messages back and forth back and forth, but they never really understand what those messages mean.

Here's a test. Okay. Raise your hand. If you've ever had a build feel?

[Speaker 1]
And the downstream system. Did the deployment anyway? Anybody? Now, in that case, did the build system not try to say I failed? They did not know it failed. Or did the deployment system not understand the signal? How do we handle this?

[Speaker 3]
So?

All right, sorry. I trimmed some of this into the back.

[Speaker 1]
Different systems, same shape. Uh, those systems were connected. The build system knew that it failed. The signal was admitted, and the deployment system still deployed.

Because this deployment system failed in the moment, it's our string. It didn't understand the message, the problem, the connection, the meaning doesn't transfer to signal doesn't transfer. The receiver has the information that reconstructs that signal, and in that moment, the receiver itself cannot construct it in a manner that it completely understands.

It works on assumptions. It works on the idea of its own schema, not the schema shared across the systems.

I have a word for this, and technically it's not my word. It's Brett Smith's word, um, if you guys have read, he's an amazing guy! Bye bye, uh, we call it configuration and configuration is a state where two systems or two people will leave their wide, but they're depositive.

They're both operating on the assumption. That they're sharing the same signal, and they understand what it means. They reach different coordinates. They reach different assumptions and ideas of what's going on, and that makes it dangerous. You can't monitor for it. You can't. Okay, uh, program against this. Is there?

Consistence cannot share the same interpretation of the same area, probably going to happen.

So, how do we escape configuration? He's tasked, right? Well, we all know that. You test twice. First, you assert, you say what you mean? You know?

You know, say what you intended, stain it. The harder it sounds. Oh sorry, this is harder than it sounds. Retrained to believe that we should be quick that we should be nibble, but we need to take that moment to understand the real problems that are going on. We only do that when we assert what we intend to.

[Speaker 3]
Second reflect.

[Speaker 1]
Saying what you heard? Make sure that you understood what is going on, right? Take that moment to have that communication connect. Take the moment to be sure that both parties understand what's happening. Only then are we dealing with configuration. This is the protocol. There's no other way around it.

Then, once you confirm if it's yes. You go back. Right, you move forward to store it. If it's no, you go back and try again. Clear up the understanding before it happens. So, how do we do this within our own systems? How do we store in a way that something that both parties are committed to after we've taken the time to do this movement?

This is our protocol. This is how to build shared systems with meaning that transfers automatically. This isn't a software pattern. This is how trust works. This is some contracts for. This is how teaching works. This is how conversations work when they work. And this is how AI should work with your tools.

But we haven't given the infrastructure to do this until now. So? Step one. Serious. You've probably heard of it. It's a CDF specification. It defines a common vocabulary and sdlc. Build started test finish, test passed artifacts, published service deployed. That's it, it's all it does, it says. When something happens in your pipeline, here's how to describe it so that every other system can understand it.

Now! And react. Not what to do next. Just what happened when to what? Think about that. Before sea events. If you wanted Jenkins to talk to Argo CD? You would have to understand the Jenkins API. Have to understand how our CD works, right? Complete that one.

[Speaker 3]
But with City events, we have one standard of communication that every tool can understand. That's the difference. That's the separator for AI. You begin to normalize that conviction. And show. What you're in 10 plus? So the city events part. It's already done. The spec exists, the tools are adopting it.

Jenkins has a CD events plug-in. Kept on ability events. I know that Spinnaker is in motion is the one spinner TSD. Um, you know? I'm sure, Captain. I've seen that using CD events. Uh, the other one. I'm not sure about zargo seated, but? We can get that more together.

Step one is complete. Vocabulary. What happened the wind? The what? Same words, same structure. Everyone agrees on the framing. But vocabulary isn't meaning. As I said before, cuppentaza are the same thing build and build, sometimes not the same thing.

[Speaker 1]
Same thing.

[Speaker 3]
Build and build. Not the same thing.

When you say build? Evening that the CI job in political? The artifact that came out of it. Reactive, constructive image.

[Speaker 1]
Or maybe the whole pipeline that does the whole thing? You know? What it means when you say it? I don't. Doesn't. And that's a challenge. Like, how do we get all the build all the Downstream systems to understand? Build startup.

[Speaker 3]
In the lower portion of the slide, both expresses. All the events listed. This is a citrus expression.

[Speaker 1]
Celtic expressions solve this problem. Take a look at the bottom. We have two build deploys. One is maybe chance. And the other is the spin deputies. You have completely different steps. But they are both. Bill deploy. Four events change created. That's the pr build started, build finished, and service deployed.

Lean past a solo developer shipping. The spin up team, seven of us change merge not created. Um, build, started test Suite started and finished. Bill finished, service deployed, and then service published. It's ready to do work. A step. Maggie Chad doesn't happen. Same word, different patterns. But if you just said build deploy, both teams would not.

They think you understand each other. Congratulations, but now look real proof.

It's the expression that makes the difference. You don't have to ask what this build deploy mean you can see it. It's expression. It's Scotch script. It's not a pipeline definition. It's a declaration of intent. It says this pattern, I expected to see these events used in this order produce a specific outcome.

The events and?

[Speaker 3]
Oh, sorry, and that outcome you receive as a receipt. A receipt for work that's already done. Verified completed. Now! With just the coupling. Of an identity. Now you have a complete cycle right here right now.

Here's a mind-blowing part. An expression is the expected future path. You write it before anything happens. You say, this is what will have happened as the workflow runs. Saying.

Saying what it did, and the expression fills up.

Now, as you can see, I'm starting to check off the expressions that would actually happen. Um, just so that you guys can get a sense for what actually happens if this progresses along. And you'll notice that as they move forward, they're fill it up. Here's what I need you to understand.

The humans uses always. The AI doesn't decide what the pipeline should do you. Do you declare the outcome? The AI's job is to understand what you declare and match it to reality. It will tell you when it's done. And when it's going to happen. The UI is not the author.

You are the I is the reader very good. Very fast, very attentive reader who can hold this entire structure in memory. And let you know when something's about to go straight? And because this is declarative, you can begin to put in resolve resolutions or the issues that you expect to see.

This matters. This time is a lot. The human is still the author of intent. You're not automating the weight adjustment. You're not, you're just encoding the Judgment. Uniform that process. In the form that can be versioned. In a form that the AI can read.

So? Hey, hi. What if your future was declared?

[Speaker 1]
Yeah, I can reason. It doesn't have to simulate. A 400 line Jenkins file to guess what happens next. It reads your expression. It sees the pattern. It knows what you intended. It watches and ratches and fulfills. Look at those two expressions. Say word Bill deploy? Different events, different teams, different contacts, both fulfilled.

Together. Because I didn't have to understand the differences in philosophy between Maggie and the spin duck team. It just needed to see the pattern in that reality against it. Sequential impaired systems are opaque to AI.

[Speaker 3]
To do this,

[Speaker 1]
an AI machine would have to simulate a state machine. Declare outcomes are transparent.

So? What's happening is the AI can read this once and hold the pattern. It batches the event complexity constant. The expression is prediction. The difference. That's everything.

[Speaker 3]
Will

[Speaker 1]
it expression fulfills when reality matches the declared intention? What happens actually happens? But not scripted. Actions not run this shell command actions as functions. I mean, after all, you guys get it. This is going to be a pub sub, right?

We standardize our functions. We make them tool agnostic. The functions don't care what systems are connected to the functions, just work. Gracefully or? Until you're ready for it.

Notify Channel. Not close to slack, not send teams messages. Nots in the Discord notify Channel. Which channel? It doesn't matter, you have slack. Since the plot you have teams, it goes to teams. But config decides. The function is a contract. The tool and the implementation detail. Think about what this means for the code that you write.

Today. If you want to notify your team of deployment completes, you write a slack API. You learn the slack SDK? You have those locks off? You manage slacks rate limits. Your code is buried to slot. Next year, the company acquires a startup and they use teams. Now you have two notification systems.

Your slot code doesn't work for them. You write the team's code. You write the attraction layer. Microservices handled up.

Now, with the notify channel on the first day of the acquisition, just drop it in because it's CD events power the information coming out of that is already standardized and already works. Same code, same behavior, different tools. That's freedom.

Previous change.

[Speaker 3]
This is what it means to build interoperable interoperability from the start to versus startup.

[Speaker 1]
All right, so look my channel. They have a slackboard space. The function Works six months later. Yeah, customer service team. That means teams. It still works. You install the tools systems, these adapters, the function Works two years later. It could be a 200 person team. They could have, um, slack notification.

You know, Discord all kinds of things they'll just work.

[Speaker 3]
And if a function doesn't exist yet,

[Speaker 1]
if they call something that hasn't connected the function not implemented, not an error, not a crass, not a pipeline field because you're too small and fixer.

[Speaker 3]
This is important. This is economic.

[Speaker 1]
Your future scale. Your code doesn't have to. That's the stack. It's the Vince, what happens, the vocabulary, the expression, what was intended, the grammar, the functions, what to do? The actions. You decide. You're building this? For your future. In a thousand different ways and a thousand different tools, a thousand different blue Scripts.

You've been saying what you wanted? The infrastructure wasn't listening. Now, he listens.

Think about the last time. She wanted. Cii system or a deployment platform at AI system to understand something and it just? Not because you couldn't execute, not because it could execute it, just didn't know what you mean. And since I've been using I, I noticed that one thing that happens to me over and over again.

I'll give AI really simple commands, and it just doesn't understand what to do. But if we declare what we expect to be done, we give it the expected information. This changes the outcome. It better understands what to do because it's matching the context of what happens. To watch you about.

[Speaker 3]
You lost that last screen. Oh yeah, no, it was, yeah, that was, okay, it was. It was supposed to be a dramatic effect. You already know what you want?

[Speaker 1]
You've always done. The only question is, are you going to keep translating yourself into 100 different languages? Um and.

And I've got like four more slots. Would you guys like to see what we built? Yeah, okay, all right. So, is that up there? Okay. So? This is the basic system right, and it uses CD event. Um, I'm giving another talk tomorrow guys, and in that talk, I was supposed to be the policies.

I actually have a live demo of this system, and so instead of doing that talk, if Tracy doesn't mind. I will show the live system so people can see how it works and connects. So, just look for my talk tomorrow, and uh, whatever slot that is in. Come on back, or we can talk at some point, you know, outside?

We're happy to walk you through the system of actually working. It's really the semantics. Uh, the expression is what handles the complexity of choice

[Speaker 3]
right. And so, now, from

[Speaker 1]
one single point and I should probably mention that this drawing will go out of date. Um, something like that. So, a couple of weeks ago? As things happen in. A couple of weeks ago, this Force comment wasn't in existence. And, of course, being the programs that we are over the weekend, we filled all this in, so all of this is available.

If you're going to see the whole stack and how we move events in systems, but one of the things that's most important that got like nailed this in my apply last students. Is that? Now you can talk to your entire company at once, based on the data that they expect their individual.

And that's the biggest threat of the system.

Trying to respect everybody's time. Get involved. Come out and see me see Candace in the back. Okay. Because when you see what it can do. Um, just waiting for an event to happen. It's very odd because you don't have to plug your compliance teams anymore anymore. They can just subscribe to Katie's employment your entire organization

[Speaker 4]
and get the information they all at once

[Speaker 1]
just automatically as is happening. Um, it will be very, very, very, very strong interpretation because it just uses the CD events and Citrus expressions. To communicate pipeline structure in advance so that tools just drop in and move forward. Thank you so much for your time!