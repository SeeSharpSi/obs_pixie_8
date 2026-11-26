---
type: project
topic: school
status: idea
---

# Part 1

## Summary
FireEye and Microsoft Defender for Endpoint are both good solutions, each having a set of pros and cons.

## FireEye Endpoint Security
FireEye Endpoint Security does a good job of tracking files and doing low-level scans. It was made from the ground-up with data in mind, and the logs show this. They can be hard to read but are obviously detailed.
FireEye Endpoint Security also does a good job with implementing simple algorithms to detect various types of attacks. These include rootkits, key loggers, adware, trojans, and more.

## Microsoft Defender for Endpoint
Microsoft Defender for Endpoint does a good job with using lots of algorithms to automate large swaths of a cyber security team's job. This means it auto-suggests remediation steps, automates alert systems, and puts "AI" in front of every word.
Overall it's a good choice for smaller teams, though it still requires an agent to proceed on certain steps. Especially in the case of a successful cyber attack.

## Conclusion
Both of these tools are good. That said, both serve more specific purposes for the other. The charts below will help on deciding, but Microsoft Defender for Endpoint is better for more teams than FireEye Endpoint Security is. Still, FireEye Endpoint Security serves its niche well.
<div class="pb"></div>


|Tool|Capability|Supported|Comments|
|-|-|-|-|
|FireEye Endpoint Security|Correlation|Yes|It does this by tracking file read/writes against a set of rules|
||Validation|No|FireEye doesn't appear to have validation|
||Alert|Yes|FireEye has an alerts dashboard that allows you to see and set up alerts|
||Deep Investigation|Yes|FireEye uses algorithms to detect various types of attacks and scan files|
||Remediation|Somewhat|FireEye provides an opt-in module that has remediation tools|
||Automation|Yes|Most of FireEye is automated, including alerts and scans|
||Threat Hunting|Yes|FireEye includes threat monitoring, though it isn't as in-depth as other tools|
||Integration w/ other security platforms|Unknown||
||Agent vs. Agentless|Agentless|FireEye is mostly used as a "set up once" system|
||OS Support|Linux, MacOS, Windows|Some features are missing from Linux/MacOS, but most of FireEye works on all major Operating Systems|
||Devices not covered|Unknown||
||Cloud support|Somewhat|FireEye has a cloud system, though it costs extra|
||Costs (per user, per server, etc.)|$30 per end-point|FireEye's pricing is based on endpoints|
<div class="pb"></div>

|Tool|Capability|Supported|Comments|
|-|-|-|-|
|Microsoft Defender for Endpoint|Correlation|Yes|It aggregates threat information into an "incident," which can be investigated with "AI"|
||Validation|Somewhat|It runs through their cloud system, meaning it's possible but not local|
||Alert|Yes|The AI system gives alerts based on file/wire scans that match rulesets|
||Deep Investigation|Somewhat|Gives details about files that correlate with alerts|
||Remediation|Yes|It includes remediation tools and automatically associates remediation steps with investigation scan alerts|
||Automation|Yes|Most of this program is automated|
||Threat Hunting|Yes|Gives information or correlative files and alerts|
||Integration w/ other security platforms|Unknown||
||Agent vs. Agentless|Both|Can be set up as agentless, but is best with an agent|
||OS Support|Linux, MacOS, Windows|It even supports WSL|
||Devices not covered|Unknown||
||Cloud support|Yes|It's Microsoft, so yes. Everything is needlessly connected to the cloud|
||Costs (per user, per server, etc.)|$3.00 or $5.20 per user|Per-user pricing depending on plan (Plan 2 is newer with "more features")|
<div class="pb"></div>

# Part 2
![[Pasted image 20231203151823.png]]
* This image shows that both the server and my client are using HTTP 1.1.
* The server's IP address is 20.122.241.50. My client/computer's address is 192.168.1.7
* The server is initially returning 545 bytes of information. Though, it's pinging back with more from HTML script and style calls (both return 1083).
* Traffic analysis is important in security because it allows you to see who is accessing what, when, and how much of something. This greatly helps companies find bad actors; if someone accesses a database, you know what IP address was used and whether it was internal or not (well, usually).