---
type: assignment
topic: school
---

#swe3623 

# 2 Quality Attributes 
Format your work as a bulleted list with brief explanations

For 5.1 and 5.2, identify each internal and external quality attribute critical to your product. Possibilities include availability, efficiency, installability, integrity, interoperability, modifiability, portability, reliability, reusability, robustness, scalability, and verifiability. You work SHOULD NOT CONTAIN ALL ATTRIBUTES!  Write these to be specific, quantitative, and verifiable. Clarify the relative priorities for various attributes, such as security over performance.  TAKE CARE THAT QUALITIES IDENTIFIED ARE COMPLEMENTARY (P. 289)

## 2.1 External Qualities 
Specify and justify any required external qualities in a bulleted list.
* Availability 
	* Availability is important because gym members may log workouts periodically throughout the day 
* Integrity
	* Integrity is especially important because members may adjust their habits based on the app's feedback. Incorrect data will cause them to adopt incorrect habits 
* Performance
	* Performance is important for mobile applications because phones are slower than PCs and because users interact with mobile apps using their fingers and swiping, meaning a less responsive mobile app can be a lot harder to use than if you were using a keyboard 
* Security 
	* Security is important because health data is very sensitive and this app can incur payments, meaning unauthorized access can cause people to lose money and health data 
* Usability 
	* Usability is important because the technical ability of this app's users will have a broad range (both IT bros and grandmas go to the gym). It needs to be built for the lowest common denominator within reason, meaning it needs to be easy to use, navigate, learn, etc. 

## 2.2 Internal Qualities 
Specify and justify any required internal qualities in a bulleted list.
* Efficiency 
	* Efficiency is important because of the digital assistants built into the app in the form of a Digital Personal Trainer and Digital Nutrition Assistant. The backend for both of these needs to be fast in order for members to get quick responses 
	* Efficiency is also important to quickly calculate health statistics so that members can receive immediate feedback on their progress towards their health goals 
* Scalability 
	* Scalability is important because the amount of members a gym has can vary from year to year, meaning large amounts of quick growth need to be accounted for 
* Verifiability 
	* Verifiability is important because this app has cutting edge features like the Digital Personal Trainer and the Digital Nutrition Assistant. These features, being new, will likely encounter more bugs and more changes to their APIs 

## 2.3 Generate a prioritization that shows ALL internal and external qualities 
Format your work like the chart on 265 of the textbook.  You are required to have at least 5, but you should include all that are relevant to your part of the system.  DO NOT INCLUDE ALL QUALITY ATTRIBUTES!

| Attribute     | Score | Availability | Integrity | Performance | Security | Usability | Efficiency | Scalability | Verifiability |
| ------------- | ----- | ------------ | --------- | ----------- | -------- | --------- | ---------- | ----------- | ------------- |
| Availability  |       |              | ^         | <           | ^        | <         | <          | <           | <             |
| Integrity     |       |              |           | <           | ^        | <         | <          | <           | <             |
| Performance   |       |              |           |             | ^        | ^         | <          | <           | <             |
| Security      |       |              |           |             |          | <         | <          | <           | <             |
| Usability     |       |              |           |             |          |           | <          | <           | <             |
| Efficiency    |       |              |           |             |          |           |            | <           | <             |
| Scalability   | 2     |              |           |             |          |           |            |             | <             |
| Verifiability | 1     |              |           |             |          |           |            |             |               |

## 2.4 Other non-functional requirements as relevant 
Specify any additional non-functional requirements.  See the chapter 1 slideshow for help with non-functional requirements.  You should have at least 2-3 here.  Make sure these are not quality attributes identified above!
* 

# Chapter 14 - Quality Attributes 
* "This chapter will help you detect and specify nonfunctional requirements you might not have found otherwise" 
* "Quality attributes can distinguish a product that merely does what it’s supposed to from one that delights its users" 
* Quality attributes serve as the origin of many functional requirements 

## Software Quality Attributes 
* Several dozen product characteristics can be called quality attributes, although most project teams need to carefully consider only a handful of them 
* One way to classify quality attributes distinguishes those characteristics that are discernible through execution of the software (external quality) from those that are not (internal quality) 
	* External qualities: characteristics discernible through execution of the software 
	* Internal qualities: characteristics not discernible through the execution of software 
* External qualities are primarily important to users, while internal qualities are more important to developers and for maintenance staff 
* Internal quality attributes indirectly contribute to customer satisfaction by making the product easier to enhance, correct, test, and migrate to new platforms 
* Table 14-1 briefly describes several internal and external aspects of quality that every project should consider ![[Pasted image 20240717152542.png]]
* Certain attributes are of particular importance on certain types of projects: 
	* Embedded systems: performance, efficiency, reliability, robustness, safety, security, usability 
	* Internet and corporate applications: availability, integrity, interoperability, performance, scalability, security, usability 
	* Desktop and mobile systems: performance, security, usability 

## Exploring Quality Attributes 
* Because perfection is not possible, we have to decide which attributes from Table 14-1 are most important to the project's success 
* Jim Brosseau suggests the follow practical approach to identify and specify the most important attributes for a project: 
	1. Start with a broad taxonomy 
		* Begin with a rich set of quality attributes to consider 
	2. Reduce the list 
		* Engage a cross-section of stakeholders to determine which attributes are likely to be important for the success of the project 
	3. Prioritize the attributes 
		* Prioritizing the pertinent attributes sets the focus for future elicitation discussions 
	4. Elicit specific expectations for each attribute 
	5. Specify well-structured requirements 
* Sample quality attribute prioritization for airport check-in kiosk ![[Pasted image 20240719111554.png]]
* This spreadsheet calculates a relative score for each attribute 
	* In this illustration, security is most important 
	* A less (<) sign indicates that the attribute in the row is more important 
	* A carrot (^) indicates that the attribute at the top of the column is more important 

## Defining quality requirements 
* This section describes each of the quality attributes in Table 14-1 

### External quality attributes 
* External quality attributes describe characteristics that are observed when the software is executing 
* They profoundly influence the user experience 

1. Availability 
	* Availability is a measure of the planned up time during which the system's services are available for use and fully operational 
	* Formally, availability equals the ratio of up time to the sum of up time and down time 
	* Still more formally, availability equals the man time between failures (MTBF) for the system divided by the sum of the MTBF and the mean time to repair (MTTR) the system after a failure is encountered 
2. Installability 
	* Software is not useful until it is installed on the appropriate device or platform 
	* Some examples of software installation are: downloading apps to a phone/tablet; moving software from a PC onto a web server; updating an operating system, etc. 
	* Installing addresses the follow activities: 
		1. Initial installation 
		2. Recovery from an incomplete, incorrect, or user-aborted installation 
		3. Reinstallation of the same version 
		4. Reverting to a previous version 
		5. Installation of additional components or updates 
		6. Uninstallation 
3. Integrity 
	* Integrity deals with preventing information loss and preserving the correctness of data entered into the system 
	* Integrity requirements have no tolerance for error 
4. Interoperability 
	* Interoperability indicates how readily the system can exchange data and services with other software systems and how easily it can integrate with external hardware devices 
	* To assess interoperability, you need to know which other applications the users will employ in conjunction with your product and what data they expect to exchange 
5. Performance 
	* Performance represents the responsiveness of the system to various user inquiries and actions, but it encompasses much more than that, as shown in Table 14-2 
6. Reliability 
	* The probability of the software executing without failure for a specific period of time is known as reliability 
	* Reliability problems can occur because of improper inputs, errors in the software code itself, components that are not available when needed, and hardware failures 
7. Robustness 
	* Robustness is the degree to which a system continues to function properly when confronted with invalid inputs, defects in connected software or hardware components, external attack, or unexpected operating conditions 
8. Safety 
	* Safety requirements deal with the need to prevent a system from doing any injury to people or damage to property 
	*  Safety requirements might be dictated by government regulations or other business rules, and legal or certification issues could be associated with satisfying such requirements 
9. Security 
	* Security deals with blocking unauthorized access to system functions or data, ensuring that the software is protected from malware attacks, and so on 
10. Usability 
	* Usability addresses the myriad factors that constitute what people describe colloquially as user-friendliness, ease of use, and human engineering 

### Internal quality attributes 
1. Efficiency 
	* Efficiency is closely related to the external quality attribute of performance 
	* Efficiency is a measure of how well the system utilizes processor capacity, disk space, memory, or communication bandwidth 
2. Modifiability 
	* Modifiability addresses how easily the software designs and code can be understood, changed, and extended 
3. Portability 
	* The effort needed to migrate software from one operating environment to another is a measure of portability 
4. Reusability 
	* Reusability indicates the relative effort required to convert a software component for use in other applications 
	* Reusable software must be modular, well documented, independent of a specific application and operating environment, and somewhat generic in capability 
5. Scalability 
	* Scalability requirements address the ability of the application to grow to accommodate more users, data, servers, geographic locations, transactions, network traffic, searches, and other services without compromising performance or correctness 
6. Verifiability 
	* More narrowly referred to as testability, verifiability refers to how well software components or the integrated product can be evaluated to demonstrate whether the system functions as expected 