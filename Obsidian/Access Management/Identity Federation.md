> Federation is a process where one system is responsible for the [[Authentication|authentication]] of a user. That system then sends a message to a second system, announcing who the user is, and verifying that they were properly authenticated. [What is Federation and Why Should Your Apps Support it? | Okta](https://www.okta.com/blog/2019/05/what-is-federation-and-why-should-your-apps-support-it/)
## History
In the days before widespread use of the web, a user would log into a single server and only have to remember one or two passwords. Applications were assumed to be for a single user, and didn't require login credentials. 

Then, as the internet began to gain popularity and applications begin to be run on the web, the number of login credentials a user had to memorize increased from just a few, to several dozen. It also meant the number of user stores grew, creating a number of identity silos. User credentials were no longer centralized in a single directory, but spread over a number of systems across the web. Who was going to manage these credentials and how would they do it in an efficient way? 

*Federation*.
## Importance for Federation
In today's modern world, digital identities are growing exponentially. Every application built comes with its own [[Digital Identity]]. This means your customers, and especially partners, likely already have their own identities, whether from a social application, a custom application, or their enterprise identity. 

When building a new application, providing a method to bring in an existing identity results in:
- **Reduced on-boarding friction**
	- The user already has an identity with their existing IdP, so they don't need to complete a registration flow to create a new account.
- **Better user experience**
	- By redirecting them to their IdP at authentication time, federation provides a sign-on experience that the user is already familiar with. The user may already have a session with their IdP, so another manual log in may be unnecessary.
- **Better user management**
	- The management of all accounts and credentials are delegated to the user's organization, and are no longer the responsibility of the application owner.
## Components of Federation
Here are some casts:
- The first system of a federation is the [[Identity Provider (IdP)]]. 
- The application a user w ants to log into is the Service Provider (SP).
- The message that is sent between the systems is called an *assertion*,

The assertion contains the account name of the user along with other attributes that the SP needs to create a user session. It is cryptographically signed so the SP can trust that it came from the right IdP.

Notice that the SP has nothing to do with the authentication of the user. It trusts the IdP to take care of that. All the SP cares about is that the user was authenticated properly.

But an IdP can be federated to multiple SPs. What does that mean in practice? A user goes to one place to login, then the IdP asserts their identity to the SP that the user is attempting to access. This means there is now a single control point for authentication. By centralizing the user's account and credentials, an administrator has only a single system to perform user management.
## Relationship with current protocols
While [[Security Assertion Markup Language (SAML)]] was cutting edge for its time, by today's standards, it looks very dated. It was designed to enable [[Single Sign-On (SSO)]] from browser-based clients to web servers by passing XML documents. 

Today, modern apps are not always going to be web-based, and an assertion using XML is too heavy for today's uses. Hence, the [[OpenID Connect (OIDC)]] was born. 
### Difference between Federation and SSO
While SSO and Federation allows access to multiple apps using one set of credentials, they are not the same thing. The main difference between SSO and Federation is their range of access.

Think of SSO like having a driver's license. Within your own country, it serves not only as proof that you can drive but also as a handy form if identification within your country for various services. Your driver's license gets you recognized in many scenarios without needing additional ID. The secure token generated during the SSO process acts like your digital proof of identity, similar to showing your driver's license.

Federation expands on this by letting your digital identity be valid across different countries or organizations, similar to how a password works across borders, enabling access without the need for multiple identities.

If you want to support federated SSO in your application in your application for different customers, you'll have to connect it to the multiple IdPs potentially owned by those different organizations. This can get complex fast because:
- Your app must be able to send authorization requests and receive assertion messages from each IdP you're supporting.
- Each IdP might use a different protocol to share authentication data.
- IdPs might also present user data in different formats.
## Federated Identity Management
## Federation Provider
