---
type: transcript
topic: work
---


Great! Thanks everyone! I'm super excited to be here, um!

[Speaker 1]
And to talk about our journey over the last decade, uh, with quantity. So, 10 years ago, this month, we put the first Quantum processor on the cloud. And its Evolution, and the evolution of that access has been changed very much by open source. We'll talk about that story, um.

And. Kind of where we're going, how we got there. It's some exciting stuff, that's that's happening now. But before that, I need to step back a second, um, and ask, maybe a more fundamental question or frame. The question, which is, you know, why is it that we might need a new kind of computing and kind of.

What is this Quantum Computing thing anyway? Um. So, the world around us is quantum in nature, right. At the macro scale, the scale of people, chairs, desks, whatever. We mostly don't notice it, but at the microscopic scale, the scale of transistors polymers proteins like this is a quantum universe and the way those systems work the way they interact.

They are dominated by quantum mechanics. Come to understand that world through experiment through classical approximations running many of these running on very large supercomputers. These are all approximations. The digital Computing. We're all familiar with, um, there's a links called classical Computing can never truly capture the quantum nature of these systems.

And to do that, we do need a new kind of computing Quantum Computing. The fundamental building blocks of quantum Computing is a qubit. We may have heard of, right? It's a Quantum bit. These are in some ways similar to trees to in in standard classical Computing, but they operate a little bit differently, um.

Because they have quantum mechanical specific operations on them, like, be able to put them in superposition, use entanglement and interference to do computations of a quantum nature.

[Speaker 2]
And when we have systems like this when we have

[Speaker 1]
processors like this, we no longer need to approximate what's going on. We can actually use the quantum mechanic nature of these systems to give us really accurate modeling and understanding of molecules, transistors, things around us.

There are computational problems today that are easy for our classical computers to solve, and there are ones that are really, really hard. And maybe they are unsolvable, right? But what's actually really interesting is that there's also a class of problems that are hard or even impossible for classical systems, but our Quantum easy?

Their Quantum algorithms that when we have sufficiently advanced quantum computers, we'll be able to solve these easily in things we cannot do with classical computing, so quantum computers will never fully replace classical systems, but they will let us solve new kinds of problems that we were just inaccessible to us before.

That.

That there are other kinds of structured data that these same Quantum algorithms can take advantage of, so there's a whole Space of optimization problems. Things like the traveling salesman problem where there are Quant solutions that kind of actually reach those, uh, better and out scales that we can never do in a classical way.

We think that there's sort of four areas, uh, that we're focused on right now. In this space, um, big kind of pillars here, the first thing I just talked about, right? Uh, these Hamilton simulation these are the molecular protein simulation environment, and they really do. Let us encode the quantum mechanical nature of the systems into problems run on the quantum computers and use that underlying quantum physics to solve those, but There are other problems.

Optimization has these kinds of structures that quantum mechanics and some of these form algorithms can exploit. And we also see benefits showing up in machine learning and differential evasions. You know, differential equations is how we build big scale simulations that do things like aerodynamics, calculations, and our critical important part of how we build the world around this.

So? It's all pretty exciting to stop about where we could get to, and uh, the thing is about a decade ago. If you wanted to go and work on a quantum computer? And do something with the quantum computer. Your experience looked like this. You were part of maybe one of 12 Labs around the world.

Maybe tens of people have access, and it was reading oscilloscopes using labview plugging cables in. And, uh, that's very limited in how we can actually explore what we can do there. So 10 years ago this month, Star Wars day. Coincidentally, uh, we tried an experiment we took, uh, this five qubit processor, um, that's a lithography scan of it there.

Put it on the cloud. Made it available for anyone to sign up. Get access to. And uh, with a simple web UI where you could drag and drop these Quantum operations on it and actually sort of run a small scale Quantum experiment there, um, had no idea if anyone was going to show up.

Um. Two weeks later, over 20 000 people have registered, had to run their workload on this, and uh, we were off to the races like people were interested. This was a place. So?

So, within a year, we release kisket. Um, which is a the Quantum information science will get. It's open source written in Python under an Apache 2 license. And this allows people to build more complicated programs. Um, optimize them, do small scale simulations, and then submit them to real Hardware as a pluggable Hardware interface.

And it works with our Quantum systems online. It also works with other people's. Um, and we invited everyone to join us, right? This is an open Journey that we're coming together, so it's it's out there. It's available on GitHub, uh, and two dates, uh, it's had over 5, 000 research papers published using this as underlying technology, and there's over 7 000 projects dependent on this building.

Additional open layers of this. In 2021. Uh. Something actually pretty exciting happened, which was we broke this 100 cubit barrier. We had these small Cupid devices, but it turns out that that having more than 100 functional qubits is really important. Uh, you can simulate a Quantum processor with less than 30 qubits, probably on your laptop would be less than 50, maybe on a super computer and but the resources go exponentially.

So 100 cubits is a non-simulatable contract. This is real Hardware doing real things you can't simulate on a classical computer. But when with search went out, right? Like you will see, we were tracking. What was the median usage of the environment and people were really, really still using Halloween handfuls of pubis, like scaling these problems up was hard.

And then it changed. And why did it change because we, it was very clear? You need more than just an open SDK. You need open building blocks more open tools on top of this. We started publishing a bunch of things called kiska add-ons. Those are those open tools again.

Open source available under Apache 2 license, sitting out on GitHub. Um, and these are encapsulations of kind of the best of quantum algorithms and research papers that are coming out now so you can start your building blocks further up the stack. The first of these, this SQD algorithm that was a year of research, deep research between researchers at IBM other institutions.

To get to a repeatable solution and then that one out open source and then Cleveland Clinic picked it up and within a couple months responded. Did their own related molecular work and was often right? Um, this is the way that you know the best of open science and open source accelerating Discovery.

Um. You know, I am a python guy. That's what I sort of will write code on when I'm, uh. When I've got my chance. And that's the what kisket was written in originally? Well, here's the thing. It is a wide ecosystem of software out there. Um, and in order for Quantum processing to be accessible to it, like, we need to be able to work with lots and lots of different programming languages.

Lots of existing code bases like C plus plus, Fortran, Julia, Etc, um. And so, last year, you know, again, in part of this journey of open, was, let's make sure that, these fundamental building blocks also were was the vast array of programming languages out there, so the core of kiskit was Rewritten.

In Rust, so it had a native library and a c binding interface to it. That's easily extendable to all of these other programming languages. And so that brings us to today. So where are we today? What do these systems do today? Um. It's kind of amazing when it's happened over the last few months, so I'm going to just show a couple of pieces of research that has come out on these systems.

So, this one is a is a recent experiment, uh, we did it in collaboration with Oak Ridge National Laboratories. It's available on the papers available on archive. You can get it there and what they did was, uh, they have a very specific magnetic Crystal, um. This, uh, this copper?

Crystal that you can see, sort of a picture of up there, and they characterize this thing by shooting a neutron gun at it and watching the Skyrim happen. So, on the left is the experimental results of what that scatter looks like through this Crystal. And in the middle. Here is the simulation of what it should look like on one of our Quantum processors.

And you can see those are matching up really, really well, right? This is the point at which? The quantum system, you being able to take advantage of those Quantum capabilities, can really model and experiment that you can then match later and see the paper.

And the process. The progress over the last couple years on problem complexity you can tackle with the systems that are available online right now has gone up immensely so. This is aggregate work by Cleveland Clinic over the last 18 months of doing molecular modeling. 18 months ago. They were able to build an algorithm on this environment that could do 10 apps.

And then it was tens of atoms and hundreds. And just last month, they demonstrated this modeling of. Trypsin, which is a molecule that's over 12, 000 atoms that they were able to do on, uh, on our quantum systems. This is an 18 month progression. Um, anyone that can, like, look at an exponential curve and kind of see it sitting right there.

Um. So, it's a pretty amazing place to go. And this first decade of open Quantum really has brought us like from this place where we have five simple qubits online. We made that available. Um, people could go and play with it. Um, so now we've got a fleet of over, uh of, of.

Systems that are over 100 qubits. And they're always on. They can solve real hard relevant problems. They've got open source tool chains that help make them accessible and available, and we would never have gotten this far without open source and the open collaboration that sparked on this native ecosystem.

So, I kind of asked the question here. Call action with the fuel, right? What will this second decade of open motto

[Speaker 3]
break?

[Speaker 1]
Um, and a lot of that depends on you. Um, and I encourage you to join in on this Journey. Um, you can get started today with kids kids, uh, and free access to real, but we're upon computers with our open plan, um, the QR code there, and the link, uh, will provide that.

So, the future is. Now, let's make it good, good.

[Speaker 3]
It's pretty cool,

[Speaker 1]
and he sort of mirrors the AI world where we have this physical Hardware investment. I mean, it takes a lot to make on a computer, but everything above it needs of it in all.