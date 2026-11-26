---
type: transcript
topic: work
---


Have a fun story. I think my my brother was supposed to be here today.

[Speaker 1]
Uh, but he said he was going up to his cabin to go fishing, which is not a Minnesota joke. That's actually what he's doing. But uh, he was here. Yesterday,

[Speaker 2]
and uh, he was going around the show before, and he hung out at the balcon Booth. He says, he's so excited, because just actually, a week and a half ago, his company,

[Speaker 1]
uh, he's the head of engineering to this company, uh, had just deployed valky and said, oh, were you using the other

[Speaker 2]
proprietary, uh, database tool, and uh, he said, yeah, but you know my, uh, YouTube of engineering came to me, and he said, you know, what? We gotta go with balke, because balkey's, where everything is?

[Speaker 1]
Uh, and so I'm super excited to introduce our next speaker, uh Madeline Olsen and Jacob Murray, uh Murphy, uh Madeline is a balky project maintainer, uh, Jacob is also a project maintainer, um, and they are going to talk us about balky and how developers and maintainers can work their way through this.

AI nuts come on up, Madeline and Jacob.

[Speaker 3]
Good morning, everyone. My name is Asian Olson. This is agent Murphy. We've heard that he's very transient these days. So, um, and we're going to be talking a little bit about how we ended about the project, are dealing with the significant increase. We've been seeing AI days. So obviously, valky is not quite as big as the Linux project, but we saw a very similar Trend to us.

Venus was just talked about. It's about getting six month release cycle, and in the last six months routine about a 55 increase and the number of individual commits that are coming to the project. And now, some of these are good rate commits from our existing contributor base. Um, and some of them are, you know, drive by the saw, one that came from someone we eventually identified as, just like an open claw box.

So it's not great. It's all the contributions. And this. This is maybe tolerable. But the bigger Trend we've noticed is that the number of commits is the lumber lines code inside those commits. Is has seen a substantial increase, so we see about 500 increase in the actual number of lines of code that we have been receiving as maintainers.

Now, part of that is because AI tooling has enabled the strong, existing committers of the project to build really big, exciting, great things and then contribute them to the project. But also, we've seen that some of the gnai tooling really likes to write a lot of code, and that code is again not always the highest quality.

And so, you know, both me and Jacob. The other maintainers have been kind of asked the question, what do we do about this? And um, the response that we kind of keep hearing is just use agents. And that's a response.

[Speaker 4]
Um, it's not the most practical, useful piece of advice, and so, um, we've been trying over the last six months. You know, we worked for a very we'll call them AI Ford companies who have been encouraging us to use AI a lot, and so we, you know, we're a little bit ahead of this.

We've been using into. We're gonna try to share a little bit of what we've been thinking about and how we've been trying to apply it. We know everyone's bending out taking those agents and say, hey, just review this code, and sometimes they're useful feedback. But they oftentimes miss the bigger picture.

And you know, I actually just did a release of Valkyrie. I got one yesterday and yay. Thank you. Um, go try it out if you want it. It's faster, it's better, but the kind of the important thing is one of the things we try to do with this release was remove a lot of the toil that comes with releasing.

And one of the things that I've noticed. Notice I've noticed is that using agents and AI for automation only saves time. If you can really trust the end results, so if we're using it to do automated backboarding, like we have to actually trust that it's working. Um, when we do automated reviews, I end up noticing that I still have to check the results, because although it finds bugs and that's great.

It still will sometimes just add tests in the wrong place or one of the things is. We use tickle, a very esoteric language for all the testing and value and. Don't really know what to do with tickle. They'll write new tasks. They won't know what abstractions are there. And a lot of times, the humans also go in and try to fix all of that.

And so kind of. One of the things I've been trying very hard is to build a tooling that delicious, a combination of both explaining the non-determinism of AI and then pairing it with deterministic code. We've been writing. So, one of the specific things that we do alive. So, valky has a development Branch, and that development Branch will write all in your code, and then all the individual commits get forwarded from the development Branch to the individual releases.

So I mentioned we did 9.1 yesterday, and so one of the tasks that needs to be done is taking all of the commits that are to be backported and backward them to police branch. Not the most exciting jobs, but it's actually something that AI has helped us. Can do so.

We have a job that runs. I think it currently runs once a day and it basically goes and collects all of the pending commits. It will then attempt to take all of those commits one by one and apply them individually onto the release branch. So, in this case, you know, we found 26 minutes, and then we do, you know, a chunk of time because the end still is a review that needs to happen?

So somebody will apply very cleanly and long as the commit applies cleanly and all the tests pass we move on. And if we do find a commit. We can use that in something. Use something like Cloud code to go and basically try to. Uh, fix it, right? Try to handle the merge complex and then the end result is.

We have these back 40 CRS. So, at the end of all of this, we still have a qmb Loop to be like, hey, were these old shared correctly wavelengths to all the source PRS to make sure? Um, that you can actually trust the province, all this data, and then the latest version actually has more details about the conflicts, not just as it was all, but you know, we, we're.

This is still a tool that we're working on overall. So, this is a combination of using AI. To do some of the toil that used to be done by hands.

[Speaker 2]
Yeah, and using AI isn't just for backboarding. We also, I've been really enjoying using the brand new Mythos model to find bugs and vulnerabilities. We actually don't have access to maps. Memphis is pacifier. Yeah, unfortunately. Okay, well, I guess we could just use Focus 4.6.

[Speaker 3]
Uh, so we've been building vulnerability and bug hunting harnesses. Mala and I actually fulfilled similar harnesses and came to almost the exact same results. So, AI tends to find similar bugs across multiple guns. And we've we found over 20 different bugs using the system. Additionally, you could we could run the system correctly on unstable and find the bug before people are recording them sort of projects.

But not everything can be solved with AI, uh, there's still a lot of automation where AI isn't really the best tool that we have AI itself is very non-deterministic, and there are a lot of traditional deterministic automations that still. Need to be built for projects like valky. One of those cases was in verifying the origin of code that is submitted to the project.

We have a lot of use cases inside of down key to identify and cache these. Externally contributed commits that are actually being pulled for Bishop from other similar projects that I maybe have different licenses. And that creates copyright and legal concerns for us. So, here we have a demo of this tool that we've built.

We actually used AI to build the tool. But the tool itself is deterministic. We've cloned here in PR that was actually submitted to the about the repository that we identified was actually plagiarism restaurant project. Um, and here you can see that our automation is running. We call this our provenance guard.

What it's doing is it's comparing the changes, the hunks of lines of code that are changed, I guess. A database of pre-populated changes from those external projects. Um, and you'll find out here soon that these, uh, in this case, the the homesick code we're actually ripped, and

[Speaker 2]
uh, this would prevent this tote from being merged, uh, which will save us a bunch of burden as maintainers where we would previously have to scan this manually and figure it out. And that goal here would be that then we can regrown this. We could rerun this, uh, check when Cody submitted again, and it should, uh, successfully pass.

[Speaker 3]
It's running again. This is running in real time, by the way. It

[Speaker 4]
does a lot of, you know, if you ask AI do, it's going to take 45 minutes and spend 20

[Speaker 3]
minutes. Yeah, that's right, we've got a little tiny spot and see. It's accessible, and then we can go emergency PR. If you find that everything is, you know? Actually shown them out of the Providence.

[Speaker 4]
And the original takeaway that I wanted to have from this brief keynote was that the end of the day we still want to make sure that maintainers are the ones who are in charge of the project Direction, right, the maintainers of the ones that have all the context they have all the history.

They know the individuals inside organizations that are using these projects and what you know, what, what's actually needed, and what's healthcare. And the comment that I mentioned earlier is like the just use agents. One of the concerns I have is that people are going to offload, like the reasoning, the thought behind the projects to the agents, and just say, hey, agent, what should we do about this?

And I don't think that's a good deal. I think there is something that gets lost when we give too much over Ryan swing. You know? When something ranks at two in the morning, like the agent might not be able to figure it out, or you might not have the person who has to access the right foundational model to go and root cause it.

So, we really want to make sure that these agents are being used to support the existing maintainers of the project. And then they just say this was the original takeaway, because while I was being here, and while I was talking with others, I'm reminded that you know the maintainers are still human.

And you know, I've seen so much more burnout in the age of AI than I have in quite a while. So, for a long time, I used to work on redis opens for software right, and one of the frustrations I had the project was that it was hard to just to get on the code we wanted to get in and right.

Now, you know, we can write as much code as we want. Like, like? Developing project is Center neutral. We have all these tools that are allowing you to write code fast than ever. So why are we feeling more burned out than ever, and I think it's just because of all of these expectations that we're putting on top of maintainers.

And it's hard to sort of keep up with that. The number of you know pains that I've gotten are slack my GitHub, but hey, we found this, the number of, you know, security vulnerability. We've heard it's gone up significantly, and yes, people are providing patches um, and they're they're.

They're trying their best to do, you know to make our life easier, but it is still it's still difficult, right? I'm just gonna sniffly more time, both inside, you know, I work a mus. I'm thankful that they let me spend my time working on a greater Source project. But it's still a huge amount of my time outside of work.

To make sure this, you know this, this launch happens, but 9.1 launch wasn't supposed to be last night. It was supposed to be a week ago, but we had so much stuff that needs to finalized a working, and it ended up happening during this conference. And so I just want to everyone to take away.

Like, you know, I think maintainers are under more stress than they've been in a long time and? You know, AI is a tool as we. As Beena said is, a lot of people have been saying, and at the end of the tools should be helping them right, helping with their mental health and making sure they're able to continue to make these products maintain these projects.

And it all depends, immense them all. So, that's the end of our talk. Um, if you want to see any of the tooling that we sort of talked about, there's a GitHub. You can protect about the GitHub, the project for the Providence guard, is called verified Providence, and then we also have the bathroom CI agent, which shows a lot of me infrastructure and Ops work that the bathroom project depends on.

To continue running. We're also doing a talk later today about Samantha cashman, which is more of a technical talk. So, if you also mentioned that come, come join us if you have any questions. We'll also be there to talk, so thank you! Thank you for your time joining us.