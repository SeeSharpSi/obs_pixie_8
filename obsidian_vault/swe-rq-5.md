---
type: assignment
topic: school
---

# RQ 9-1
1. Performance is one of the most important characteristics of software implementation. The meaning is in the name: a sports car can be comfy, but to fit the name "sport" it needs to be fast. A slow sports car is bad. Software is similar in that it can look nice but needs to run well for users to enjoy using it (or even be able to practically).
2. Completeness is the goal of meeting all system requirements. This seems simple, but how complete an implementation is can be a good reflection on the initial requirement-eliciting phase. Some clients want things that are impractical. Do you fail to meet these requirements, or tell the client they aren't possible from the start?
3. Readability is the idea that code needs to be easy to understand by other programmers. This means that someone can hop into a codebase with little-to-no prior knowledge and figure out what's going on (which is very hard to do in Java because it's built around abstraction).

# RQ 9-4
False. Some applications are just fast (e.g. booting up an http server on GoLang). Most applications should be written with _some_ performance needs in mind, but especially simple programs probably don't need to.

# RQ 9-5
1. Duplicate Code
2. Large Class
3. Switch Statements

# RQ 9-8
1. IaaS (Infrastructure as a Service)
2. PaaS (Platform as a Service)
3. Cloud Application Services
4. Cloud Services for Developers

# RQ 10-3
1. Inspection
2. Reviews
3. Walkthroughs
4. Dynamic Testing

# RQ 10-6
1. Once software conforms to a preset standard (e.g. IEEE, W3C, ETSI).
2. Once software is "performant enough." This means that it runs on minimum spec hardware at a reasonable speed (e.g. a videogame runs at 60fps on a Raspberry Pi 3). This can vary a lot depending on the application.

# RQ 10-7
## X
| Input | Output |
|-|-|
|-1|Invalid|
|0|Valid|
|1|Valid|
|MAX_VALUE|Valid|
|MAX_VALUE - 1|Valid|
|MAX_VALUE + 1|Invalid|

## Y
| Input | Output |
|-|-|
|-6|Invalid|
|-5|Valid|
|-4|Valid|
|15|Valid|
|14|Valid|
|16|Invalid|
