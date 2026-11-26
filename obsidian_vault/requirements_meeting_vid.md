---
type: meeting
topic: school
---

#swe3623 

# video
purpose of meeting:
* go over expectations for project
create member app for members of the studio
* come up with features I listed in project description
* this is an elicitation meeting 

## Project Description
* Concept is loosely based on a real-world situation 
* If you are influenced by any other models you need to let me know
* Situation:
	* Work out studio did everything manually 
	* Recently converted practice to managing things digitally 
	* When you become a member of the studio you need access to the mobile app
	* Create a mobile app that's a one-stop shop that can do the things listed
* Create fun group name and logo
* There are two separate workout locations that have two workout rooms that have a couple of different classes they teach. When you sign up you leave a credit card on file, can pay for incidentals from the app. Different tiers, 4, 8, unlimited visits per month
	* Class sizes are limited. Put a cap on things (so like 30 people can't sign up)
	* A user profile will become very important, so you can track your fitness activities like weight, age, height, gender. Health conditions, goals. All these play into workout goals, progress, nutrition fees, etc.
* There are also incidental fees 
	* A big part of this application should be a digital nutrition assistant and digital personal trainer
	* This is an additional charge, something you can sign up for if you have the app
	* Give personal attention to the user
	* This will set it apart from other workout apps in the world

## q&a
* in the description of the project is says "following the parts of the project, they are intentionally vague. . . Your team should only choose one. Are we choosing only one feature or all of them?" 
	* Team should do all features. All features should be inside every team's apps 
* "this is to be focusing exclusively on the members. Not to worry about admin privileges or employees coming in to change information" 
	* It is primarily for the members. The staff and people who run the gym will not be using this to manage members. But you do want to make sure an admin can come in and make announcements 
	* We are the devs, so how the announcement is shown is up to us 
* Is the app in ios, google play, etc. What are the technical specs 
	* I want it to be made for a mobile device. If when you go into marvel (?) you create your project based on iPhone or Android. It doesn't really matter which one you use 
	* Basically deliver prototype that looks like it's on a phone
* Does the gym have a theme? (yoga, stretching, get buff, etc.) 
	* The studio just offers classes at those two locations. The classes they offer are yoga, soomba, spin, pilates, and hit programs with free weights 
* What does the user profile look like? What is the demographic of this studio? 
	* Weight, age, height, gender
	* Health conditions, goals
	* "it's just that i want to loose weight" but some people go into fitness to run a 5k or to do a bike ride, etc. 
	* specific to each user, when you sign up you sign up at the gym 
	* I would think a phone number and email address would be important as well 
* Goals: do you want them to be selecting from a list or typing them in? 
	* I would suggest that you outline some common goals (weight loss/gain) 
	* At some point you should take into consideration body composition (probably out of scope of this) 
	* Share a list of fitness goals (run a race) 
	* It would be fair to list some canned answers, but also have the option to share some other goals they have 
* For class enrollment, what information do users need to provide in order to enroll in a class and are there any classes that have extra steps to enroll? 
	* Trying to keep this focused on what a member would need 
	* Would want the members to see some sort of schedule 
	* You don't need to figure out how the employee would create the schedule
	* Each class will hold only 20 participants, have mechanism that doesn't allow enrollment if there's already 20 people in it 
	* They should be able to sign up to a class if it's on the schedule
	* Hours are 9-9, class lasts an hour with 30 minutes in between for cleaning/setup 
	* As a member you should just be able to go, see what's there, sign up 
	* Is the app expected to have some sort of social media presence. Like smart watch lets you share your runs 
		* That's up to you
		* Part of the digital personal trainer should track the workouts you've done at the studio (took 2 spin classes, 4 hit, etc.) 
		* I do want to make sure, as a member, you can record exercise workouts that you do outside of the studio 
		* Doesn't have to work with 3rd party apps, no requirements for that but can make assumptions there if we want to 
		* But do incorporate "oh i went for a 5 mile run," stuff outside of studio as well as inside 
	* Is this gunna be like an AI personal trainer, or is someone logging in from the gym with a chat box, how fleshed out do we need to be with that? 
		* To address the first part: I included so many features because most teams start out with 5 people which is a lot 
		* I try to have enough features so that everyone has something meaty to sink their teeth into 
		* Digital assistant: What I envision is that it would put added value to an app that you could get anywhere
		* There would be add on fee to use it
		* The main thing as what the user sees. This is all user-facing design 
		* It's more of a simulation than actually coming up with a workout plan 
		* Could use chatgpt to put in some information 
* Is there a particular color scheme? 
	* No basically
* How involved is billing? 
	* When you sign up at studio you give them credit card on file that auto pays monthly. The only thing you would want to pay for through the app are incidentals 
	* Don't worry about membership sign up in app 
* Can we have a feedback form on the app 
	* If you have time but that's not a requirement 
* What's the payment system like? 
	* Just credit card is fine
	* If I were actually coming to you with a real app in mind I would say "tell me what payments I need to take" 
* Workout screen, how involved? Graphs, pie charts, etc. 
	* Simple, bear bones 
	* This month you completed four hit classes, 3 yoga classes, etc. 
	* All classes are same length. Would be cool to see how many of each class I took past month 
	* Or like, if my goal is to gain/lose weight the user should input weight at certain amounts of time 
* Login info given to user. Is it a picked username/pass or does the gym give it to the user? 
	* Just username password 
	* You can make it just a clickthrough screen
	* Honestly don't need to see a login screen itself 

# Quick loot at VSD 
* Make sure students work together. Sometimes seems like diagrams, lists, etc don't match up 
* Do want to see sketches in our document 
* Probably will only be 8-10 screens for the app 
* 

# Notes .docx she showed 
## Design 
* Please develop a name for the studio. Don't use your groups name
* Create and original logo

## Studio Details 
* There are two studio locations with 2 workout rooms per studio 
* Each class will hold only 20 participants at a time. Some mechanism must be in place to make sure that classes don't exceed the limit 
* Hours are 9am-9pm. Classes last one hour, with 1/2 hour cleanup and setup time in between 
* Class offerings are: Yoga, Zumba, Spin, Pilates and HITT with free weights 
* Members sign up on location and leave a credit card on file 

## Three Tiers of Membership 
* 4 visits per month. $60. Can add on classes at $12 per class 
* 8 visits per month. $120. Can add on classes at $10 per class 
* Unlimited visits. $150 per month
* Members should be identified by their membership type and not allowed to exceed monthly visits 

## User Profile
* To use the app, the user must set up a user profile with information critical to health and fitness goals 
	* Weight 
	* Age
	* Height
	* Gender
	* Goals (weight and fitness) 
	* Health conditions 

## Incidentals and fees 
* If you book a class and late cancel (less than 12 hours) or don't show, the charge is $12. This is automatic, but should include notification by the app 
* The studio runs monthly promotions that are optional. The charge varies. Please develop at least one for demonstration purposes 
* A member can pay for additional classes 

## digital personal trainer
* $20 add-on for unlimited plan 
* Member can join at any time 
* Will design a workout schedule tailored to the user based on the information above 
* Allows the user to set progress at the studio, but also allows the user to track workouts outside 
* Online coaching and chat are available 9am-9pm 

## digital nutrition assistant 
* $20 add-on for unlimited plan 
* Member can join at any time 
* Will design a nutrition plan tailored to the user based on the info above 
* Allows tracking food and calculating recommended macros for goals 
* Online coaching and chat are available limited hours 9am-9pm 