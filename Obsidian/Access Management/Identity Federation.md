> Federation is a process where one system is responsible for the [[Authentication|authentication]] of a user. That system then sends a message to a second system, announcing who the user is, and verifying that they were properly authenticated. [What is Federation and Why Should Your Apps Support it? | Okta](https://www.okta.com/blog/2019/05/what-is-federation-and-why-should-your-apps-support-it/)
## History
In the days before widespread use of the web, a user would log into a single server and only have to remember one or two passwords. Applications were assumed to be for a single user, and didn't require login credentials. 

Then, as the internet began to gain popularity and applications begin to be run on the web, the number of login credentials a user had to memorize increased from just a few, to several dozen. It also meant the number of user stores grew, creating a number of identity silos. User credentials were no longer centralized in a single directory, but spread over a number of systems across the web. Who was going to manage these credentials and how would they do it in an efficient way? 

*Federation*.
## Components of Federation
Here are some casts:
- The first system of a federation is the [[Identity Provider (IdP)]]. 
- The application a user w ants to log into is the Service Provider (SP).
- The message that is sent between the systems is called an *assertion*,

The assertion contains the account name of the user along with other attributes that the SP needs to create a user session. It is cryptographically signed so the SP can trust that it came from the right IdP.

Notice that the SP has nothing to do with the authentication of the user. It trusts the IdP to take care of that. All the SP cares about is that the user was authenticated properly.

But an IdP can be federated to multiple SPs. What does that mean in practice? A user goes to one place to login, then the IdP asserts their identity to the SP that the user is attempting to access. This means there is now a single control point for authentication. By centralizing the user's account and credentials, an administrator has only a single system to perform user management.
## Relationship with current strategies
While [[Security Assertion Markup Language (SAML)]] was cutting edge for its time, by today's standards, it looks very dated. It was designed to enable [[Single Sign-On (SSO)]] from browser-based clients to web servers by passing XML documents. 

Today, modern apps are not always going to be web-based, and an assertion using XML is too heavy for today's uses. Hence, the [[OpenID Connect (OIDC)]] was born. 