---
type: assignment
topic: school
---

#school #IT4823 

# Part 1
## 1.
The main difference between static and dynamic code analysis is the running state of the code. In static analysis, code is inspected before it's run. During a dynamic analysis, the application/code is inspected while the code is being ran. From a developer's perspective both are useful; static allows changes to be made before major errors occur, while dynamic allows real-world issues to occur. Both have pros and cons (and both should be used, to some extent).

## 2.
### SonarQube
#### Overview
Sonarqube is a company that produces a CI/CD platform for developing "clean code" and has a priority on security and code quality. SonarQube's software suite includes a [linter](https://www.sonarsource.com/products/sonarlint/), [PR analysis](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/pull-request-analysis/), [quality gates](https://docs.sonarsource.com/sonarqube/latest/user-guide/quality-gates/), and more. Unfortunately they push hard on clean code with fairly vague terms like "clean code is secure" and "clean code applies to all code." The ideas behind clean code are cool, but Sonar shouldn't sell them as something in house; we've all used prettier, and we've all made modular, abstracted functions.
#### Dynamic vs Static Analyzer
SonarQube prioritizes static code analysis using their [SonarScanner](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/overview/). They have implementations for various build systems, including Gradle, .NET, Azure, and more. During analysis, SonarScanner requests data from a server and scans the files provided, resulting in a report (basically an LSP).

#### Vulnerabilities identified (SQLi, etc.)
SonarQube includes software pertaining to cybersecurity; namely, their [security engine](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/security-engine-custom-configuration/) that's included in the enterprise edition of SonarQube. This edition allows users to check the paths their code pulls data from (e.g. to prevent injection attacks), allows testers to use custom validation, and allows developers to use passthrough to color their data as sanitized or unsanitized. This is mainly for preventing code injection.

#### Software Languages, supported. Tools, etc. supported
SonarQube supports 33 "languages" (they include things like XML), though language support depends on the version you purchase. For instance, C isn't included in the community edition, but is in the developer edition.

#### Costs
SonarQube provides several editions. Commercial editions are priced per instance, per year, based on lines of code. The Developer Edition starts at $150/year for 100,000 lines of code, and can be extended to $65k/year for 100M lines of code. The Enterprise Edition starts at $20k/year for a maximum analysis of 1M lines of code, and can extend to $240k/year for 100M lines of code.

#### Other Advantages/Disadvantages
SonarQube seems nice, but its main draw is clean code. The current trend in development lends a lot towards better practice, rather than better post-code linting and prettier-ing. WebDev would definitely enjoy SonarQube's features; they love using dot files to create nicer configs and code. But backend devs might differ, depending on the company.

### Vercode
#### Overview
Veracode is SaaS company that offers both static and dynamic code analysis. It is made to be modular; even the [home page](https://docs.veracode.com/r/Getting_Started_with_Veracode_Products) of their docs talks about building an inventory of third-party components to create your own CI/CD platform. Their main focus is on scanning APIs.
#### Dynamic vs Static Analyzer
Like mentioned, Vercode provides static and dynamic analysis. Their static analysis platform is a SAST solution that is specifically built around tests and being integrated into an already created CI/CD pipeline. It is used to make sure code adheres to preset guidelines (e.g. linting) and conforms to security checks.  On the other hand, their dynamic code analysis (or DAST) solution is meant to deliver broad code coverage and APIs. It targets RESTful APIs and "web applications" (so APIs, again) to see if real-world responses and results are correct and predictable.

#### Vulnerabilities identified (SQLi, etc.)
Veracode mainly scans APIs that you've made. Unfortunately, getting security tests for third-party integrations requires direct contact with the Veracode development team ([source](https://docs.veracode.com/r/Request_security_tests)). That said, Veracode does offer manual penetration testing that simulates real-world attacks on an application in its runtime environment.

#### Software Languages, supported. Tools, etc. supported
Veracode supports 32 languages/platforms. Unlike SonarQube it doesn't lock support for certain languages behind a paywall, meaning users can use Veracode's scanning tools on any of its supported languages with no extra fee.

#### Costs
Veracode doesn't have pricing on their website, but their [contact](https://info.veracode.com/request-quote.html) page says that they can lower the cost of exploitable vulnerabilities from 500 to 7 pounds "per vulnerability" (this statistic isn't useful at all, but it's the only quote they have about pricing I could find).

#### Other Advantages/Disadvantages
Veracode seems like a good system to scan APIs and do *some* static code analysis. The main draw seems to be their dynamic analysing and how they can mimic real world attacks to test real world system static code analysis. Another draw seems to be their dynamic analysis and how they can reproduce mimic real world attacks to test real world systems.

### Compare
While both of these solutions seem fine, SonarQube seems compelling. Veracode doesn't have documentation on their homepage (you have to search for it with a search engine), and SonarQube has pricing. SonarQube also seems slanted towards developers; they advertise what modules they have and how to use them in a more direct way than Veracode.

#### Static/Dynamic Code Analysis
If a company needs dynamic code analysis they should use Veracode. Veracode offers some useful features like penetration attack imitation, and the SonarQube doesn't seem to offer comprehensive dynamic code analysis.
Still, SonarQube seems to have better code analysis. Veracode doesn't go in depth on their static analysis, whereas SonarQube allows you to use their modules directly in build systems.

#### Vulnerabilities Identified
Veracode has both static and dynamic code analysis, meaning it will probably catch more vulnerabilities. That said, SonarCube has support for more languages and allows scanning for maintainability; something that is probably fake, but pretty cool if it works. Both of these things are extremely important in preventing and catching vulnerabilities.

#### Software Languages, Tools, etc. Supported
SonarCube supports a few more languages and allows direct integration into build systems, while Veracode very openly supports third-party plugins. Besides this their language/tooling support is extremely similar.

#### Costs
SonarQube has an odd price bracket; they lock out entire languages for lower tiers, and charge based on lines of code instead of data. On the other hand, Veracode doesn't have pricing but seems to have a better, non-locked-out system (though that's somewhat of a guess; I can't see their pricing).

#### Which is better
If someone needs dynamic code analysis they should use Veracode. Otherwise, SonarQube has a more compelling offer (disregarding pricing, which is an unknown for Veracode).

# Part 2

## Question 1
A function stack is a type of data structure that adheres to the Last in First Out data structure methodology. It's also the name of memory allocated by the programmer inside of code, rather than the heap (memory allocated by the runtime).
Pertaining to strcpy(): the code in the assignment doesn't work (see picture below) because the string being copied includes the nil byte `\0`. Let's assume the code is modified to work using `mybuffer[11]` instead of `mybuffer[10]`.  When `mybuffer[11]` is declared, it allocates 11 empty "boxes" of memory that each consist of 8 bits (one byte for each `char`). Then, strcpy() assigns each `char` in the string to one of these empty memory addresses allocated by `mybuffer`. Technically this isn't using push/pop methods, so I assume the question is asking about stack memory, as opposed to heap memory. Heap memory is allocated by the runtime (JavaScript would be V8/Hermes, Java would be JVM, etc.), whereas stack memory is allocated by the programmer (this includes declaring variables, creating functions, etc.).
strcpy() explained: Let's say `mybuffer` points at the memory address 102. The first `char` in strcpy() is assigned to this address. Then, since `mybuffer` is of type char (8 bits), C finds the next memory location in the array (102 + 8 = 110). The next char in strcpy() is assigned to this address. Rinse and repeat.
I thought this image would be useful:
![[Pasted image 20231007230359.png]]
Here's a drawing of stack memory allocation:
![[Pasted image 20231008140021.png]]

## Question 2
The code is not safe because strcpy() doesn't check if the memory the string is being copied to is large enough. This could result in buffer overflow (or my favorite website, stack overflow).