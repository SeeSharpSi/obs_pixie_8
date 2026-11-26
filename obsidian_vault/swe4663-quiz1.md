---
type: study
topic: school
---

# Chapter 1 
Project content and deliverables 

## Objectives 
* Why requirements elicitation, analysis, specification, and agreement should be completed prior to planning 
* Why software project managers must ensure that project requirements - in the form of (1) the deliverables and (2) the characterization of the needs to be satisfied by those deliverables - are available and properly prioritized 
* Why software project managers should focus their energy on requirements management and let the software engineers and analysts perform the requirements development 

## Gathering and Analyzing Project Requirements 
* **Software requirements** 
	* The needs and the wishes of the users and the customers that may be delivered as solutions in the form of software 

### Potential Pitfalls 
* List on pp. 22.6-23.1 

### Completing the Requirements Specification as a Separate Project 
* Sometimes initial plan as requirements as sole deliverable 
* Need to state requirements of requirements gathering process (lol) 

## General Requirements Management Activities 
* **Software Prototype** 
	* A software model created to represent a user interface or a function for the purpose of better understanding the requirements and the feasibility of the proposed solution 
* Figure 1.1 - General Requirements Management Activities (p. 25) 
* Project Managers may intervene, but software engineers should perform the tasks in Figure 1.1 
* Entrance Prototyping Criteria List (p. 26.2) 

## Types of Requirements 

### Project Deliverables 
* List of example artifact deliverables (p. 27.2) 

### Project Needs and Their Characterization 
* Second type of requirements identifies the needs, characteristics, and constraints for which the software project must provide the solutions 
* List of some (p. 28.2) 

### Review and Approval of Requirements 
* Project Manager ensures first set of requirements is clearly defined, understood, prioritized, and agreed upon - have all parties "sign off" on them 

## Internal Requirements Generation and Prioritization 

### The Prioritization Process 
* Figure 1.2 - A general prioritization procedure (p. 30.1) 
* List of activities resources are set aside for (p. 30.3) 

### Role of the Software Product Management Board 
* List of where candidate requirements come from (p. 31.3) 
* **Software Product Management Board** 
	* A group of people chosen to assist in the determination of priorities of requirements and the grouping of requirements for product releases 
* List of areas of interest for picking people on board (p. 32.2) 
* **Release Management Council** 
	* A group of people chosen to assist in managing the entire software project from goal setting to the final product release 

## Quick Estimates and High-Level Requirements 

# Chapter 2 
Task Analysis 

## Objectives 
* How the Work Breakdown Structure (WBS) is used to analyze the tasks that are needed to develop the deliverables specified in the requirements 
* How effort, in the form of time and resources, should be assigned to the tasks shown in the WBS 
* Why the preliminary schedule, with milestones, developed from the WBS is a key part of planning 

## Work Breakdown Structure 
* Once the requirements specification is understood and completed, the software project management team is ready to start on the Work Breakdown Structure (WBS) activity 
* **Work Breakdown Structure (WBS)** 
	* A depiction of the project in terms of the discrete pieces of work needed to complete the project and the ordering of those pieces of work 
* Initial WBS considers the "big picture" - it's high level 
* They can use the WBS to form the initial project schedule, which includes tasks, dates, effort 

### Steps in the WBS 
* List of steps (p. 38.6) 
* Figure 2.1 - Flow of WBS to schedule 

## WBS in Practice: Introduction to an Example 
* Example that has two deliverables: Executable code and help text 

### Deliverable 1: Executable Code
* This is on p. 40.4 

### Deliverable 2: Help Text, Usage, and Reference Information 
* This is on page 40.5 

## WBS Task Refinement 
* Refinement of design activity A may result in a table such as Table 2.1 (p. 41.4) 
* Table 2.1 - Subtasks within the Design Activity (p. 42.1) 

### Task Sequencing and Sequence Diagram 
* Is there sequencing between tasks? 
* Figure 2.2 - Sequence diagram (Sequence relationship of activity A subtasks) (p. 43.1) 
* **Sequence diagram** 
	* A diagram that shows all the tasks required to complete an activity ad the order in which those tasks must be performed, including the depiction of the tasks that may be performed in parallel 
* Construction of sequence diagram List (p. 43.4) 

## WBS Time and Resource Assignments 
* Guideline to WBS refinement level on p. 44.3 

### Units of Task Measurement 
* Smallest task done in <1 day = 1hr units 
* Smallest task done in >1, <5 days = 1/2day units 
* All other should be days 
* Also find work volume unit 
* Table 2.2 - Example of Historical Information 
* Figure 2.3 - Subtasks with estimated times 
* "Critical path" is the longest path from start to end; other paths allow for slippage (covered more in chapter 16) 

### Task Estimates and Task Assignments 
* In Figure 2.3 time unit should be 1/2 days 
* Next, we apply resources to each task, steps List (p. 47.4) 
* Table 2.3 - Subtasks with Time Estimates and People Assignment 

### Milestones 
* **Project milestone** 
	* A significant even in a project that occurs at a specific point in time 
* Milestones are larger, elevated "things" to be accomplished 
* Table 2.4 - Subtasks with milestones (further enhancement of Table 2.3) 

## WBS Iteration and Acceptance 
* Two areas that require extra care in the WBS Process: 
	* Task effort estimation 
	* Inclusion of all relevant tasks 
* Review Process achieves two things on p. 51.3 

# Chapter 3 
Goals and Measurements 

## Objectives 
* Why project and product goals should be specified during the planning phase 
* Why goals should be expressed in the form of measurable attributes that have specific metrics 
* How most project and product attributes require extensive analysis before an appropriate metric and corresponding measurement step can be defined 

## Project Attributes 
* Specify characteristics of deliverables 

### Preliminary Goals 
* Example List (p. 54.2) 
* Without this recasting of the goals, one would face the issues of "what to monitor" and "how to monitory the project status" during the monitoring phase of POMA 

### Measurable, Trackable, Validatable, and Verifiable Goals 
* G/Q/M - Systematic approach for setting project goals (tailored for specific needs) and defining them in an operational and traceable way 
* **G/Q/M (Goal/Question/Metric)** 
	* A software metric paradigm based on identifying the goals, formulating questions about the goals in quantifiable terms, and establishing the metrics to answer the formulated questions 
* **Measurable attribute** 
	* An attribute for which there is a well-defined metric and methodology for its measurement 
* **Tracking** 
	* Keeping a record of the measurements taken on an attribute 
* **Validation of goal** 
	* Comparing a stated goal for an attribute with the actual measurement taken for that attribute 

## Metrics and Measurements: An Overview 
* Metric vs. measurement example: 
	* Metric might be "hour" for the attribute "time;" and a clock is the tool used to perform the measurement 
* **Metric** 
	* The unit used to characterize an attribute 
* **Measurement** 
	* The act of characterizing an attribute, which may involve multiple steps, utilizing the agreed-upon metric for that attribute 
* **Capability Maturity Model for Software (CCM for SW)** 
	* A model, defined by the Software Engineering Institute, that defines give possible levels of maturity for a software organization. The five levers are Initial, Repeatable, Defined, Managed, and Optimizing 
* **Capability Maturity Model Integrated (CMMI)** 
	* A process assessment and improvement approach defined by the SEI. It is the follow up to the original CMM approach 

## Deliverable-Related Metrics and Measurements 
* List of often important deliverable attributes (p. 59.2) 

### Metrics and Measurements Example 1: The Quality Attribute 
* **Errors Versus Defects** 
	* Here we are using the terms "error" and "defect" differently than we have before, so the definitions of these terms need refinement: 
		* A software _error_ is a mistake made by the software supplier (or developer) 
		* A software _defect_ is the manifestation of an error during the execution of the software 
* Figure 3.1 - Inverse relationship of problems found versus quality 
* **Incremental Goals** 
	* As much as one may desire... (p. 61.4-62.2) 
* **Quantitative Subgoals** 
	* Once a defect severity categorization is established, then... (p. 62.3) 
* **Metric Definition** 
	* Given this set of subgoals (p. 62.4), the metric for the software quality attribute would be defined for each defect type: The number of unresolved "open" defects by defect severity level 
* **The Measurement Process** 
	* (p. 63.1) 
* **Reporting Format** 
	* (p. 63.2) 
* Table 3.1 - Weekly Quality Report (p. 63.5) 

### Complex Attributes 
* Metric definition requires a set of, or combination of, statements and definitions 
* **Complex attribute** 
	* An attribute whose metric definition requires a set of, or combination of, statements and definitions 
* **Simple attribute** 
	* An attribute whose metric may be stated with a single definition 
* List of successful project management items that should "at least" be in the plan (p. 65.7) 
* List of "goals for software code deliverable quality (p. 66.3) 

## Project- and Process-Related Metrics and Measurements 
* List of common, nondeliverable project-related attributes (p. 66.6) 

### Metrics and Measurements Example 2: The Schedule Integrity Attribute 
* List of example schedule goals (p. 67.5) 
* **Schedule Attribute Metric and Reporting Format** 
	* The metric for the schedule is the same as that for time. The actual process of... (p. 68.5) 
* Table 3.2 - Weekly Schedule Report (p. 68.7) 
* Table 3.3 - Task Breakdown for Schedule Attribute Example (p. 70.1) 
* **Task Overlap** 
	* To asses whether any of the requirement tasks overlap, the project manager... (p. 70.6) 
* **Buffer size** 
	* The amount of buffer to place on the initial estimate from the WBS is a project management call. Although there... (p. 71.3) 
* **Schedule Integrity Goal** 
	* The schedule integrity goal of the project can now be established, given... (p. 72.2) 
	* **Immediate-recoverable goal setting** 
		* Setting a goal and its associated metric and measurements in such a way that if the goal is missed, there is an immediate way to recover without expending a large amount of extra resources and potentially causing other goals to be missed 
* Figure 3.2 - Example Schedule (p. 73.4) 

### Interrelated Attributes 
* Many process and project related attributes are intertwined 
* Interrelated attributes List (p. 75.5) 

## Influencing Downstream Phases 

# Chapter 4 
Project Resource Planning 

## Objectives 
* How planning proceeds for the three main targets of software project resources planning - human resources, processes and methodologies, and tools and equipment 
* How the three separate plans are pulled together into a single combined resources plan 
* How resources may be outsourced and thus require the project manager to plan the human processes, tools, and equipment resources accordingly 

## Planning for the Three Types of Resources 
* The key resource for most projects is people 

## Human Resources 
* This isn't "company HR," it's people power. Skills, number of workers, etc. 
* Recruitment and hiring proceed in two stages, List (p. 80.4) 

### Skills Matrix 
* Table 4.1 - Skills Description of Personnel Required for Example Software Project (p. 81.1) 
* **Direct project activities** 
	* Activities that lead to a customer deliverable. Human Resources for these activities must be assigned or the customer deliverables cannot be delivered 
* **Indirect project activities** 
	* Activities that are related to the planning, controlling, and reporting of the direct project activities. People assigned to these activities do not directly work on the customer deliverables and thus can become marginalized 
* Reasons for personnel ramp up List (p. 82.4) 
* Table 4.2 - Initial Skill Matrix (p. 82.6) 
* Designer could quit after their task, or assume another role - matrix doesn't say 

### Hiring Plan 
* Table 4.3 - People Hiring Matrix (p. 85.1) 

### People Hiring Matrix and Recruiting Plan 
* **People hiring matrix** 
	* A project hiring plan shown in the form of a matrix or bar chart that indicates each specific human resource and the time period for which that person is associated with the project, including his or her recruiting and assimilation time 
* Table 4.4 - Direct Management Involvement in Recruiting 

### People as Human Capital (what) 
* More people require more people (admins, managers, etc.) 

## Processes and Methodologies 
* These are resources (woah) 
* **Software development process** 
	* An ordered set of defined activities that describe the defining of requirements, designing, coding, testing, and release for a software artifact. A process may contain some subprocesses, such as the design subprocess within the software development process 
* **Software methodology** 
	* A set of rules and principles defined to achieve a specific goal and to accomplish a specific task in the development or support of software 

### Software Project Phases 
* List of phases in all software project cycles (p. 90.6) 

### Requirements Process Planning 
* List of issues software planners/managers should consider (p. 91.3) 
* Example guidelines for acquiring/generating requirements process and methods (p. 92.3) 

### Design Process Planning 
* List of activities that may be in the design process (p. 92.6) 

### Implementation and Programming Process Planning 
* Code developing, documentation, and publication development activities 
* List of possible activities for this phase (p. 94.3) 

### Test Process Planning 
* List of possible activities (p. 95.4) 
* **Test scenario** 
	* A description of a set of interactions between the system and an external agent, which may be a user or another system, to accomplish a desired user task or goal. these scenarios are often directly derived from the requirements specification document 
* **Test case** 
	* A description of a specific interaction between the system and an external agent; the interaction has defined inputs and defined expected outputs or results. Test cases are usually developed from a test scenario 
* **Test script** 
	* A test case written in a language that may be used directly by some test tool to conduct the actual test 

### Product Release Process Planning 
* List of two activities that are part of software release phase (p. 96.3) 

### Other Process Planning Considerations 
* **Cross-Functional Process Planning** 
	* In addition to the activities related to the major phases of a software project, some activities cross boundaries or... (p. 96.5) 
* List of some major cross-functional activities (p. 97.2) 
* **Process as Intellectual Capital** 
	* Other cross-functional processes and methodologies may need to be defined as well. The important thing... (p. 98.2) 
* People must learn these methodologies 
* These methods should be viewed as "intellectual capital" (I disagree but ok) 
* **Intellectual capital** 
	* Knowledge that is considered an asset and ultimately has financial value 

## Tools and Equipment 
* List of details concerning hardware (p. 99.4) 
* List of details concerning software (p. 99.6) 
* List of tools classification categories (p. 100.2) 

## Combining the Resources 
* Table 4.5 - Combined Resource Matrix (p. 101.2) 

## Outsourcing versus Insourcing 
* **Outsourcing** 
	* Physically moving work to external sources 
* **Insourcing** 
	* Physically bringing in external human resources to perform work. These external resources may be from different organizations within the same company 

# Chapter 5 
Risk analysis and Planning 

## Objectives 
* What the concept of risk is -  namely, an anticipatable uncertainty that may be identified and analyzed 
* How risk items can be identified from previously planned areas, such as project deliverables, tasks, schedules, goals, and resources 
* What is involved in planning for risk: identification of risk items, prioritization of risk items, and analysis of the risk mitigation alternatives 

## Risk Definition 
* **Risk** 
	* A problem that has a greater than 0% but less than 100% probability of occurrence 
* **Problem** 
	* An event that has a negative value associated with it 

## Risk Identification 
* Figure 5.1 - Risk Management and POMA (p. 109.1) 
* List of major sources of risks and software development (p. 109.3) 

### Identifying and Listing the Anticipatable Risks 
* For software project planning - List of plan categories to identify risks for (p. 112.2) 

## Risk Prioritization 
* **Risk prioritization** 
	* The activity of ordering risks based on some criterion or set of criteria 

### Prioritization by Recovery Cost 
* **Recovery cost** 
	* The cost in terms of effort or financial expense to solve a problem should a risk materialize 
* Table 5.1 - Risk Prioritization by Recovery Cost (p. 113.6) 

### Types of Recovery Cost Prioritization 

### Prioritization by Risk Value 
* Includes probability of occurrence - not just "badness of outcome" 
* RV(j) = P(j) * RC(j)
	* RV = Risk Value 
	* P = Probability 
	* RC = Recovery Cost 
	* j = Possible problem 
* **Risk value** 
	* A recovery cost that is influenced and modified by another criterion or set of criteria. The probability of the risk turning into a problem is such an influencing factor, and when such a factor is taken into account in modifying the recovery cost, the result is the risk value 
* Table 5.2 - Risk Prioritization by Risk Value (p. 115.10) 

## Risk Mitigation 
* **Risk mitigation** 
	* An activity that may reduce, minimize, or totally avoid a risk 

### Cost-Based Mitigation 

### Cost of Mitigation 
* Table 5.3 - Estimated Mitigation Costs for Risk Item J (p. 117.6) 
* Lowest cost = choose it 

### Probability of Success 
* Choose which has best probability (obviously...) 

### Mitigation Value Cost 
* MVC(k) = P(k) * MC(k) 
	* MVC = Mitigation Value Cost 
	* P = Probability of failure 
	* MC = Cost 
	* k = mitigation alternative 
* **Mitigation value cost** 
	* The cost of risk mitigation after taking into account another criterion or a set of criteria, such as the probability of mitigation success 
* Table 5.4 - Mitigation Value Cost (p. 118.7) 

### Fixed Budget for Risk Mitigation 
* Table 5.5 - Sequential Application of Fixed Budget for Risk Mitigation (p. 119.6) 
* Table 5.6 - Allocating a Fixed Risk Mitigation Budget by Maximizing Risk Value (p. 120.6) 
* Max risk value approach (p. 120.1) 
* Risk plan should include List (p. 120.5) 

## Risk Removal and the Risk Plan 
* Table 5.7 - Risk Removal Plan (p. 121.1) 
* We addin' target dates BOYS!!! 

# Chapter 6 
Human Resources 

## Objectives 
* What software organizational structures are possible, including those for both software development and software support organizations 
* What preparations are needed to acquire human resources - recruiting, hiring, and bringing new people on board 

## Software Project Organization: An Overview 
* p. 129 

## Software Development Structures 
* p. 130 

### General Organizational Structure 
* Figure 6.1 - General software project organization (p. 131.1) 
* **General software development organization** 
	* An implementation-independent general organization that includes all the major activities required to develop software artifacts, from inception to release. The spe... (p. 131.3) 

### Refining the General Organizational Structure 1: Matrix Versus Hierarchical Orientation 
* **Hierarchical organization** 
	* An organizational structure in which all the people associated with a project are grouped into functional departments that report directly within the vertical line of command of the organization 
* **Matrix organization** 
	* An organizational structure in which people are grouped based on the functions they perform. These people may not report directly within the vertical line of command of the organization 
* **Virtual organization** 
	* An organizational structure in which many of the project personnel are located physically apart and are bought together as a temporary functional team 
* Figure 6.2 - Modified general software project organization (p. 133.5) 

### Refining the General Organizational Structure 2: Functional Orientation 
* Figure 6.3 - Refined software organization: Functional orientation (p. 134.4) 

### Refining the General Organizational Structure 3: A Highly Specialized Organization 
* Figure 6.4 - Refined software project organization: Software development specialization (p. 136.1) 

## Software Support Structures 
* After release, still need to support 
* **Software support and service** 
	* Post-software-release activities related to clarifying user questions and fixing software problems encountered by users 
* **Customer management** 
	* The set of activities related to ensuring that the customers' needs are properly served 
* Figure 6.5 - Software support organization (p. 137.6) 
	* Has different levels, explained on pp. 137.5-...? 

## Recruiting and Hiring Software Personnel 
* Once positions outline, software Project Manager must fill spots 

## Recruiting 
* Examples of some common software positions and related skills descriptions (p. 138.6-...?) 

### Hiring 
* Interview can be several stages 
* Interview prompt sheet question examples (p. 140.5) 

### Bringing People on Board 
* List of preparation items before new employee arrival (can be delegated to someone else) (p. 142.5) 

# Chapter 7 
Processes, Methodologies, and Tools 

## Objectives 
* Why a process may have been chosen for the project during planning, but must be revisited, properly positioned, and controlled for the project team during the organizing and preparing phase 
* How the details concerning methodologies, which are typically not included in a project plan, are defined, specified, and introduced to the team 
* Why the tools, which accompany the processes and methodologies, are an important productivity aid for the project team 

## Processes 
* List of factors software project process is further tailored for (p. 145.4) 
* Article on ISO, SPICE, and SEI (p. 146.3) 

### Process Map 
* Still need to map overall process, clearly list activities, explain relationships of steps 
* Figure 7.1 - Overall project process map (p. 148.4) 

### Process Flow 
* Arrows in Figure 7.1 show flow of activity - dotted lines = could go back (or even farther) 
* Need "exit criteria" companion doc for Figure 7.1 
* Exit criteria from design process example List (p. 150.4) 

### Configuration Management 
* Made up of a complex set of activities that relate to management of artifacts generated 
* List of what it includes (p. 151.4) 
* **Configuration management** 
	* A set of procedures that define, track, and control the artifacts produced during the development, support, and maintenance of software 

### Processes and Subprocesses 
* Transform from high-level process plan to project specific model must include List (p. 153.2) 

### Process Introduction and Education 
* Education and communication should come in stages 
* Example approach of staged approach (p. 153.5) 

## Methodologies 
* Process provides macro steps, methods provide micro steps 

### Methodology Definition 
* Methods described example for functional testing (p. 156.4) 
* **Predicate** 
	* A relation (e.g., _x_ = _y_) that has a value of either true of false. In programming constructs, an "if" statement is often used to evaluate the truth or falsity of a relation 
* **White-box testing** 
	* A testing methodology in which the actual ode is reviewed during the development of test cases (can count predicates) 
* **Black-box testing** 
	* A testing methodology in which the development of test cases is based on requirements or design documents but not on a review of the actual code 
* Two items needed for functional testing (p. 157.5) 

### Methodology Preparation 
* **Aspect-oriented programming (AOP) 
	* A new software development methodology that emphasizes cross-functional features or concerns that may arise in the requirements, design, or implementation steps. Examples of aspects include design constraints, system properties, and system behaviors 
* Judge software methods with this criteria List (p. 159.2) 
* First stages of preparation (fourth stage may be needed) 

## Tools 

### Tool Identification and Preparation 
* Activities to prepare for acquisition and use of tool List (p. 160.4) 
	* First step especially important 

### Tool Selection 
* Criteria for tool selection should take into account analysis of List (p. 161.5) 

### Tool Usage Preparation 
* Train the project team 
* Even after training there's a period of time the team may lose some productivity 

# Chapter 8 
Goals and Measurements: Preparations and Costs 

## Objectives 
* How the goals specified during the planning phase can be reexamined to ensure that proper metrics and measurement schemes are defined and implemented 
* How the software project team should be prepared so that it will accept the measurement scheme 

## Transforming Goals and Measurements 
* Organizing phase other important notions to be weighed List (p. 168.1) 

## Clarifying Definitions of Goals and Measurements 
* To alleviate confusing measurement scheme, do List (p. 168.4) 
* Goals should be "clear" 

### Decomposing the Ease-of-Use Example 
* Example steps for usability test List (p. 169.3) 

### Potentially Misleading Measurements 
* Example of arithmetic on categories List (p. 169.7) 
* Table 8.1 - Effect of Varying Assigned Values (p. 171.1) 
* Different value systems lead to different results. This can cause misleading results 

### Building a Measurement Operational Plan 
* Refinement steps List (p. 171.5) 
* **Operational plan** 
	* A plan that contains all the details of how to implement what is contained in a general project plan 
* Operational plan for usability testing example List (p. 172.4) 
* Items that need to be considered for goals and measurements during this phase List (p. 172.7) 

## Embracing the Measurement Scheme 
* One thing to put forward plan, another to get acceptance for plan 

### Participating in Goal and Measurement Preparations 
* It's good to have other people participate in analysis for these reasons List (p. 173.3) 
* Goal-Question-Metric approach defines a measurement model as follows List (p. 174.3) 

### Goal Attainability 
* If team members don't think goals are achievable, moral drops 
* To win general acceptance and positive reception of the goals and measurements, the software project management must ensure these are in place List (p. 175.4) 

## Measurement Costs 
* Reasons put forth to explain not setting goals and measurements List (p. 176.3) 
* Example breakdown of effort required to measure design review results List (p. 177.3) 

