> Single Sign-On is a type of authentication in which a user logs in to one system and is automatically granted access to other services.. Rather than having an employee create a separate set of credentials for each app, they simply login once and can access any app the IT administrator has given them access to.

You've likely experienced SSO before. For example, when you sign up for Gmail, you are automatically authenticated to YouTube, AdSense, Analytics, and more. Likewise, if you log out of your Gmail or other Google apps, you are automatically logged out of all the apps.
## History
The rise of the web changed the way software was consumed. [[Software-as-a-Service (SaaS)]] has become the standard by which modern applications and services are accessed. This model allowed for many start-ups to build specialized products that focused on a singular task and do it well. Protecting each individual software would be extremely hard and tiring for many. This is when the idea of SSO arose.
### Username and Password
Username and Password [[Authentication|authentication]] is the tried-and-true method of protecting application. This is a commonplace to this day because it provides a simple experience that most people are familiar with. Since the credentials for this type of authentication are stored in a database, passwords must be hashed and salted. 

> Hashing is the act of cryptographically translating the password into a one-way verifiable key. Salting is the act of adding a random string of characters before hashing them.

Enhancing this flow comes in the flavour of enforcing strong password requirements, forcing password changes every so often, and preventing password reuse.
### Social
Social authentication has gained prominence in the last few years because it allows organizations to authenticate users with existing accounts. These social applications, or really, any type of applications that act as an identity provider is called a [[Identity Federation|Federated Identity Manager]].

This type of authentication has the benefit of allowing an application to offload many of the authentication, user data storage, and security duties to the social authentication provider. An organization can simply take the unique id from the social provider and use it as the identifier in their application.

However, the drawbacks are clear, such as the ability for the social authentication provider to stop providing access which would break the systems' authentication system. This is called *account linking*.
### Passwordless
Passwordless authentication is an up-and-coming methods of authentication that aims to improve the traditional username and password experience. Wherein username and password authentication a user is required to provide both a username and password, with this type of authentication, the user simply provides their username.

With the username provided, the system generates a one-time passcode, referred to as an OTOP, and delivers it to the user via email, SMS, or a dedicated app. Once the user provides the code back to the system and it has been verified as legit, then the user will be authenticated.
### Multifactor Authentication
Multifactor authentication is the combination of any of the above types of authentication 