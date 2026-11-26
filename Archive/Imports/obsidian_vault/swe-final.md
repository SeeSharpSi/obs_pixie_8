---
type: study
topic: school
---

# Chapter 1 & 2
* Functional vs Nonfunctional Requirements
	* Differences
	* Functional Requirements:
		* Input Formats: What is the format for input data
		* Sorting: How do you sort things
		* Special cases, boundaries, and error conditions: Are there any special cases? How should we handle them?
	* Non-functional Requirements:
		* Real-time Requirements: when a program needs to perform in real-time
		* Performance requirements: how fast the program runs. How fast it inputs and outputs
		* Modifiability Requirements: know the expectation for future modifications and make those easily possible.
* Different kinds of testing
	* Predetermined inputs are "test cases" and require some thinking
		* If results do not match expectations:
			* Debug
			* Fix
			* Retest/Reverify
		* Stop when all test cases produce expected results
	* Acceptance testing
		* Testing done by clients
	* Verification & Validation Testing
		* Validation Tests determine if devs are building the right thing for clients
		* Verification Tests determine if the system build is correct
	* Unit testing
		* Test for specific piece of software
		* Checks each module, function, and/or method written
	* Black Box testing
		* Test/tester has no prior knowledge of internal workings
		* Test/tester provides input and observes output
		* Useful for seeing how the system responds to expected and unexpected user actions, its response time, usability issues, and reliability issues
	* White Box testing
		* Uses knowledge of internal structure to test logic
		* Tests smaller parts of the application
		* Test cases can be designed while looking at the design and code implementation
* Tasks involved in creating a software project
	* Estimate total minutes
	* Estimate calendar time
	* Estimate subtasks
		* Divide into development tasks, divide these into subtasks
* ==How to solve a complex problem w/ three methods:==
	* Decomposition
	* Incremental
	* Modularization?
	* Integration and Modularization
	* Look at their definition and differences
* What is software integration?
	* All unit tests put together and execute it
	* The process of linking together individually tested units into a coordinated whole system
* Where does effort estimation come in?
	* Is it technical or nontechnical?
	* It's nontechnical
	* Know the differences
	* Estimating the total effort and coming up with reliable project schedule under this difficult condition is one of the main reasons behind so many software project failures
* Communication paths
	* How they change based on # of people
	* Learn that algorithm
	* (n(n-1))/2
		* n = # of people

# Chapter 13
* What is project management?
	* What are its goals?
		* Scope: The project deliverables must meet the requirements and specifications laid out in the project scope
		* Schedule: The project deliverable must be delivered on time within budget
		* Quality: The project deliverable must meet or exceed the quality standards set for the project
		* Not meeting these criteria is considered a failure
	* What is it planning to achieve?
		* When done right, every part of the business runs smoothly
	* What is the end goal of a project?
		* Satisfy customer needs
		* All required attributes (quality, security, productivity, cost, etc.) are met
		* Target milestones are met along the way
		* Team members operate effectively with high moral
		* Required tools and other resources are available and effectively used
		* Submit on time
		* Work as intended
* Four phases, POMA
	* Planning
	* Organizing
	* Monitoring of status
	* Adjustment
* What are risk management's components?
	* Identify the risk
	* Prioritize the risk
	* Mitigate/Analyze the risk
* What is Project Effort Estimation used for?
	* It's used to estimate how much effort is needed to complete a project. This helps allocate resources, time, skills, etc.
* Work breakdown structure:
	* What is it?
		* A depiction of the project in terms of discrete sub activities that must be conducted to complete the project
	* Why do you need it?
		* It's needed in order to prioritize a sub activities "weight" (how hard it is) and "need" (how soon/much it needs completed)
* Gold? Question matrix and what is it?
# Chapter 3
* Why do you need software engineering?
	* Realizing the degree of complexities between a one-person programming effort and a large software system effort
	* the number of failures in software projects and defects encountered in the software products
* Reasons for project success vs failure:
	* Budget
	* Time
	* Schedule
	* Does it "do as intended?"
	* User involvement
	* Executive management support
	* Clear requirements
	* Proper planning

# Chapter 4
* Waterfall, Incremental, Spiral
	* What do they do?
		* Waterfall: Oldest. Tasks occur sequentially one after the other. Four main tasks must be completed:
			* Requirements
			* Design
			* Implementation
			* Testing
		* Incremental: Divides the system's functionality into small increments that are delivered one after the other in quick succession
		* Spiral: Risk-driven software development model. Combination of waterfall and incremental; each phase begins with a design goal and ends with the client reviewing the progress. Reduces risk. Cyclic approach.
	* What are their differences?
		* Waterfall is bad at revision
	* What are the advantages and disadvantages of each?
* Rational Unified Process:
	* Traditional or nontraditional?
	* It's traditional, but why
	* Four phases, each consisting of:
		* Business modeling
		* Requirements
		* Analysis and design
		* Implementation
		* Testing
		* Deployment
* Capability Maturity Model
	* CMM
	* A method to evaluate and measure the maturity of the software development process of an organization
	* Scale of 1-5
	* Higher = better
	* Levels:
		* 1: Initial
		* 2: Repeatable
		* 3: Defined
		* 4: Managed
		* 5: Optimizing
* CMMI:
	* What is it?
		* Capability Maturity Model Integrated
		* Upgrade of CMM
		* Two representations, Continuous and Staged
	* Maturity Levels:
		* Initial
		* Managed
		* Defined
		* Quantitatively Managed
		* Optimizing
	* What is it used for?

# Chapter 5 A
* Agile methodology
	* What is it?
		* Term used to describe software development approaches that employ continual planning, learning, improvement, team collaboration, evolutionary development, and early delivery
		* Involves working in iterations
		* Works off the basis that changes can be made quickly
		* Is the most popular approach to project management
		* Involves constant collaboration with stakeholders and continuous improvement at every stage
		* Incorporates continuous testing and responsiveness to change
	* Pros:
		* Involves stakeholders, meaning end product meets their needs more specifically
		* Is iterative, meaning it can adapt to change faster
		* Constant involvement of teams and stakeholders and constant assessment of progress means less risk is involved
	* Cons:
		* Doesn't work
		* Requires more coordination
		* People can become complacent, as less tech-savvy people are often placed in charge
* What is EP?
	* Extreme Programming
	* Mainly focused on customer satisfaction
	* Highly organized
	* Takes the best practices of the development process to an extreme level
	* Concentrates on getting more feedback
	* Small iterations (1-2 weeks)
	* Eliminates defects in early stages
	* Phases:
		* Planning
		* Designing
		* Coding
		* Testing
		* Listening
	* What is unique about each of these that keeps them separate from the others?

# Chapter 6
* Why is requirement engineering important?
	* What a software system should be, but not how it's constructed
	* The process of defining, documentation, and maintenance of requirements in the design process of engineering is called requirements engineering
	* 
* What is scope creep and what causes it?
* What is Requirement Engineering?
	* What are the things associated with it?
* VORD:
	* Viewpoint Oriented Definition
	* What is it?
	* What is it used for?
	* It falls under Requirement Analysis
	* It's the different views of the stake holders
	* You take them and group them together
 * Requirements Analysis
	 * What tasks are inside it?
	 * Why do you need to prioritize a requirement?
* What are the different ways to cluster/group requirements?
* Software Architecture:
	* What is the difference between each kind?
* What is Software Architecture?
* What is the difference between each view of software architecture?
* Views:
	* Logical
	* Physical
	* Development View
	* The others...
	* What are they? What are their differences?
* What is architecture?

# Chapter 7
* Relational Database design
* Object-Oriented Database design
* Understand what every phase is
* No questions about any diagram

# Chapter 8
* What is cohesion coupling?
* What is The Law of Demeter?

# Chapter 9
* What is the importance of:
	* Programming guidelines
	* Styling Guidelines
	* Indenting
	* Spaces
	* Naming Code/Files Appropriately
* Debugging concepts:
	* What is the process you follow
	* Stabilization
	* Localization
	* Detection
* How to use VM ware
	* Turning a physical server into multiple virtual servers
* Developing in the cloud:
	* Servers that are accessed over the internet and the software databases that run on them
	* What is it used for?
		* Avoiding maintaining physical servers
	* What are the different types of services?
		* Infrastructure as Service (IaaS)
			* Rent IT infrastructure and VMs
		* Platform as a Service (PaaS)
			* On-demand enviroment for developing, testing, delivering, and managing software applications (AWS Lambda's GUI)
	* Cloud, Pros:
		* Flexible
		* Scaleable
		* Less system admin labor
	* Cloud, Cons:
		* Less control
		* Legal issues (countries w/ different laws)
	* Cost?
		* Depends. For smaller projects the cloud can cost less, but for larger projects it will cost more. It's hard to make general statements about cost

# Chapter 10
* What is Quality Assurance?
	* Activities designed to measure and improve quality in a product and process
* What is Quality Control?
	* activities designed to validate and verify the quality of the product through detecting faults and "fixing" the defects
* What is the difference between inspection and testing?
	* What are the types of testing?
		* Acceptance validation
		* Verification
		* Dynamic Testing
		* Static Testing
		* White box (uses code)
		* Black box (doesn't uses code)
		* Stress
		* Performance
* How do you create test cases?
	* What are they?
	* How to create?
		* Grab from previous projects
		* Faults
			* Error guessing; test cases based on plausible faults
			* Error-prone analysis; finds areas of requirements and design that are error prone and makes cases for them
		* Boundary value analysis and equal sonneting (==short answers==)
			* min
			* min - 1
			* max
			* max + 1
		* Path analysis
			* Analyze number of paths in program
			* Decide which ones to test
* Test driven development:
	* What is it? (bad)
	* You write test cases before you write code
	* You write code for the purpose of passing test cases
* When should you stop testing?
	* When you have no errors
	* When you run through all your test cases
	* Stats based off test cases
	* Defect Seeding
* Inspection:
	* Phases
	* Different parts
	* "Phases in inspection and what are the different parts, Planning meeting preparation walkthrough, write in a sentence or two. Know difference between inspection and planning and other ones she mentioned too quickly."
	* Is peer review of software to identify bugs or defects
	* A team of 3-6 people typically studies a work product independently and then meet to analyze the work in more detail)
	* Planning is when the team gathers all of the information they have to determine the scope and process for a project
	* Inspection phases:
		* Planning
			* Moderator plans activities performed by small team
		* Overview
			* Presentation given to the inspector with some background information
		* Preparation
			* Each reviewer studies the project individually. Notes issues
		* Examination / Meeting
			* Moderator conducts meeting to collect and review defects
		* Rework
			* Author changes the work product
		* Follow-up
			* Moderator verifies changes are made to product; compiles defect summary report

# Chapter 11
* Software Artifact
	* Shows everything involved in the development of a program
	* Mock-ups
	* Design docs
	* Test matrics
	* Prototypes
	* Notes
	* Data Models
	* Diagrams
	* etc.
* What is Software Configuration Management?
	* Process of managing all pieces of artifacts
	* Deals with version selection
	* Tracking changes
	* Tracking version control
	* What is Software Configuration Network?
	* What activities are involved in Software Configuration Management?
		* Understanding the policy, process activities, and the resulting artifacts that need to be managed
		* Determining and defining the framework that needs to be used to manage these artifacts
		* Determining and bringing any tools that need to be brought in to facilitate the management of these artifacts
		* Training and ensuring that the agreed-on configuration management process is practiced and adhered to
		* "you have different kinds of artifacts starting from planning to maintain anything related to your p
		  roject are your artifacts. Anything related is called artifacts and managing those artifacts is software configuration."
* Software Configuration activities:
	* Manage artifacts
	* Decide framework
	* Decide methodology
	* What kind of tools are you going to use?
	* What kind of training will you use?
* Configuration Management:
	* How do you take care of artifacts?
	* What framework will you use?
* Storage:
	* How do you store artifacts?
	* What access methods will be used to retrieve artifacts?
* What tool do you use to implement configurations?
	* What's best for your project?

# Chapter 12
* What kind of customer support can be provided?
	* Defect support
	* Non-defect support
* Defects vs non-defects
	* Defects are for technical issues
	* Non-defects are for people unfamiliar with the tech
* What is Problem Arrival Code?
* What is Sun Setting? How do you do it?
	* Everything has a retirement
	* You slowly retire a project
	* No more upgrades
	* Start a new project
	* How does this procedure work?
* What is Problem Fixing?
	* What kinds of fixes are there?
		* Periodic Fixes (low priority, non crucial)
		* Priority Fix (immediate, crucial)
		* Fixes in large clusters? Crucial fixes?

# Student Asked Questions
* What are the four phases of inspection?
