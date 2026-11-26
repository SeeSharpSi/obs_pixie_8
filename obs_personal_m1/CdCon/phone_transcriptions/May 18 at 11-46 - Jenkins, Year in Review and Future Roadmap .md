---
type: transcript
topic: work
---

[Speaker 1]
And it's, it's just the nature of the thing that many of us have. Jenkins controllers install them, they're doing real work, and the real work they're doing really matters.

There we go.

[Speaker 2]
So, I want to talk to you about the many faces of Jenkins. Jenkins lives and dies on its people. There are all sorts of people involved in the Jenkins project security people, events, people, people working on Google, summer of code, people working on user experience? Let's talk to those things and see the ways that they help you and that you can benefit from their work.

Visualizing pipelines is crucial. We've got to know what happens. We've got to know why it happens. We've got to know what fails, and we need to see it quickly. The user experience has improved significantly. Thanks to this thing called the pipeline graph view, it's been there for multiple years.

It is high performance, actively maintained, and fits very nicely with the existing Jenkins juicer experience, and it is an excellent replacement for Blue Ocean that is deprecated beginning in July of 2026. So if you're using Blue Ocean, get off of it and get onto pipeline drafter. It's that simple.

Next, we're also working to re reimagine the manage Jenkins UI. System administrators spend an awful lot of time in Jenkins, dealing with manage Jenkins nodes, security credentials all tied to this UI, and coming in 2026, already available in preview. Since January of 2026, you can enable from the experiments page on your user account for you and you alone.

This managed Jenkins experience. Kids faster. It's simpler, it's easier to understand. It gets rid of some of the Clutter, and yes, it's still evolving. That's why it's not the default, and it will continue to involve. We won't make it the default, probably until September. So, we're getting lots of experience with it, making sure that we're comfortable.

We want you to have a good experience. Now, your users. Deal with jobs and builds. And the job and build experience is also going through a major revision. Jobs and builds are the places where end users spend big chunks of their time. This UI is focused on reducing the Clutter that is in the existing UI so that the things you need most a pure first again.

Also available from an immediate click on your experiments page as a user. You turn it on. Nobody else has to see it, but you can explore it. See how it's working and what it's doing. You can turn it back off. It's that kind of transparent. So jobs and builds crucial.

The dashboard, the top level thing. The first thing you'd see also going through significant improvements. We're delighted with the progress we're making here. This one probably has the most work yet remaining. It'll continue getting Evolution throughout 2026, Isis Vic. We suspect we won't enable it live. Default until 2027, we've got to have the time to make sure it works, but it's it's evolving, strengthening, and growing.

Now, on the securing side. Okay, you care about security, and if you don't care about security, you should care about security. And Jenkins has a crucial part of your delivery system needs to be secure. Thanks to the European commission. A bug value program has been initiated for Jenkins this year, BEC funded.

Yes, we hack to act as the front end to receive bug Bounty submissions from. I think the total values are up to 5, 000 Euro will be paid for bugs submitted to specific areas. We're deeply grateful. The first three advisories in 2026 all included issues from the bug memory, so we're getting good results from it.

We really like what they're doing. Content security policy is another piece of security. This is an opportunity to allow you to configure your Jenkins to be more secure by default. Content security policy, the way for an application that's running in a web browser to ask the web browser. Please Safeguard me against certain classes of vulnerabilities.

You can now enable content security policy in Jenkins, its top plugins, all support content security policy, and that enablement will block most cross-site scripting vulnerabilities in your system, even if a plugin has that vulnerability. So, this is a safeguard for you, but you have to choose to enable it.

We will probably not enable it by default until 2027. We don't want to break users and surprise them. So, the other piece of the story Google summer of code. Thanks to Google, they fund major investments in open source software every year through their summer of code program. Jenkins has been authorized for five slots.

Two AI slots. Uh, two tool modernization pieces and one working on our website. We're very grateful to Google for what they've done to Foster and support open source. They make cash payments to those who are selected to perform this work after a summer of work on the Google summerboard code project.

We specifically thank the mentors they've done great things by acting as mentors of these brand new contributors. Now! Brand new contributors has created a bit of a challenge for the Jenkins project. Um, Google summer of code caused us to go from, on average, 90 open poll requests to Jenkins core at any time six months ago to now.

150 open Corporal requests against Jenkins Corps. That's a bunch. And the danger is, it overwhelms the maintainers, right? So, we've had to adopt some some implementation details. PS AI is not the problem here. The problem is not that AI is being used to generate these. Yes, it's frequently used.

We like that the problem is quality of the submission. So, we've got some some nice little indicators we use to tell us if the thing is a good quality first. If you don't use our pull request template, we close your pull request. Oh, whoa, already 40 or more percent of the things.

Just get closed that fast without us wasting any maintainer time. Just close it because you didn't have the good sense to read what we wrote. Hey, first, second. Co-Pilot is getting better and better at reading Jenkins plug-in source code. It is impressive how good they are. We let co-pilot do the first review.

And guess what? It will find things that are flagrant, missteps it will, it will identify. Oh, you've introduced this terrible, horrible thing, and we can watch to see if that submitter acts on it or not. We haven't spent any maintainer time co-pilot does the work. Likewise, we've decided to allow not more than two open pull requests from any new new contributor.

Now, some of them Flinch at that. Oh well, wait, a sec. I've got more. No, sorry. If we don't get you all the way through at least one or two pull requests all the way to merge. You are going to risk overwhelming us. We can't have that, so simple limits matter deeply.

Java updates so? The Java ecosystem continues to do what it started doing with Java 11, which is every two years release a new long-term support version with significant features. 11, 17, 21, 25. Jenkins in order to maintain itself has decided to support the most recent Java LTS and one prior.

That means we just dropped Java 17. We now support 21 and 25. It matters to you because, well, because we just had a great blog post that said, look, I saved 10 percent of my runtime memory by upgrading from 17 to 21. No other change to the code instance.

They just changed jdk. And that saved them. And, and I'm sorry, in the cloud memory is money. Right, it matters deeply that you save memory. So big win. We're also pleased that we were able to upgrade from Spring's five to six in 2024 and we'll go to Spring 7 in 2026.

Dependency updates matter. We want to stay current. We want to stay supported. Open source projects on which we rely. We don't want to put a burden on them to support us with something that they don't want to support, so it matters deeply that we get up to date. We're really pleased also with the work that's happened in the transition of Jakarta.

All right, so there was this Java Enterprise Edition thing. We are now moving very nicely onto Jakarta ee10 this year nine. We made the transition two years ago, and we expect it's going to be the same kind of steps steadily as Jakarta versions come out.

[Speaker 1]
Hey, Mark, is that migration to those new versions going easier than it did in the past? Well?

[Speaker 2]
The. Okay, so there's a long and so good question. The question was, is, are the migrations any easier now than they were in the past? The 2024 migration was horrific. Because it was major technology shifts at multiple points, and the Jenkins project has this phrase in its governing document that says.

Compatibility matters. And so we strive diligently to assure that your 15 year old plug-in still runs. Now, come on. That thing was built with Java 1, 4, maybe, but it still runs. Compatibility really does still matter, and therefore the cost is was very high for that transition. In 2024.

[Speaker 1]
The

[Speaker 2]
2026 transition has been surprisingly smooth. Guess what? The 2024 people were really smart. They did a great job those of us doing it now are very grateful. I'm supremely grateful for what they did so much easier now, and they get easier every time time. Do one.

[Speaker 1]
Okay, thanks for asking.

[Speaker 2]
So, a crucial point for me to make is that the employers who employ people who work on Jenkins are crucial to the Jenkins project. People have got to eat and these developers. These people are paid by an employer who were very grateful they fund them. Please, if you've got people who work on Jenkins.

Thank your employer. And encourage them to continue supporting that. We're especially grateful to cloud bees. They fund multiple people on the infra team, multiple people on the security team, and two of the officers to Jenkins. We're really, really pleased that the diversity in the jackass project, but that one company is crucial to our our funding and our ongoing development.

Now, the other thing that we're grateful for is the services that are provided. Continuous delivery Foundation provides significant funding for our infrastructure, and they protect the intellectual property. So we cannot. No single company could take Jenkins private. Can't be done because the foundation owns the intellectual property. We're grateful for that Microsoft.

We thank them for for GitHub. It's wonderful that we host on their their service, and they gave us a major infrastructure donation. Also grateful that was their 2026 donation. AWS has donated for the last two years, and again, we're so grateful for them. We could not run the project without their and for donations.

It's that crucial. Special thanks to jfrog. They absorb the burden of Hosting our artifact repository. Even with the? Tragic misuse that sometimes happens when large organizations decide to repeatedly download the same artifact over and over and over. Please, if you're from large organization. Whichever that is, check that you're caching the stuff pretty please.

It's really painful for me to have to go submit an abuse report to AWS because you're abusing infrastructure that is being donated. Likewise, you think the bossian for their donation of our bug tracker? Remember, we've had a bunch of great successes in the past year. Pipeline visualization Java support spring support?

Um, the bug boundary programs, and we're looking forward to things that are coming this year. More user experience changes, Google summer of code, and more from bug boundary. What we need more contributors? We need people who will help do a little bit of work. What we also need more funding.

If your company is not part of the Linux Foundation, encourage them to become part of the Linux Linux Foundation. Once they're part of the Linux Foundation, include encourage them to become part of a continuous delivery Foundation. That's it! Thanks, our next talk, oh clap timer.

[Speaker 3]
Our next event is the

[Speaker 2]
CDF Town Hall that will happen over the lunch hour. So, this is your chance to take a lunch break. Sorry, I ran over. Shame on me, um?