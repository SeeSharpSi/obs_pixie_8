---
type: transcript
topic: work
---

[Speaker 1]
For a clean, professional look.

Hello, hello. So, we're gonna go ahead and get started. To introduce myself. I'm Jacob Murphy. One of the documentators, and I'm here with. Who is the queen of Belgium?

[Speaker 2]
I work at Google my mom's at Amazon today. We're here to talk to you about semantic caching. Um, so just to show our hands who here has heard of semantic cashing before. Who here has used it in some kind of project that you've built? No hands. Okay, that's great, so we're going to go over.

Uh, what significant cashing is and why we needed what changed and why we're no longer looking at just simple key value caching? And then, uh, we're gonna go through some of the toolkit that you have, uh, in open source, to build semantic caching applications. So, the the key thing that changed here is that caching is no longer just a hash table problem.

So, if you know what Valky is? That's the project that Milo and I work on. It's an inventory essentially named memory hash table that you can remotely to get a quick key value lookups. Uh, there's a bunch of other features like data structures that we have that are encoded Sts.

But at the end of the day, it's mostly a hash table problem, but when you introduce AI, uh, the tip is that there's no longer a clean key that you can look up inside of the hash.

[Speaker 1]
Um, instead of looking up by point, you now have to look up based off of a geometry lookup.

So, as you know, caching is one of the oldest.

[Speaker 2]
Archetypes of software engineering. There's lots of different ways that you can add caches to your applications. You have things like query caching. You have like session storage. All of these use cases people use for valkyrie. And various other connection applications. But they all change on the fact that your e-lookup is going to be an exact lookup inside of this app.

And this has historically worked really good because. Real workloads tend to be skewed. The most common distribution of traffic actually is usually like a zipian distribution. Which is like a power law, so you have this rank of items here on the right side. With the first rig showing that this item is accessed in order of energy bigger than the second type.

So, think about something like social media. The top social media accounts are accessed incredibly frequently. But there's a lot of accounts that are very infrequently accessible. Um, this creates this power law as if he and style distribution of traffic.

[Speaker 1]
So before, like cachet ratio logic, used to just be how much memory do I want to give my cash? And I will kind of capture some rank of this distribution. And since I'm capturing. The the most dense part of the?

[Speaker 2]
The house because it's cash. I'm going to get a really good hit rate for a pretty low cost. But now, with AI, the query has changed. It's no longer an exact key. You end up with a lot of different paragraphs, right? So someone might ask from Seattle, so people are always asking, what is the weather in Seattle today?

Is it going to rain in Seattle? Seattle forecast, I think I should know about Seattle weather today. Um, all those

[Speaker 1]
different ways actually have medical intentions. My, uh, normalizing these, is going to be very difficult to get to a consistent hash key across all of those.

[Speaker 2]
If you just take these queries and you run them through the cache, your hit rate is going to be basically zero, right? You're no longer having applications that are sending very similar queries over and over again. And with the zippy and distribution, uh? That that distribution still does exist, but it's less.

It's more contagious. Um, on the other hand, uh, not only is your hit rate going down because of the way the traffic has changed. But your cost is going up a lot. Uh, element calls are not milliseconds, like calls to a database. They tend to be orders of seconds.

Um, there's real dollars that you're spending on the PPI purpose that you're no longer saving. Okay, so just to illustrate this, uh, you kind of have, uh, here, on the left, a traditional cache where you have a bunch of points within, uh, here. I'm just kind of projecting it onto a 2d space, but you can imagine each one of these is some different point lookup that your application is going to be making.

And before, you could just take these, put them into your cash into the word. But now, these points have fuzzed a bunch. And it's, it's now a contiguous heat map of different queries that you're going to see. And you end up with the same special space flight now. Uh, what we're matching against has to change.

This is where we start getting into geometry.

[Speaker 1]
Just to clarify, uh, very often. What you're going to do is, you're going to take these squares. You're going to encode them into some kind of geographic or geometric representation we call that like a vector embedding. And then you use. Like, you see very much to create. The matches between the purple green orange.

But it has a lot of edges. Um, the first one being I?

[Speaker 2]
You need to configure some kind of threshold and thresholds are effectively trade-offs. A really tight threshold means that you're going to have a lot of false misses. Someone asked for. What is the weather in Seattle today? Someone else asked for. Uh, what is today's weather in Seattle? If you have a very tight radius.

Those might have slightly different semantic representations. They might not be a match, and that's going to show up as additional cost. Overall, this actually isn't that big of an issue. It's just ineffective caching. Uh, your other option is, you can loosen your threshold, right? But now, you have a different problem, which is false hits.

And argument. Those are much worse if I ask, what is the weather this Wednesday? And I ask, what is the weather last Wednesday? Those need to be very different results. Uh, if I were to have a threshold that was loosened up that those both match? We would send last week's weather instead of this week's weather to the user.

So, those bugs tend to hide behind the cachets. And here's the representation of this. You can see you have like a false Miss. Maybe it's a very sparse area of your your heat map. I think that's another. Edge of this is that? Here. It looks like these are all the same size.

Of the the areas of the hit points are all the same size, but in reality, like the embeddings generate non-uniform distribution. Uh, the embeddings might be very tight in one location where you have a lot of semantic detail, but in other locations, they might be very sparse. So the threshold?

Being static leads to. In this case, a potential false Miss for a query that should have been categorized into the purple group. Or a false hit in this query that is somewhere between green and red.

And it's not just the threshold. There's a lot of different problems that you might get. Obviously, when you're talking about caching, one of the things you need to think about is staleness. How do you evict scope?

With traditional KDE fashion, right? Key value caching. You would, uh, store a value. Associated with some TTL, and then if that value wasn't refreshed or retrieved in a certain amount of time, it might age out and you get that space back. But with semantine fashion, you now need to think about.

Is that area that he's not very popular or not? Maybe the specific query hasn't been all right. The specific result hasn't been protreated in a certain amount of time. But it's in a very hot area of the heat map. And maybe we don't want to digital? Uh, you have other problems like multi-tenancy, uh.

So, if you have different services that are storing data, they need to be isolated for one another so that you don't end up with caches from one service leaking into another cache. Personalization becomes a big challenge, because now, uh, you can't look up the result for one user and present that to a different user, right?

If I say, what's the weather at my house today? I can't get someone else's weather that there's on the other side of the world. And finally, you have. Problems with, like, conversational memory. So, if you have like multi-term? Your cash hit rate, right? Drop to zero as you're no longer just looking at one query.

You're really appending that query to a history of conversation. And now, now it's going to talk about all the good things about safety catching. Apparently not talking about the good things. Um,

[Speaker 3]
so, yeah, so one of the great things about working at, you know, a big tech company is weak to help a lot of our customers, you know, build the stuff in production, and so we're going to talk through a little bit about kind of the mechanics of how you know, build such a big introduction.

Um, I was just going to add that we are going to leave watch at the end because we think it's a very technical topic. So, if people have questions, we only should we have enough time for people to ask those. I think generally speaking if you have an interesting use case.

It's good to kind of talk about it and elaborate that, so we're going to give the broad Strokes and how you build such a system in production. Talk a little bit about some of the

[Speaker 2]
caveats that Jacob was just mentioning.

[Speaker 3]
And then talk about how it's implemented across three different popular Vector simulator research engines. Um, so the semantic cash flow if we draw the closest parallel to how we imagine with traditional KBK KB lookups. Um, as you start with your initial prompt, and you're then you're going to go through an embedding process.

So this is the process, basically taking that query triangle down into those mathematical array that you can store in a vector similarity?

[Speaker 1]
The simplest way is just to take it, and then basically

[Speaker 3]
embed it as a. As a strain, you can also use like a lightweight LM to basically try to rewrite that query to make it more edible. Try to take out all the personalization aspects you can try to demoralize it a bit. For example, you say, hey, what's the weather where I am in Seattle?

You can de-personalize it by going and saying, okay, the person is in Seattle or they're in Minneapolis right now. Specifically, next Wednesday is a specific date. You can go take that out and put that in there. So all this happens during the embedding process, which can be as lightweight or as.

Comprehensive as it means to be. And then what their events you and storage inside of extra similarity database? So, from there, the next step is going to be. You're going to do the search over that Vector space, so satisfactor space is probably going to be hsw.

To basically, you know, depending on what kind of type of systems you need. We'll talk about sort of tradeoffs between those two. Um, so typically that's going to be an approximate search, so you're going to hear a lot about things called recall when you're sort of evaluating the performance.

And that's basically, you know, ideally, you should always find the closest neighbor. But the only way to do that effectively. In very high dimensional spaces is to search everything, and that's not computation feasible today, um. I mean, it might be based on a use case you can use. We'll call it flat index, and I'll just search anything, but most people use frox events.

Um, and so recall is basically you know what percentage of the best values did you find while searching? So, you want that number to basically be as high as possible. Um, so after we you find out so you found an object, it's what the algorithm thinks it's the closest neighbor.

Then you have to evaluate against that threshold, and this is what Jake was talking about, and we'll talk a little bit about you know how you tune that then? How to think about that value? As Jacob mentioned, it's very much a use case specific problem, right? You might have

[Speaker 1]
a lot

[Speaker 3]
of queries, which aren't as inherently very semantic and similar right. If you're building? Now, I'm bringing snow, and we're building a calculator app like, it's not very good, right? You need very precise match for that to work. Um, if you're feeling something very generic, you might be able to have much lower representations, you know, like?

What are some things to do in Argentina or some things new to Minnesota? You know, as long as you're able to. Basically, the whole app is built around that you might be able to get away with a lower threshold. Great! So let's talk a little bit, um?

[Speaker 2]
More about the specifics about, you know, the tuning of those variables we talked about. So, some analysis that we did within elasticash, basically. Do you know more or less transparent? Um, caching, semantic caching. So, this is this was a very simple. Benchmark we built based on a 63 parameter query.

[Speaker 3]
Um, which was basically. Uh, on the far left is the threshold for. Um, how close it needs to be? This is like a cement, like, how close the two objects are this high dimension out of the space. The top value is the Baseline, right? You're not using a prey at all semantic cache in front of the system at all.

So that's based on the Baseline and basically tuning that threshold. You'll see that the hit rate will basically change over time. So high threshold means we are doing. We are very strict in what we count as a semantically similar match. So, using a threshold 0.99, we saw an example of 23.5 in rates.

Uh, so these specific queries were I believe about travel information. So, basically, you know, what's it like in Argentina? Where are some things to do in Argentina, that type of thing? And then the accuracy is based in this recall primary. We were talking about, like, how accurate are these actually giving you the, the correct, or the result you were intending to graph?

Um, so having too high of a baseline, uh, too high, the threshold. You're not gonna see very much savings, because basically everything's going to be a Miss. You're going to constantly have to go back to the LM and then regenerate it from

[Speaker 1]
scratch. Go do things do. I'll go do all the tool calls. Figure all that good stuff out to give a good response back to the end user. So, for this specific workload, 0.8 is kind of a good, sweet spot. So, having that threshold got a hit rate of about 87 percent.

[Speaker 3]
Um, so 92 percent of the time we were grabbing the best result. And

[Speaker 1]
then you're able to save about 84 of all of the cost savings based off of.

[Speaker 3]
Basically reducing the calls to the outline. This specifically was based off using donkey as a vector store.

[Speaker 1]
Um, and we'll talk a little bit about why you might, in fact, velky or open search for PG of x.

[Speaker 3]
Uh, and at the bottom, you can see, sort of, where we're getting benchmark data from. Uh, fun Benchmark. Was The Benchmark community against all this using Titan, the Titan embedded model? Um. So, choosing the right technology is very important. So, uh, as Jacob mentioned earlier, we both work on the docui project.

Zavaki is an entirely in memory. Uh, KB database, so that means it's going to be very efficient at doing fast processing memory. And that's why it was traditionally very good for KB lookups, right? A Katie lookup traditionally takes a couple of microseconds of in memory, but the downside is, you have to store everything in dram and dram is very expensive.

Right now, the systems are very expensive right now. Um, but it's pointing very good if you need very high throughput and multiple one's very real-time opinions.

Now, this is going to be contrasted with something like open search Vector, so their main beta representation is on disk. And that means you ever see much higher latency when doing queries because you have to be gaining a lot of data back to memory based based page caches as opposed to starting with natively in memory.

Um, with open search, we're going to be saying batch updates, so updates are going to be reflected a little bit more slowly. So, if you basically want to update the cache and then require the cache like, open search will be a little bit slower. But would you really benefit here is at scale?

You're going to be spending a lot less money on the actual storage of data on disk. Uh, now. Another very popular thing is PG Vector. PG Vector is, uh, basically an extension for postgres. A lot of people would consider postcards a traditional, you know, primary database, but it can also be used for all sorts of other stuff, and we've seen a lot of individuals use it for semantic caching.

And it has a lot of the same benefits as open search. Uh, it's going to be a lot cheaper to store if you have a very large Corpus of data. The actual request rates to the system itself is a bit lower. I also want to touch a little bit on durability, um.

One of the things that a lot of people think with cash is that they're ephemeral. You're always taking ttls on them, but that's the necessarility you don't want ASD durable. And the reason for that is with traditional lookup. Um, the actual regeneration of the data is actually quite cheap, right?

So, if you lose the data, you have to go requiring the database that SQL query is not going to take that much time. But semantic search actually takes a long time, right? Because you can build this work with this embedding elements or quite slow. The cost is actually much higher, so there's actually a lot of value and actually durability.

Storing the resultant computation on disks so that it fails. Instead of re-running the entire system back to the L1, you can just reload it back to the disk. So, valkyrie does have durability options which have historically been unused for caching workbook, but they're actually quite useful in the context of semantic caching.

And obviously, open storage opinion Vector also have all that good stuff with durability. So this was something I kind of considered. I wasn't trying to pick the right technology. Um, so we've got one level deeper inside, one level deeper, and talk about what this actually looks like underneath that.

So, we're talking about Valkyrie first, because vacuum's, my favorite. And. So specifically, which means this whole spec to catch and look up is you need to create a vector similarity effect. So, I'm now here. That means using the full text. Module. This is naming we've inherited from redis because redis first created a full text module, and then they added Vector similarity to their full text.

So that's the way it is.

[Speaker 1]
Um, with the schema and the scheme will be. Hey, here's a query, and then here's the answer with text, and then the actual meta itself. So those are the three values we're storing, where the answer would be embedding.

[Speaker 3]
Um, at some point, you might want to store more information, like user context, if it's a multi-turn conversation you're having with us. You might want to also store the specific user information, and so that can also be stored inside the index as well. And there's a bunch of different distance metrics as of right now.

I think most people use cosine for this specific workload, but it is one of the things you can play around with. And Ben, the specific workload we have. The dementia is specific to the. Any embedding you're using in this case 2024, hopefully that's consistent across all three of them.

So, you're going to create this index and then the index will basically index all the keys that have a specific.

Cool. So then we have the index. We have all the data built up. So now when we get a query that comes in, we're going to go to our embedding model. We're going to generate the embedding, and I do a search against it. Uh, in this case, we have the.

Not odd. Little syntax of like dollar sign equals, um, basically saying. Hey, k n look for this? Is this for this embedding based on inspector? And then you will basically get results back. And if you do not get anything, I would say it would be in your specific. Threshold your tolerance.

You will basically then don't have to go and run the. Query back to the LMS. Get the actual results, and then you'll store the value inside the cache table with anything else right. It's on the Miss you store it. So, this is very similar. This is very traditional looking and docking.

So, we're going to quickly go through what this looks like in the other two databases. I'll see something very similar. We're creating table in this case for the exact same information. The query the answer in the ending? Um, just like the Valky, the PG vector is based off of an extension, so you will create the extension Perfectors first.

Basically, load that extension in. And then you will. Basically do the same type of thing. You're doing a select. You're basically wearing. Hey, the little two angle brackets with equal is.

[Speaker 1]
Simple, and you're basically looking to say, hey.

[Speaker 3]
Yeah, go find something. Where at a score, which is basically a semantic similarity,

[Speaker 1]
and then it limits the number of results, uh, just so it's not returning everything you don't. It's very important for the evacuate. It will protect the whole data. Right, looks the same thing, but also a slightly more similar syntax that some people might think about.

[Speaker 2]
And then, lastly, with open search. One thing that's cool, or maybe not cool about search, is it is a little bit nicer than that. It has a lot of apis that do a lot of heavy lifting for you, so you're able to basically do what what is? Get out of a cement cash value, so you're going to be putting objects into a semantic cache and basically then doing the center cache queries off the top of that.

You can say they all basically have the same pattern and which database is best for you is going to depend on your workflow. And you should try all of them and see which one makes the most sense for you. Or if you already have your data in one place.

The general recommendation is to put the cash already in the database you have for a while. There was a trend for purpose built Vector databases. I think we've sort of reversed that Trend, and now people are just thinking.

[Speaker 1]
We should probably put the vector similarity where the date already is, or with all the systems.

So just kind of at the closing thought, um, so caching for AI is basically the same function as we wear same problems that we were dealing with for a very long time. We have back ends that are very slow, and we want to make sure that we are accelerating those.

So, basically, we're taking the same problem. We had four just with a new distance function. And basically, we want to. It's a new type of optimization problem to optimize for, but everything we were talking about the same hit rate still means the same thing. Observability still means the same thing and then eviction and correctness are all still very important.

Things so you can take all the same learnings you had with how you were building caching systems in the past and translating them to. Samantha cash. So, as I said, we're going to have a good bit of time for questions and. You want. You can follow us on socials.

Thank you so much.

[Speaker 4]
I just realized Jacob's social is just about the project, so he's about the project. All right, I'm gonna take out these sunglasses.

[Speaker 1]
Does anyone have any questions?

Don't

[Speaker 3]
know. We have another microphone. You could repeat it. Okay, okay. So how do you? Tailor different civilizations, right? Um, like when you run you, the one of these contexts that you want to provide? The first user response to? Significant semantic. Yeah, so the question is, how do you not lose personalization to make sure that the crash the requests are relevant for your user?

Let me make Jacob answer that. Yeah, so I think. Two things like one is, uh. You should understand that your application needs personalization or not, right? Because if you don't need personalization, obviously, a semantic cash going to work really good. Um, now if you do need personalization, you have a few options in your toolkit.

I think the most common one is like you would run a lightweight pass at the end to basically get you get the generalized response from the cache llm system. And then, once you have the generalized response, you would pass that through something that's lightweight and quick to personalize it in some way.

That would allow you to take the majority of the work and still generalize it. But there's a trade-off there, right? Like the Deep contextual understanding of the personalization that comes with llm was like changing the T Cloud. You're not going to get that, um. So, you have to understand for like the purpose that you're building what you need, right?

If you need truly deep personalization, like, maybe, uh, you just need to send the full context off to Ella. I mean, the bigger the aquarium, the less likely it's going to get right, but you're going to do what you might just do it ahead of right. So, you change the initial prompts to reduce and still be kind of relevant.

Yeah, yeah, so if there's personalization is an actual? You can do an in normalization pass on that. Which yeah, you definitely need to be normalizing all of the parties because English is very hard. As we all know, like, there's? Hundreds of different ways to say the exact same thing.

And you know, just? The right similarity between them might not be.

[Speaker 1]
The only thing that I.

[Speaker 2]
I've I've seen a specific user inside AWS news, is they always try to normalize it to a set of tool calls, and so the question is, like, how would you like, look up my order like it will normalize it to a tool call that's parameterized, and so you just need to keep basically that set of instructions in the cache and then when the LM goes looks for it, you'll find that set of tool calls, and then it'll be able to call those with and add the relevant personalization so you can.

Also, it doesn't need to strictly be like that one step, right? Not all. Passionate is just. Oh, here's the all right. Here's the response. It's, like, hey, here's all the data you need to implement that specific action that you want to use.

[Speaker 1]
You mentioned. Yeah, you mentioned

[Speaker 4]
using a lighter llm to maybe depersonalize the initial prompt so that it's easier or more likely to find the vector representation, but I may have missed it. What are you? What do you recommend using to translate? I'm not in, you know, data science land? What do you recommend using to translate the prompt into a vector representation?

Um,

[Speaker 1]
yes, what are you actually using to translate the query into the bedding? So there are basically embedding models that are supporting that we are using. The Benchmark I showed was using a version of Titan, which is a. I think an Amazon system, but

[Speaker 3]
there

[Speaker 1]
are other ones that are widely available that specifically do that. They make tight types of building that, being as we met cool. I think there. So, it's important development hug your face. Yeah.

I

[Speaker 5]
had a question about the threshold setting process because it seems like the thresholds might need to be different in different applications, and then. So, how can you make the threshold setting process scale for different applications? Like, what do you have to do to find those thresholds. Yes,

[Speaker 2]
the question is, how do you probably tune this threshold and this is by far? I've done this entire version of this talk multiple times, and this is by far the most common question and. Um, the most common thing we've seen is just you have to go try it for application, so making sure that the system you build is tunable by default, and you're basically looking for those caching rates, right?

Like that you're, you're still looking for a good 80 percentage attachment rate while making sure that the accuracy is still reasonable. It's

[Speaker 1]
going

[Speaker 2]
to always end up the application specific. Um, at least right now. There's a there are some. Like tools that will do this for you. Um, what? I've noticed a lot of them have kind of gotten deprecated over the last couple of months, because everyone sort of just does this themselves.

It tears it out. So, like, you don't really need.

[Speaker 1]
Your own libraries implement this functionality for you, because it really requires you to tune it yourself. So, if you're hosting a bunch of applications, and they all want to configure this properly. Um, I think the right answer is just basically provide them enough of their ability and tooling so that they can go self-service and pick itself themselves, which is kind of the same is true of captioning as well.

Oh,

[Speaker 5]
just just one, just because also the accuracy is going to depend on the application too.

[Speaker 2]
Some more missing critical? Applications. We need a higher accuracy, and you just have to figure that out when your development system, I guess, yeah. So, the problem?

[Speaker 1]
Yeah, I was just gonna say it's an area of a lot of research

[Speaker 3]
just to the threshold setting. Um, I think also like, here. We're looking at static thresholds, so like, for every query, we do the same, uh, threshold lookup. I think there's research that's coming on, about, like whether or not you might need Dynamic thresholds. So, like? Figuring out where in the geometry is this?

It's n-dimensional space of potential embeddings, right? So, like, where are we? And, like, how dense is this area, right? Um, because point eight might work good in this specific area of the embedding? Hyper space, right? But in this area, it might not work so good. So, lots of research coming in here, I think right.

Now, like we see a lot of semantic caching being used for chat Bots, where you have a lot of similar queries being asked. Like, imagine you have like a retail website. Lots of people are asking similar queries, like, uh, you know, will this fit a six foot two men, right, um?

Uh, the accuracy there might be okay if it's a little off, um? Other applications you need to have, ultimately, like very high accuracy, and you maybe aren't going to be able to save as much. Ultimately, just like with casket ratio, you were tuning, like, how much memory do I get my cash?

What eviction algorithm am I using? Am I using these recent newsly speaking news, Etc? There was a lot of tuning involved there, and uh, you know, you're trading on costs. For a bigger cash against, you know, more cash ratio. Now, it's just an additional 100 parameter that you have to kind of figure out.

So, definitely look for additional research here.

[Speaker 6]
Can you speak a little bit to the

[Speaker 2]
conversational history piece, like with the personalization? Like how that scandals?

[Speaker 1]
Personalization, especially with the multi-turn conversations.

[Speaker 2]
Um, and there's another dimension here, which is KB caching. Is this other trendy topic which there's another talk at the same time about KB caching, and we've had it at the same time? Um, we're just trying to just within the same conversation. Just, you know, keep track of all the pre-computed, uh, Transformations that have been happening onto on top of it, which is kind of separate video research for the individual terms.

Um, I, I know some people have been like, oh, you just get like attached, like the user ID and specific context onto it, but that kind of destroys the entire chance of finding a similar search. Um, so we haven't seen people be very effective outside, like building for user memories.

So, like the process of like memory information that some folks talk about is, you know, adjacent and relevant to semantic caching. Is it kind of a similar separate problem, so building those specific per user memories that they can then reference while doing? The generation of the term. It's kind of what we've been seeing folks doing.

[Speaker 3]
Yeah, I think like, uh, semantic caching is kind of the the highest level of cash that you can think of right. If you're taking the whole query and you're trying to find the answer to that query. But there's lots of places to add caching in between, like Madeline, was saying to KD caching when you're actually caching inside of the difference itself, um.

Or, you know, as a pre-pass to the LM, you might be doing some kind of rag lookup or something like that to get those pieces of memory, which is another common use case we see for the same exact problem, but being solved as a pre-pass versus. In this case, we're talking about doing it as a replacement two, the element column.

[Speaker 1]
Thank you.