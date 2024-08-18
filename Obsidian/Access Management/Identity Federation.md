> Federation is a process where one system is responsible for the [[Authentication|authentication]] of a user. That system then sends a message to a second system, announcing who the user is, and verifying that they were properly authenticated. [What is Federation and Why Should Your Apps Support it? | Okta](https://www.okta.com/blog/2019/05/what-is-federation-and-why-should-your-apps-support-it/)
## History
In the days before widespread use of the web, a user would log into a single server and only have to remember one or two passwords. Applications were assumed to be for a single user, and didn't require login credentials. 

Then, as the internet began to gain popularity and applications begin to be run on the web, the number of login credentials a user had to memorize increased from just a few, to several dozen. It also meant the number of user stores grew, creating a number of identity silos. User credentials were no longer centralized in a single directory, but spread over a number of systems across the web. Who was going to manage these credentials and how would they do it in an efficient way? 

*Federation*.
## Components of Federation
Here are some casts:
- The first system of a federation is the [[Identity Provider (IdP)]]. 
- The application is 