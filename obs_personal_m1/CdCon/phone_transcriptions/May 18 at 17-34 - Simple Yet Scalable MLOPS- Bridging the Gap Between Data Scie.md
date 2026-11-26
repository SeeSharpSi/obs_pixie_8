---
type: transcript
topic: work
---


Ops without actually using.

[Speaker 1]
All right startup from first principles without really using all the other tools. The fancy stuff which has a place in the industry, but if you're just starting out, you want to get it into the system, trying to build simpler models without getting logged into a ecosystem generated do not know anything off initially, so that's all sort of, and this is something that has been battled hardened, which we actually been tested out in production.

And now, Financial Services organization in India. So that's what we will be talking about about how to go about it. Um, so I'm sure every single developer has had the experience. Oh, but it works on my machine. Um, and that amazing production. And ml is definitely no exception, because code can change training.

Data can change.

[Speaker 2]
Um, a runtime environments change, and sometimes it's not really easy. What exactly did they even deploy? Um, traditional devboxes that chicken code, but ml systems, you know, they ship more than code. You have to actually the code, the actual data Behavior, and that's why ml needs a cicd approach that focuses on weaker disability, and not just um.

Um, so what is ML Ops, uh? For people that may not be as familiar, um, it's basically just devops adapted from machine learning, and it connects. It's the link between data scientists and operations and infrastructure teams, because data scientists care about the experiments features the metrics and model quality, different infrastructure, Community care, more about um reliability and scaling monitoring.

Monitoring and production and rolling back if something goes wrong. There are a lot of tools that work on this as we talked about, so I'm also is open source. It's pretty good for, like, experimental tracking. Um. As per tracking model versions and metrics, modelingage and stuff, and then you have, you know, Google, Amazon, um, Microsoft, you make their things?

And the advantage of the platforms is definitely, you know? They provide the convenience and that manage the infrastructure. Um, and they can be very useful for teams, but if you're just starting out, you know, maybe playing around? They can also introduce complexity, and then you're basically locked into that one vendor of that platform, right?

Um. So, our proposal is to focus on a similar approach that uses get DVC Docker. Kubernetes. Um, not to replace the platform, but to start with something that's simple and portable, and then can be built upon you.

[Speaker 1]
So, this is the sort of the architecture that we're talking about here. So, we have a developer who will be committing some code. Or some new amount of data. And we are, we are talking about two distinct angles. One is code is in a version control system, like git.

Or whatever. I perform on curial, but don't people don't. So I have. So, and then the data is actually in something, which is a data version control, which is a company with DBC, which is a company which has been called International or AI. They have recently bought it. It's an open source tool, but lay cafes, the people who make lay cafes are also part of the and bought over the DVC DVC essentially.

Is of a way of? Storing the metadata associated with the data under version control while keeping the data outside the version control thing. We know that version control has this huge problem that most Pollution Control Systems are basically designed for text data. They are designed to student as effectively.

They do the Delta thing. You can compress the data as you store it, but when you go to and store binary blobs every blob, even if one bit differs. You don't really know where it is, so you have to store the entire data over and over again, which is a lot of overhead for Version Control Systems.

For example, when I was trying to do some version controls of PDF files. In my Mercury, I used to say that this file will take 500 MD of something of memory to gram to manage. I mean, which was the craziest automation. So, if I have to store documents, I actually don't store the PDS anymore.

I store the text latex talk the text keep that version controlled along with whatever it is so. So, this is where we use DVC to put the version controls. The idea is that you build a model. You store the artifacts in a in the bucket there.

[Speaker 3]
In this, uh, repository, which is there?

[Speaker 1]
This is the data market. It could be S3. It could be any other object store. It could be an FS filer also, whatever it is, and then make it require. The model will be pulled and built. Then we'll bake the model in the in the docker container. This is where we'll essentially ensure that our entire thing is reproducible, whether the Docker container.

Uh, with the model bank came, and then this model can be deployed in a container repository also directly deployed. The key angle here is that we are basically whenever we are doing. We are keeping the port separate as well as the data set rate. Every.

Every model is trained on some particular angle about amount of data. If the data is changed, the model drift happens. What you said distribution get brift, right? So new data is coming in. Your models need to change. Your models will get wrong, so you need to pull them out of production.

You need to retrain a model, but you are not really sure whether the new model works. And for that purpose, we have also proposing that we do a. Blue clean sort of a deployment. So this is about how DBC works. Just just go back to a DBC here. So, the TBC works.

You basically within PVC. You have a there's a pickle file, which is the model file, which contains everything the 500 MP is just an example thing, but if you just store the metadata associated within the hash, what is the file locations and all of that stuff, so that the next time when you're trying to pull it, you will can go to the source and re download it, which again, if you go to the previous one, that same information can we can store it on our local bucket or whatever it is.

All the data sets and all that. They ensure that they are version control. Yeah, yeah. So, this is where we are talking about, uh, same thing, but instead of saying that PNF model drift happens, we talk about a blueprint deployment. So, we build a new model. The blue model, the Blue Lake.

There is the model, which is.

So, the blue one is what have been currently in production. We have got a load balancer here, which basically takes the data. So, if we are not, don't have a new model, everything is going to. Uh, do? Model and everything is fine, but when we have a new model which is being built where the docker container and the container repository, we push it out into production, another environment, and then using whatever tool we can actually do.

A 1090 rule, then person goes to the new one. 90 percent goes to the old. One continues to, or you get to a complete hundred percent, switch at all, depends upon the how critical you think this serve product is for services. If it, if your financial service and organization you will actually do very, very, very?

Service Health.

[Speaker 2]
With like availability and AI behavior, but also model monitoring. So this is what he was talking about with distribution shows. We actually have to track metrics that are common in MLM. You might be familiar with like accuracy and position recall when we have the ground truth available, um. So, like, in case of like, say, a classifier we might not know the correct label immediately, but like, once we have that data, we can compare our predictions, um, and look at our actual outcomes.

And if we observe drift, so if our model Behavior deviates from what we had originally expected, um, and deployed into production. We know that something has changed, um, whether it's maybe the data has changed. Like, maybe, um, the customer Behavior changes, um? Or maybe there's a problem with the model where it suddenly starts predicting maybe like greater percentage of cases as something like high risk, and like, fall detection, we know that B should roll back.

Go back to go back, um, like, change our load balancer. Go back to our old environment and then rework our model. Quick question is is the blue green also considered how you can set up a shadow?

[Speaker 1]
A point of thing. We have not looked at this from the point of an llms. We're likely talking about systems, which are deterministic enough. Oh, okay, because llms actually require a very, very different evaluation methodology, which. Which we do not know yet. I mean, so she is studying, so she might be able to tell exactly what it is, but uh, but can you

[Speaker 3]
explain more about what you mean by the shadow weather, uh, well, with your gold per answer a shadows and input to two places, so you have the primary. Yeah, I, I

[Speaker 1]
think I think that's a similar idea where you can do it, but for if you haven't really talked about this on the perspective of another, because evaluating llms is a different thing where we really do. But if let's say it's a regression model where we are doing what tracking normal, it's much more simpler to understand that this one was abroad than anything, or if you are doing some other sort of classification and dog cat problem, and dogs are being so those sort of scenario.

But yeah, that's what is the shadow signal? Okay, so we can, actually. I mean, we are talking about load balancer. Here, you can balance it. Or, you could actually also say that both things can go concurrently, right, right? Like, uh, if if you remember the old tandem systems they used to do lock star things to ensure?

Everything is reliable enough and the voting and all that stuff. I think we can build that sort of a mechanical. Also, got it.

[Speaker 3]
Thank you.

[Speaker 1]
This is just an example of what a blue green deployment is that. It comes through a lower balancing, so it can actually say a copy. You can send package board.

So, yeah, so our main takeaway was, I don't think it has to be very complex to at least start out with scalable envelops, um, um, um.

[Speaker 2]
But there's a few things to remember. We'll see that models are not just code. We really need to keep track of the data that the model is trained on, because that really does affect model Behavior, of course. Um, and that models should be Deployable artifacts. We can't just say, you know, it works on my machine.

It was giving me so, and so I'll put on my machine, make it into a consistent container with a consistent runtime. And then deploy it, um? And then we also. Need to keep testing, observing, and monitoring and keeping a human in the loop where needed. Just to watch out for things like distribution shift.

Um. And I think.

[Speaker 1]
Um, yeah, and I think we need to follow the units. We keep it simple. There are too much complexity has come into the into the entire ecosystem. I mean, my bad previous system deal with X was doing for another time,

[Speaker 2]
but

[Speaker 3]
but they need to actually go back to the basics and try to get these things why we are doing what we are doing and try to.

[Speaker 1]
I mean, a lot of time we are rebuilding scaffolding. Everybody is just rebuilding all this scaffolding again and again and again. I think we don't need to rebuild it every time. So? And then keep it simple, stupid. Naturally, there you go. Yeah, all right. This is a wish to connect with us.

[Speaker 3]
Did you get back to the last song? So get DVC Docker, uh, what does GVC represent in that? Give

[Speaker 1]
me the it's a data Version Control. Yeah, so I

[Speaker 3]
ran into this with my systems and a bunch of my mlx. Teams were like, we want to use DVC, and I'm like, wait, you're going to add yet another attack Vector into my pipeline. We can just use get lfs and you can store your stuff and you get your versioning out of git and then get lfs stores.

The model in artifactory or or?

[Speaker 1]
You're right about that, but I honestly did not really look at git elephants because one last thing when I looked at git LFS, it seemed to be a bit too complex, but I, I think that is a, I mean, you, I, I mean, mileage varies. You may be right on that, and I'm not going to because it SFS is actually supposed to be exactly for the same sort of purpose.

Yes, in our mind is less complicated than DVC, which is just another layer on top of here. Yeah, it provides a lot of the same functional.

[Speaker 3]
Yeah, I, I. When you go back, look at, get off. That's now I will say this. It's got its problems. I mean, it is the NFS of the get world, but if you get it set up, right? We haven't set up, right? It works 99 of the time, and I don't have any other system and

[Speaker 1]
look and take a look at it because the last time I looked at bitlfs. It was likely for somebody who said that I'm backing up the stuff on pen drives and the people do. It is, yeah, was the truth. That's how I got. But I think the conceptually there it's all similar.

What you're saying is, instead of using a separate thing, just use the example, right?

[Speaker 3]
A joke perfectly. Similarly, what about Lake FS? That's just simply on top of your object store and using git like operations

[Speaker 1]
and BBC up in the same company. Okay, so I, uh, and that company Lakers company actually bought DBC, but I think the lake FS is built for a larger organization sort of a thing for large data Lakes where you would need to manage all of that and I'll get the store level, but this is known.

You have to file level. I would say so that that. In a S3 bucket or in a object store, you access the article differently than as you do it on a filer or the right. Well, most of us actually are more used to be filing. Approach. I mean, that's what I mean.

I don't know the idea of having object blocks, and you can only access them by an sjdpa sort of a request or something that is alien to me. But, but that's what. So, thanks. Any other questions, please?

[Speaker 3]
Thank you,

[Speaker 1]
oh! Oh, I say, can you maybe describe a little bit more about baking the model into a container of their specific tools that you're using or? Your own process. Using the same model that you would build. A pickle file, and you just use that along with whatever you need.

Other tools you need to ensure that the docker container is able to cost,

[Speaker 3]
so you just have like an actual runnable like container with python or whatever dependencies are there. Okay, based on whatever one likes.

[Speaker 1]
And yeah, I think we are standing between everybody else. Yes. Thank you. Nice to meet you pleasure. Adam yeah, Silas.

Thank you free at Red Hat Summit, uh, no, I was not. I could not make. I'm here to kill me. Cool! Have a good day! Hey, hey, Adam, how are you? I'm welcome. Good to see you.

[Speaker 4]
Factory.

[Speaker 3]
Right, that I think has been good. We had 10, we had 10 operating systems that I know that we supported up, and so about three or four years ago.

[Speaker 5]
When we kind of killed off Solaris and some of the other supports I had right now, like the main product is Docker and kubernetes, you know, to see eye images. It's not Docker, it's oci images game. Um, that's the main product, the the first Legacy product is. Rpms or Debian packages or?

The new ones aren't on the Z, um, that's still vintage sass. Oh, oh, but you can run our product on the Z with Linux with Linux on it? Yes, but we would never not run on your frame,

[Speaker 6]
right? Your your Z product is still there, though it's just not the the latest product. Yeah, it's not

[Speaker 5]
the latest product. There's no

[Speaker 6]
shot there. Well,

[Speaker 5]
look, I got to tell you, there's a, there's a Mainframe in the basement. It makes 200 million dollars a year, exactly.

[Speaker 4]
There's only five guys left that know how to work on that code base right then, and it's written in assembly. And, uh, now let's see, I was seeing Java okay, but it's not, uh, no, no, we don't have any transactional.

[Speaker 7]
There's nothing the SAS stuff is not transactional analytical, right? It's all about interesting.

[Speaker 4]
All right, we're going to be another language. Nope, nope. We went from pl1 to C.

Secret.

No, no, that was an Apple product. There's a million lines of code, right? It's. It's the first one uses that, um, gtk uses something like that. Then, you use the same function. Yeah, the thing is that all methods are public trial and being. Yeah, but gtk is C plus plus, and so that C plus plus is has object oriented.

That's why the plus plus, yeah, yeah, right, the? Plus. Well, now it needs like four pluses well, yeah, plus plus, right, and you got like, well, which version you want 17? Or, you know, whatever the newest version is and whatever so, but I've got all of that code I have.

I have the the pl1's gone thank God, but the C code, the original C code. Like, if you find some of the old ones you're like, that does not look like. C that looks like pl1 and just Rewritten and see. And then the new. There's a middle section of the code here.

Looks like very well written, but it's not object oriented. And then there's the object oriented. And then we have the threaded kernel stuff, and so when

[Speaker 5]
you get to the threaded kernel stuff, that is when it gets really complicated, right? So one of the projects I'm working on is fine-tuning a model to be able to write the threaded kernel code. It's so complicated, but understand the concepts of how you use it, like the model that they trained last year before I got involved.

[Speaker 8]
But it couldn't understand the constructs. It didn't understand why you did this,

[Speaker 7]
and so I went back and was, like, well, that's because you didn't format Gator, and this is the whole thing about AI.

[Speaker 5]
If you don't have good data, you're not gonna right. Yeah, this is no different than every day we've worked on. All this stuff a whole lot, right? And I don't know why this is lost on people. You cannot just beat a bunch of random crap into something and expect it to be organized.

The engine that generates and for sponsors is highly dependent on the feed that you gave. Yeah, just is right, and so I've had. The advantage is that I worked at a startup in the early 2000s that was writing an AI model that was going to do all kinds of insurance processing, which was evil on its own.

Anyway, I worked there and then, you know, step forward a bunch of years, and I show up, and it's like I've been there 14 years. We've always been doing this type of stuff, you know, and it's just we don't. It's just not as large language, right? It's a much more determinist an a store if you take.

Next door, and you program it on a data set. Is gonna be, right? Every time, right? It's AI, but it's going to be right everywhere, which matches with their mlr stuff, right. Where you're saying, look, it is deterministic, right? It's. It's enormously large programming, but it's deterministic. Yeah, I mean so, so I've been, you know?

That's what we have, but, uh, um. The problem is that the guys you wrote the really hard codes, oh God, right, welcome. Retired, but okay, but only 20 years away from that in the experiment. Right? Truthfully, yeah, Linus is not going to live forever. Neither is very Cartman. Yeah, so we're we're 50 years as a company, right, you know, and you've got when the colonel gets to 50.

We're gonna have the same problem now. The big? If you want to draw a similarity between my company and the colonel of benevolent dictator and the benevolent indicator has steered the thing in the right direction. Every time when the Benevolent hitter goes right, you're gonna have Python three, okay, and that's.

Or that's, that's a big, yeah. But, but that's, that's at least a a problem that we've seen and can be discussed.

I assume you have to think about that because, and they're, they're younger than I am. So, a benevolent dictator, we were okay, we've got a new family dictator in the game. Oh, but what I'm working at, then they decide a, um, a plan for who would replace Linus or is that?

Oh, I don't know. No, no, that's definitely. Yeah, so we've got a, uh, right, but there's all kinds of outside things. Well, okay, but but isn't isn't. One of the things that you described on the Milestone, an indication that plants sometimes go awry anyway. Yeah, doing object oriented in C.

Probably today is not used as oh, that was a great step, but you've got the code base. There's no way you're giving it up. It's working code. It's production money making code, you know, what I'm gonna say is, you don't mess with battle, tested exactly, and don't battle test it.

For 40 years, we spent 40 years beating all the bugs out of it right, and when Washington said we had to use memory safe language. Oh, Dr G doctor goodnight came to us and I happened to be on the security team at. Nearly, he's like, give me a report of every memory.

Unsafe, uh, bug we've had in the past 10 years, right? There weren't many, you're reading. He's, like, I'm gonna go to Washington and crack skull, right? We're not. We're not going. Okay, that's the same kind of story, oh much, smaller project. Let's take control project, right? They put they put Mythos against it, it reported this curl.

Yeah, recorded 14 issues Carol team and now analyzed one of them. One, one total one, yeah. Is a minor issue, all the others, uh, no, like millions of lines. Guess what, guess what? Same game, right? Yeah, sorry. Memory, unsafe language, but well coded and battle tested. You probably shouldn't recoded the rest.

No, you shouldn't, no, because you're going to make other mistakes exactly, and oh, and I've done enough experiments on that to prove that I'm right, right? So one of the theories that my a couple of my buddies and I had after a few drinks was, is that we should get over there.

Yeah, um. Write a plan right for your for your project. You run the plan, figure out all the things are going to go wrong, and then write your architecture document, but that thing, now that it's working properly and then you take that plan and take all the bad pieces out of it.

Put all the good pieces in it right now. You've got architecture diagram and a plan. I was like, I should be able to go to Ai and recreate this thing, and it should be better. Yeah. No, no, not only no, but not only no, it made the same mistakes between the first time, right?

Yeah, and then for s**** and giggles, I have three agents. One is my personal agent that I've been working on. I have two other agents all written in Ross, all right. And this one was first. This was second. This one was, at the same time, all three of them had the same butts.

How interesting right to the point where these two, right? So, I find the bug in this one. I could solve it in these two in about three seconds. I'm, like, I know what's wrong. Just go fix this. Yeah, but but okay. But and it was because of the model's personality keeps making the same as well.

We're back here. Probabilistic response from Source data, right? Yeah, sorry, yeah. Where is it going to get bug free code? There isn't a lot of it. Actually, it's going to get a lot of code. I was actually upset because I thought my theory was brilliant, because then you just take that speed up of.

I was able to write this thing in half the time, and then you write it twice, and it'd be perfect, right, right? Yeah, that's not true, right? I wrote it three times, and it was wrong every time, and I'm beating the bugs out of three things now, right, let's go.

Yeah, let's go. I was going to ask you sorry. That's why.

[Speaker 7]
There, too, even though that common mistake. Well, no, I mean, you could save Mark from me getting the basking chicken. That's what I'm saying I was gonna start laughing Jacob. He's saving us. My question was, I've got my body, of course. What we are talking about, like, we don't care about these things.

Yeah, but it needs to run, like, yeah, no, you're good, um?

[Speaker 5]
So, I was on my company, whose effort we migrated from bitbucket to gitlab. Yeah, which was the whole thing, but the hard thing is, we get lfs. How do you keep users from just dumping data into your instance? Is it? Do you have like a saloon for that or education education?

Yeah. Okay, so why? I have left hand to directions.

Don't trust me. Hello. So, anyway, look with the LFS thing I haven't got.