---
type: project
topic: school
status: idea
---

# Sprint 1
1. ~~Allow three types of users – administrator, manager, and regular user (accountant) to login to the system~~
2. ~~The administrator user should be able to create users and assign roles~~
3. ~~The administrator user should be able to update information about a system user~~
4. ~~The administrator user should be able to activate or deactivate each kind of user~~
5. ~~Each kind of user should be able to log in to the system once credentials are created in the system~~
6. ~~The login username, picture, should be displayed clearly on the top right corner of the login page once they have successfully logged into the system~~
7. ~~The login page should have:~~ 
	1. A text box to enter the username 
	2. A textbox to enter a password which will be hidden as the user keys in the password 
	3. A submit button 
	4. A forgot password button 
	5. A create new user button 
	6. A logo which will be displayed on all the pages of the application 
8. ~~The create a new user button will be used if the user is accessing the system for the first time.  Clicking this button should display a user interface where the user will provide personal information such as first name, last name, address, DOB, and click submit to request access to the application.  The administrator should receive email request and must approve or reject the request.  If approved, an email should be sent to the user with a link to login to the system~~
9. ~~A button for forgot password.  If this button is clicked, the system should prompt the user to enter email address and user id the person provided when his credentials were created in the system and ask security questions to allow him to supply new password~~
10. ~~Passwords must be a minimum of 8 characters, must start with a letter, must have a letter, a number and a special character, if this requirement is not satisfied, display at appropriate error message~~
11. ~~Password used in the past cannot be used when password is reset~~
12. ~~Password must be encrypted~~
13. ~~A maximum of three wrong password attempts should be allowed after which the user should be suspended~~ 
14. ~~All login information must be stored in database tables~~ 
15. ~~Three days before a password expires, the user should receive notification that the password is about to expire~~
16. ~~The administrator should have a report where he can view all users in the system without going straight to the tables~~ 
17. The administrator should be about to suspend any user from a start date to expiry date such as if the person is on an extended leave 
18. ~~The administrator should get a report of all expired passwords~~ 
19. ~~The administrator should be able to send email for any user from within the system~~
20. ~~A username should be made of the first name initial, the full last name, and a four digit (two-digit month and two-digit year) of when the account is created~~

# Sprint 2 

## Administrator User:

21. ~~Add, View, Edit, or Deactivate accounts.  You can ask the administrator to select which service he wants before displaying the appropriate user interface where he can perform the functionality.  When an account is added, you must store in the database at least the following required information using a user interface designed to allow entering or modifying the information:~~
    1. Account name
    2. Account number (must have correct starting values as discussed in class)
    3. Account description
    4. Normal side
    5. Account category (e.g. asset)
    6. Account subcategory (e.g. current assets)
    7. Initial balance
    8. Debit
    9. Credit
    10. Balance
    11. Date/time account added
    12. User id
    13. Order (e.g cash can be 01)
    14. Statement (e.g. IS (income statement), BS (balance sheet), RE (Retained Earnings statement)
    15. Comment
22. Duplicate account numbers or names should not be allowed;
23. ~~All monetary values should have two decimal spaces;~~
24. All monetary values must be formatted using commas when appropriate;
25. ~~Account numbers should not allow decimal spaces or alphanumeric values;~~
26. ~~Accounts with balance greater than zero cannot be deactivated;~~
27. ~~View either individual accounts and their details or a report of all accounts found in the chart of accounts;~~
28. ~~Search using either account number of account name to locate an account in the chart of accounts;~~
29. The name of the logged user must be shown on the top left corner of the page;
    - is top-right fine?
30. ~~The logo of the software must display on each page;~~
31. Clicking each account in the chart of account should take you to the ledger of each account;
32. You should be able to filter the data in the chart of accounts page using various tokens such as by account name, number, category, subcategory, amount, etc.
33. ==A pop-up calendar should display at the top left corner of the page;==
34. ~~Buttons to other services provided in the software such as journalizing must be found at the top of each page;~~
35. ~~An event log showing the before and after image of each record added, modified, or deactivated should be generated each time data changes by any of the users.  The event logs must be kept on a table.  The user id and the time and date of the user who made change to the data must be saved.  Each event must have a unique auto generated ID.~~  
	- needs styling
36. ~~Each of the pages in the application must have a consistent color and layout scheme;~~
37. Each button must have a built-in tool-tip providing information about the purpose of the control;
38. Each page must have a help button having information about the entire software organized by topic
 
## Manager user 

 * Can view accounts but can’t add, edit, or deactivate accounts, but can perform the rest of the services the administrator can perform;

## Accountant User

 * Can view accounts but can’t add, edit, or deactivate accounts, but can perform the rest of the services the administrator can perform