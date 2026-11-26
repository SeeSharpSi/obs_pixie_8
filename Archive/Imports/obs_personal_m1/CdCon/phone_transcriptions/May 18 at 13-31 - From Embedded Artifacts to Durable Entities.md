---
type: transcript
topic: work
---


Hey everyone. Also, I'm Bill Powell.

[Speaker 1]
I work at

[Speaker 2]
Apple on as a software engineer on the speaker team, and I also maintain a few events project. So today, we're going to talk about the journey I took across the execution context from megabytes, sometimes gigabytes down to field bias.

[Speaker 1]
So,

[Speaker 2]
I want to start at the beginning. So, when I first joined Apple, I wanted to understand exactly what was happening under the hood for anyone unfamiliar spiritual is a open source. It's confused delivery platform. What I found was that speaker carried a huge amount of racial state inside his execution context.

That context moves from stage to stage service to service and eventually back to the user through the UI. The key issue was duplication. Artifacts was not represented as a lightweight reference to durable state, but they were embedded directly into the context. So, when multiple stages reference the same artifact, spiritual could carry that same data over and over again.

That meant execution context was much larger than the option operation actually required. A lot of the data in the context had no meaning to the current stage. It was just along for the ride.

[Speaker 1]
So, I want to first talk

[Speaker 2]
about the old model, what it looked like password. So, when a pipeline triggers for deployment, the usual flow starts by baking this artifact from an external Source, so Spinnaker would then pull that artifact down. Prepare for deployment and eventually stores it as an embedded base64 object. Yes, embedded basis before, so that means the full artifact now lives in the executioner, uh, context.

So, from that point forward. It is carried through the execution life cycle. From stage to stage. From service to service and eventually all the way to deployment. Speaker, then record what was deployed. So, that means the same artifact is duplicated again. The problem is that the embedding the large artifacts directly in the execution context makes every execution State expensive.

That means rendering the pipeline to serialize the deserialization. Persistence retries all repeatedly. Process the full artifact payload. Until the pipeline reaches the terminal State.

Now, imagine a fan out kicks. A single artifact that touches four regions or wants to deployed four regions, right? So the kubernetes Manifest will use kubernetes as an example may only defer by a single name space, but branches. The bridge that of the the four regions would then have the full, full multi-megabyte, uh pipeline, or sorry manifest through the whole system right, or would be multiple, uh, would be?

Express that for four regions there.

So, now that we understand the problem, the? Direction actually became pretty clear on what we needed to do so. Instead of embedding this full artifact, we just want to. Reference it, right? We don't want to embed. We want a reference. So, the step, though first step, was actually the artifact store.

Instead of carrying that full artifact, what we wanted to do was, instead, replace it with a reference of, uh, what we call a artifact URI that

[Speaker 1]
alone

[Speaker 2]
actually compressed most applications, down from 60 for small pipelines and 80 for large. Then, we two get one step further, which was the entity store the so the entity store is just a different strategy of the artifact store, so the artifact store what it's doing is, hey, I want to match for artifacts that are embedded base64 and then store it.

The entity store is, like, hey, I want to match against a specific set of criteria that the user or the the, uh, the Spinnaker indicators, uh, uh, would want to check against and then. Get stored, though, so you can think about it kind of like this. So?

[Speaker 1]
Well, pipeline runs.

[Speaker 2]
Is this something that we want to store in the context so? Is this a manifest? No, okay. Is this a manifest? Yes, okay, let's store that. So for more, more real world complex pipelines. This pushed reduction even higher, so this was an additional 85 percent.

So, a lot of thought went actually into where this change should live. So, the goal was not to reduce the payload size, but the goal was to reduce a payload size without enforcing everyone to. Uh, you know? Without enforcing everyone to, um, you know, Force Spinnaker to? You know, change the implementation of stages, services, and pipelines.

Uh, implementation to understand what the new storage model would look like, so instead it would then just kind of be under the the hood or make that impact as as least invasive as possible. So we landed on serialization, because that is where execution already, uh, x's, and enters the system, so every time Spinnaker would persist, transfer, or reload the contacts it has to serialize and deserialize that data.

So, on serialization? And our fact would then be instead of persisted, uh, to the context. Would then be swapped out with a reference. Then on deserialization. We choose what microservices would then expand those artifacts. So the the the system that was interested would not care about or would continue to be would continue to work as intended without any knowledge of of this reference URI.

So this was a main maintainability win, and it would allow Spinnaker code to behave exactly the same.

[Speaker 1]
That changes the slides where your model.

[Speaker 2]
Wait, was this little Maria on this side? I'm trying to scroll down, but it didn't allow me to. Keep going!

[Speaker 1]
This one. Yes, yeah,

[Speaker 2]
okay. Okay, so now that we understand the problem, the direction we can't pretty clear, it's not referencing, is a reference to a rod. We give the, uh, six to eight percent, uh. And then want to go through here. Key design choices. So, um? I mentioned that serialization was kind of the the Crux here of.

Of making it transparent to spiritual, because when you when you serialize that allows us to then make the references. Uh, what allow for the references to be serialized, or the artifacts are serialized to references and then deserialize back to to, um, the artifacts when they're needed.

I want to talk about the reference format, so the reference format is actually application for slash context hash. So, the important bit is actually the context hash because it makes a retry is actually an item home, so that means you don't want to re-upload that artifact again, right? So we can use that context hash to say, hey, did we upload that already?

Or yes, we did, then we don't need to do it again, right? So, because very, very cheap that way, so manifests get their own type. So we have artifacts, which is now represented as remote base64 and then manifest to be represented as something completely different or not different, but remote, not base64.

This would allow for, or the reason why, that was done is because we don't want breaking changes for remote a64, because if we start applying that, you know, remote mapping basis for remote map base64 might have different implications that might introduce breaking changes? So, we wanted to keep

[Speaker 1]
it simple there and be safe.

[Speaker 3]
So, with any architectural trade-offs, there's always.

[Speaker 2]
There's always the challenges, right? So the biggest win is actually size, right? So we, we took this massive size of sometimes gigabytes down to megabytes down to kilobytes. We now have this layer of indirection, so that means that any time that you you encounter this reference and you want to use it.

You now need to fetch it right so that that cost is is in Direction. And at any stage I actually need to. You know, fetch that now requires a a round trip and a registered Handler, so a Handler introduces a new failure mode, which has to be be able to be observed and and managed.

So, to get the this is kind of the recommended migration path that that I think a lot of people should start using because it it just makes the blast raise a lot a lot smaller. If there are any issues, so you start with a a store for your most expensive applications.

Don't turn it all on just for everyone to start with. Very filtered rollout for just the most expensive and then. Once you are comfortable with that, change is slowly enable it through the filter filtering, which you see right there and then once. Once those old, those old executions would then slowly start to drain from that expanded view.

Now, down to this small reference view. And then, once the, you can determine that that is stable. You can then start rolling it out for more users.

So, what does this unlock? So this unlocks something that's very critical. Is that it allows for the pipeline semantics to be separate from the stored semantic, so that means the storage back end can become right now. It's S3, but that could be something different in the future, right? So right now, a test three, but that could be SQL.

It could be, you know, whatever you choose in the future, and that can just be configuration option. And I want to call out that the your eyes, purposely generic, because this out opens the door for so many different, uh handlers, to then use a different way to store a particular, um.

Uh, attribute. So right now, we mentioned that kubernetes manifests are not silver,

[Speaker 3]
but you can store some other attribute or the whole. The, for example, what we did as a kind of a thought experiment, what is the whole thing? The whole execution became a. Two minutes, two minutes. The whole thing became a reference, right? The front end didn't work, but the back end did.

So that just means the front end needs to adapt some of those changes, right? But you could store everything and lose my point. So?

[Speaker 2]
I want to give a little bit of time for some questions. I'm sure there are of of the entity swords, and just in case. So, yes, did

[Speaker 3]
you

[Speaker 1]
see? Did you start off with like the because I don't? I should start off with that question. Yeah, yeah, yeah, so I'm back, and how many people were putting by that clock. Yes, yes. So, a big problem here was, uh, oh uh, Superior for Master Pipelines would cause.

[Speaker 3]
Booming, which is out of memory, right? So, so that that helped by replacing by moving the artifacts from the context, which reduced the size by first 80, and then again that 80 shrunk down by another 880 solve the umi problem. So, um, was there any questions?

[Speaker 2]
Yes.

[Speaker 4]
Was there a performance price you? You change from immediately available to medium to go somewhere else. Did you get bitterness from people? Oh, you slowed me down.

[Speaker 3]
No, because you would see a massive speed increase for things that didn't need the artifacts. Most stages actually don't need the artifact, right? It's only deployment. So, all the other stages sped up, and the only part that slowed out was deployment, which is at the very end. So, overall, on average, you get a huge win on on on speed.

[Speaker 5]
This, um, after this, why did you choose to go with, uh, with the custom

[Speaker 4]
Uris with with the shows, and not some, like the URL, for example, from from the other specifications that, you know,

[Speaker 3]
package column, some examples. Oh, pearls, yes, yes, yes, pearls. So this was chosen just for, um.

[Speaker 2]
Because Spinnaker manifests could have differences, uh, on the content, right? So, that's what we're showing. We're not showing just the artifact itself, or we're showing the content within the artifact so that the

[Speaker 1]
the the the the difference there is that if we went with something like Pearl, it's a little bit too, um. It will allow for too many collisions, so we wanted to be a little bit more granular. So that's, that's the reason. Does that help. I don't know if, so, like, like we didn't know at the time Pro, would allowed for that granularity.

So that's why we chose this. So, Steve, we gotta stop. We got our next speaker. Oh sorry, yeah, yeah, yeah, sorry. Sorry, all right. Thank you. I appreciate it.

Oh, okay, okay.