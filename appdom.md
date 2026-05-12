# Sprint 2 

## Administrator User:

* ~~Add, View, Edit, or Deactivate accounts.  You can ask the administrator to select which service he wants before displaying the appropriate user interface where he can perform the functionality.  When an account is added, you must store in the database at least the following required information using a user interface designed to allow entering or modifying the information:~~
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
* Duplicate account numbers or names should not be allowed;
* ~~All monetary values should have two decimal spaces;~~
- All monetary values must be formatted using commas when appropriate;
- ~~Account numbers should not allow decimal spaces or alphanumeric values;~~
- ~~Accounts with balance greater than zero cannot be deactivated;~~
- ~~View either individual accounts and their details or a report of all accounts found in the chart of accounts;~~
- ~~Search using either account number of account name to locate an account in the chart of accounts;~~
- The name of the logged user must be shown on the top left corner of the page;
	- is top-right fine?
- ~~The logo of the software must display on each page;~~
 - Clicking each account in the chart of account should take you to the ledger of each account;
 - You should be able to filter the data in the chart of accounts page using various tokens such as by account name, number, category, subcategory, amount, etc.
 - ==A pop-up calendar should display at the top left corner of the page;==
- ~~Buttons to other services provided in the software such as journalizing must be found at the top of each page;~~
 - ~~An event log showing the before and after image of each record added, modified, or deactivated should be generated each time data changes by any of the users.  The event logs must be kept on a table.  The user id and the time and date of the user who made change to the data must be saved.  Each event must have a unique auto generated ID.~~  
	 - needs styling
 - ~~Each of the pages in the application must have a consistent color and layout scheme;~~
 - Each button must have a built-in tool-tip providing information about the purpose of the control;
- Each page must have a help button having information about the entire software organized by topic
 
## Manager user 

 * Can view accounts but can’t add, edit, or deactivate accounts, but can perform the rest of the services the administrator can perform;

## Accountant User

 * Can view accounts but can’t add, edit, or deactivate accounts, but can perform the rest of the services the administrator can perform
 