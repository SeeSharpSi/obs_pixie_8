---
type: transcript
topic: work
---

[Speaker 1]
Hey everyone, I'm

[Speaker 2]
Belle guttman from AWS, and I'm here to talk about strengths. Our open source agent SDK and the journey we took from framework to what we're now calling an agent harness. Why we build strands, uh? Towards the end of 2023, the beginning of 2024, we were building Q developer, our agentic chat bot for the AWS console, and we realized that we kept building scaffolding and writing code on top of what the other one, but we couldn't keep up with the llms, the models becoming more small and more sophisticated.

We wanted to get out of the way of those models. Dozens of teams inside Amazon, and in addition to key developer Hero internal tools. We were all building the same thing independently. The agent Loop tool dispatch context management guardrails, same patterns, different implementations. So, we built a shared SDK, and then we made a bet.

We decided to open source it. Our design philosophy was simple get out of the way of the models. No State machines, no Dives, just a prompt plus tools, and let the model join the loop. We have the tool decorator, an agent implementation, and a single call to instant achieve the agent, right?

Just let the model drive the loop, a few lines of code, any model, any Cloud Apache 2.0. You can swap providers in one line, and your agent doesn't change. The aging code does not change. We launched open source, and the response actually blew us away. We have about 1.5 million downloads a week.

We have almost 6, 000 GitHub stars. We currently have two sdks. We started out with the python SDK. We now have a typescript SDK more coming soon. They're both fully open source, and we've had hundreds of community contributions building with us.

But we learned something from the community recently that the framework that just orchestrates isn't enough. Developers want a full runtime. So, we see this in three separate categories. We've got the behavioral middleware execution environments and opinionated defaults. Behavioral middleware are things like steering hooks that correct the agent mid-loop, not just block the agent from continuing to execute.

There's no other open source SDK that can do this. We have execution environments, a rust-borne shell that's coming soon. It gives sandbox code execution out of the box and opinionated defaults. Things like file system context permissions all just work without configuration.

So, what do we mean by opinionated? What does this mean in practice? We have file system access that works by default. We have a Sandbox that gives you safe code execution. Context management is built in. It's not folded on. Staring lets you correct your agents, not just halt it.

Sessions have pluggable persistence. We have files S3 bulky for distributed deployments. The harness handles the hard part so you can focus on the interesting ones.

Strength isn't just for chatbots. We recently launched strands Labs, which is similar to what we have AWS Labs, but for agentic applications where we try to Showcase both our own internal and any of your Innovative AI projects, using strands or adjacent to something related to using strands. One of the projects we recently launched, there is our physical AI toolkit, robots controlled by agents.

Imagine this pip install five lines of code and you've got a robot arm in front of you. Picking up a cup of water? We integrated with leading Vision language action models vla models, and we're working with many partners on our Edge cloud-to-edge orchestration across billions of devices. And this is all open source.

The architecture is actually pretty simple. The agent's plan in the cloud, doing things like task decomposition, multi-aging coordination, Fleet scale learning, and the robots execute at the edge. They perceive they reason they act with safety, critical operations running locally. It's bi-directional, the intent flows out, feedback flows back.

Everything I showed you and talked about today is open source.

Agents.com, which will direct you to each of these individual sites. And if you want to go deeper, I'll be at the AWS booth later today from about 10 30 to noon for a media expert session. Come on, say hi. I'd love to chat more with you all. Thank you.

[Speaker 3]
All right, our next speaker is going to, uh, talk about something I think is really interesting.