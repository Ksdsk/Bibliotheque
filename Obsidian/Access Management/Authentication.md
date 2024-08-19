> Authentication is the act of validating that users are whom they claim to be. This is the first step in any security process. [Authentication vs. Authorization | Okta](https://www.okta.com/identity-101/authentication-vs-authorization/)

Authentication is important because it helps organizations protect their systems, data, networks, websites, and more from attacks. It helps individuals keep their personal data confidential, empowering them to conduct business with less risk. With a weak authentication system, you are risking yourself to:
- Data break or exfiltration,
- Installation of malware, such as ransomware, or
- noncompliance with regional or industry data privacy regulations.
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
Multifactor authentication is the combination of any of the above types of authentication. Usually, the act of asking the user for an additional piece of data like the [[#Passwordless]] structure is quite common.
### Identity Federation and Single Sign-On
[[Identity Federation]] and [[Single Sign-On (SSO)]] go hand-in-hand. SSO allows a user to login once and gain access to multiple disparate apps and services. Federation deals with managing user identities and granting them the rights and privileges to log into these disparate apps and services.

