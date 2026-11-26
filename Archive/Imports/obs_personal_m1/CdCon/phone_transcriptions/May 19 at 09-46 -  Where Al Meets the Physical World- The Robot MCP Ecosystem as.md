---
type: transcript
topic: work
---

[Speaker 1]
Involved in the mcp community for quite a while, which is crazy in that. It's not here at all, but one of the things that's interesting is. MCP has always thought of, you know, connecting, you know. Systems and data software sets. But our next speaker is actually using mCP to connect to the physical world of Robotics.

Our next speaker is Rohit, uh John varghese. He is the director of systems engineering at contoro robotics. He is the co-creator and maintainer of the Ross mCP server, uh, he's going to talk about mCP ecosystems and robots as an open bridge between the Ai and robotics. Please, welcome, real bad.

[Speaker 2]
It's good to be here.

[Speaker 1]
Uh, just for mic objects to. If you could hear me, I'd like to get to know who I'm talking to so.

[Speaker 3]
Uh, just a quick show of hands. How many people here are actually, you know, familiar with mCP and used it? Okay, that looks like most of us in here. All right, how many people, uh, have worked with robots? A good number, uh, know what? Ross the robot operating system is.

Okay, perfect. Uh, I guess with that, I can jump in. And before jumping in, who am I?

[Speaker 4]
Uh,

[Speaker 3]
I'm I consider myself a roboticist. I was part of the founding team at harmonic bionics, where we did, providing exoskeletons as a medical device took it from NSF funded research concept to appear registered product. It's in hospitals today, helping people recovering from stroke and spinal cord injury. Um, I'm also part of the founding team of control robotics.

That's where I am right now, working with robotics for the warehouse. Proud Longhorn, briefly faculty at the University of Texas at Austin, which was probably the most rewarding piece of everything on this slide. I physically couldn't take the long hours alongside a startup. But why, I'm here today is as part of an open source project using mCP to bridge agent AI and Robotics.

So, before jumping in some disclaimer? Is, you know, in the physical AI world, we have end-to-end policies and vlas Vision, language action models, advancing on their own track, LED from the self-driving world, but also starting to penetrate the robotic space quite heavily. Uh, today. What I'd like to talk is an alternate path.

Uh, not applicable everywhere, but applicable in a lot of spaces.

[Speaker 2]
Uh, we're bringing AI agents to already existing robots deployed on the field via MCP.

[Speaker 4]
So

[Speaker 2]
I, typically, when I'm talking to roboticists, I start by describing what mCP is. I don't think I need to do much of that in

[Speaker 1]
this room.

[Speaker 2]
I then introduced robotics middleware with Ross as the example and then go into how an mCP server you know connects the two.

[Speaker 3]
So, I really skip past this. What is mCP? It's the way that you connect. Agent to Ki or AI AI models really to external tools, it it, you know? Before mCP, you had a host of bespoke connectors that went between. Everything you had to every model and I'm old enough to to remember when that was how external tools were for computers.

Mcp promised a unified.

[Speaker 2]
MCB promised a unified connector, which allows you to essentially connect any tool that you build to any model. And enables you to get your agents and complex workflows on top of that existing infrastructure. All of the good things that we know about it. Coming to Ross the robot operating system?

It's really hard to describe what it is. It is so many things, but in the context of today's talk, I'd like to focus on one part of it that it standardizes communication between different nodes that you might have inside the robot system, so you could have Hardware drivers that run your Motors that, as one node, you could have your perception stack.

Multiple nodes starting from your cameras to different different nodes that process it. You could have a motion planners for robotic arms. You could have a slam that gets you mobile robots. And within Ross or this middleware. You have tropics, Services, actions, and other ways of communication between these nodes.

Again, Ross is. It's hard, it's hard to see. It's so many things, but another piece that I really love is the vast library of community build tools. Of all the things that I told you this. Now, there are examples in Ross, like, move it for motion planning of robot arms lab that does it for mobile robots.

And so, bringing the two together so. Again, structural Frost. You don't need to go too deep, but bringing the two together. Essentially, we could write a mCP server. That on the back end is plugging into existing robot middleware. And on the front, exposing that as an mCP server to your AI models.

Essentially, right now, you've got something that's compatible across AI systems, cross-platform. And as a roboticist. What excited me the most is? It plugs into existing robots without any custom code required. Because using existing middleware existing protocols that go through again, taking Ross is this example. I did not need to write or modify the other nodes on my robot.

I just had to add one more. And. Created a surprisingly emergent behavior. It surprised us as we first started it and. The response. I'm going to actually say over here. This is my first contribution back to the open source community, and it's been quite humbling. The the growth we've had since we went public in September as a, you know, collaboration between us and the University lab.

But I want to point out over here that this is not really a strength of what we did, but right place, right time, right? Idea. The. Agent capabilities to existing robots. You can really create some emergent Behavior, so at this point, I'd like to invite you to see some examples of this.

Um, going to feature a lot of what I saw in the community and one of our world. So, this is Wilson. It's built by. It's a little custom robot completely designed and built by Trace Laru at the University of Texas at Austin. And it's a mobile base. It's got a little robot arm on it.

It's got it's. It's running Ross under the hood to to handle most of its internal operations. But then, using Ross MCP added Gemini as a layer on top of it. Now, I'll let you see some things that. That he's done with it. Do we have the audio on that?

I'll just jump back all right, let's go. Hey Wilson, can you give me a Coke from the mini fridge and bring it to the living room? Got it. I'll get you a code.

[Speaker 3]
I'm Roger Coke to the voting room.

[Speaker 4]
It's the goal. Thank you for some robotics student, right? You have your your little robot helper that gets you your quote from mini fridge. But over here. What you had him do?

[Speaker 2]
Is, of course. You can recognize Gemini doing, handling the interaction, the voice interaction to the robot command. The navigation across the room is handled by nav2, which is a slam package within Ross. The when the fridge is open, I saw a different demonstration of his where there was a Coke and a seven-up, and so the photo taken by the robot goes back up to Gemini, which says the Coke is on the left and

[Speaker 1]
aims a robot that way. Okay, the Coke is now centered in the frame, grab.

[Speaker 2]
So, a really nice interplay between the two. I'm gonna jump to the next example. This was asset control. Now, we're coming to Industrial robots. So, here I'm using Claude. I've got robot MCT connected to the robot. And it's vanilla cloth? No, no pre-training, but I have given access to the technician manual, and I'm going to say, go debug my robot.

And that's a vacuum gripper. So, what you're going to see is testing the old system there.

[Speaker 3]
After exploring,

[Speaker 2]
it's realized how to control the robot. It's enabling the valves. Reading pressure sensors. And then from the manual. It detects that the red values are too low. Going into the manual decides to perform more tests to isolate. Where is the fault? Opens, and it closes a few more valves, reads the pressure.

Analyzers and summarize these as language models do very well. Correctly identified. The issue told me a leak and my favorite part over here. Is. It recognizes that this is by the pressure reading when it opened just that zone. Being extremely low comes back and tells me this is a big leak, so you're not talking just like a crack in your holes.

One of your cups has fallen off, or the hose has been unseated. Go and spend, and this is something that I now have. My my field crew run periodically. Just run the group adjusts, and it finds a small leak somewhere, isolates it to a Zone, and says, go inspect that.

It's something I use for debugging when I'm when I'm working on on robot. It's like, oh. My game plan didn't work. Just examine it. Find out where in the whole system you've got the problem. There's other people in the community.

It's like, there's one more time. I'll be patient. There we go. There's other people in the community who have. Who have used this on mobile robots. So, on the left, you've got controlling and orchestrating a drone. And nung bin over here has has actually done this even Outdoors again using other packages of Slam and other forms of navigation involved in Ros to navigate several miles, draw a circle, go in circles at a one mile radius around our building.

And on the right, controlling a unitary goal. If you look at the prompt that Arab gave over here, it's extremely vague, it says. Do various clips and shake a hand? And what you had persona doing over here was again going through the the API that this little robot has and sees that backflip is sender command.

Three shake hand is send a command 22. And it's, it's doing those things.

[Speaker 3]
Also in simulation. So over here. You've got two robots being orchestrated by the same model. One to push the box out of the way. An obstacle out of the way and then bring the other one into that space. Now that the obstacle is cleared and use the cameras to see what you can see.

It's a simple demo is only a bad

[Speaker 2]
extinguisher, but

[Speaker 3]
The the the research that they were proposing at hardcore lab. They were our collaborators who actually worked with us from the early days of the mCP was that this can be used probably to send your your little robot around the warehouse and look for anomalies. Look for open doors and other things.

Tying all this together, kind of the vision that I'm hoping to see with. This is given an option to combine the reasoning and adaptability of model AI as it matures. I forgot to mention. Previous example was using a local model, so not the client was two ones. And connecting that to the repeatability and maturity of Robotics tooling today.

[Speaker 2]
Now, we just joined the agent of AI Foundation under the next Foundation. We hope to support, you know, I have a lot to learn about about doing things open source, but I hope to actually. Uh, join the effort and something that makes me personally excited for this is when you use this modular approach.

All of the safety layers, the new bake into robots, especially involved in industrial robots, are preserved. The agentic layer is not able to override them and allows you to be reliable and trustworthy. And another piece that we already saw in the examples today is that this lowers the barrier to entry for agent and physical AI orchestration.

Uh, by essentially putting together modules that already exist and having the emergent behavior that. Many people today believe is only possible with end-to-end trained

[Speaker 1]
plas and models.

[Speaker 2]
So, if I were to leave you with one message, it's that physical AI doesn't always need the bigger model. Sometimes, it just needs a common interface. And. Global mCP is one such example of that. Where we took reasoning and orchestration from both local and Frontier models. Combined with the control of existing mature middleware.

Open and modular. It allowed us to skip retraining using just vanilla vanilla AI models without any custom glue. And again, I have to say that this is not physically able is so big. That no one approach is going to solve all problems. So, vlas internet approaches learn policies extremely powerful and have high use where low latency and experience Market.

But there could be a vast space where mCP could enable existing middleware. To create emergent Behavior. And with that? Thank you. This is an open source project, so please do get in touch. Try contributing and thank you very much.

[Speaker 1]
That was, uh, super cool. I mean, I kind of imagine where this goes in terms of, like manufacturing Systems. I'm gonna have to talk Rohit into, uh, joining one of our mCP dev days events and our agent con to come back and talk and bring your robot friends next time.

Yeah, yeah, we. I think that, you know, this is something that a ton of the people in EMCP Community are really interested in an epigenetic eye Foundation. Um, there's just been a lot of conver.