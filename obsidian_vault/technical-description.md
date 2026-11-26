---
type: project
topic: school
status: active
---

#SWE3313
# The Stack
To make a thorough system we've chosen a specific technology stack to suite specific needs.
* Java backend
* HTML/HTMX front-end for tight back/front end integration
* SQL (or sqlite) database for simple queries and data storage
We chose these technologies because they integrate well with front-end apps while having high support for backend configuration. This is good because our app requires a simple GUI with a lot of backend processing.
Further on we can include serverless authentication, though it is not currently needed since we do not support 3rd party authentication (Google, Facebook, etc.)

# The UI
The log in screen will query our database through Java with a simple UI. The application will drop the user into a home screen with shop information and a "login/signup" button will be in the top-right of the screen. If a user is logged in to an admin account, the application will have an "edit info" tab and a "view status" tab on the home screen for pricing and revenue.
The hardware requirements for the client will be a basic browser that supports ES5 (even deprecated browsers like IE support this). The requirements for the server will also be sparse; most computers support the JVM and can do basic http calls. Further requirements will depend on user count.
We took this approach because it negates any Java UI libraries (they aren't easy to write and system support is difficult) and opening a .jar to order pizza seems odd.

# How it will work
An http server will be hoisted on a local port (in production this will be a server). This server will handle routing, while the client will render the hypermedia it receives through a browser.
The hypermedia approach allows us to execute simple ajax calls that are easy to parse on the backend. This also allows us to update the UI in a fine-grained manner; creating a front-end with React, Svelte, Vue, or the like creates challenges we don't need to face.
When the front-end executes an ajax call the backend will parse it, responding with `HTTP 200 OK` and posting the response to our database.
Our database will be made in SQL (or sqlite) and will consist of items, customers (aka accounts), and purchases. When a customer creates an account an ID, name, address, payment info, etc. will be stored. Items are similar (pizza type, cost, inventory, etc.). When a purchase is made a "purchase" item will be stored that consists of a customer id, item id(s), date, and price.
Pricing info, sale count, and other related information will be pulled from this table with ajax requests made in the front-end and parsed in the back end.

# Developer Goals, Approach, Methodology

This product will adhere to the Waterfall process; one product is being produced that won't be iterated on in the future.