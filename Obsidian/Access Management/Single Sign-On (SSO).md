> Single Sign-On is a type of authentication in which a user logs in to one system and is automatically granted access to other services.. Rather than having an employee create a separate set of credentials for each app, they simply login once and can access any app the IT administrator has given them access to.

You've likely experienced SSO before. For example, when you sign up for Gmail, you are automatically authenticated to YouTube, AdSense, Analytics, and more. Likewise, if you log out of your Gmail or other Google apps, you are automatically logged out of all the apps.
## How it works
With an example for a typical SSO:
![[Pasted image 20240818230045.png]]
The **authorization server** lives on `domain3`. `domain1` and `domain2` interface with `domain3` to both [[Authentication|authenticate]] a user and also to verify that the user is authenticated. In this implementation, the user will still log in with one of the above-mentioned authentication types. However, they will only have to provide this set of credentials once. The SSO system will take care of granting authentications.
## Glossary

| Term                                                                                       | Definition                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Access Management                                                                          | Administering the logins and passwords of users across a range of apps and resource - typically contained inside a single organization.                                                                 |
| [[Authentication]]                                                                         | Validating an identity as true or false.                                                                                                                                                                |
| [[Authorization]]                                                                          | Specifying which resources a user should be allowed to access.                                                                                                                                          |
| Back-end Server                                                                            | A server where user information is processed that the user cannot access.                                                                                                                               |
| Claim                                                                                      | A declaration about a subject that is supposed to be true and trusted depending on the identity provider. For example, an attribute like name, role, or permission.                                     |
| Client                                                                                     | An application that obtains information from a server for local use.                                                                                                                                    |
| Credentials                                                                                | Usernames, passwords, email addresses - any of a variety of means for communicating parties to generate or obtain security tokens.                                                                      |
| Delegation                                                                                 | Calling external APIs to authenticate and authorize users. Keeps apps and services from having to store passwords and user information on-site.                                                         |
| Domain                                                                                     | A network where all resources and users and linked to a centralized database on which all authentication and authorization takes place.                                                                 |
| Factor                                                                                     | In authentication, a vector through which identity can be confirmed. There are three basic categories - knowledge factors, ownership factors, and inherence factors.                                    |
| [[Identity Federation#Federated Identity Management\|Federated Identity Management (FIM)]] | A system of shared protocols that allow user identities to be managed across organizations.                                                                                                             |
| [[Identity Federation#Federation Provider\|Federation Provider]]                           | An identity provider that provides single sign-on, consistency in authorization practices, attributes exchange practices, and user management practices between identity providers and relying parties. |
| Forest                                                                                     | A collection of domains overseen by one central authority.                                                                                                                                              |
| Identification                                                                             | The process by which a user's information is received, collected, and taken up for authentication.                                                                                                      |
| [[Identity Provider (IdP)]]                                                                | A website, app, or service responsible for coordinating identities between users and clients.                                                                                                           |
| [[Kerberos]]                                                                               | A ticket-based protocol for authentication built on symmetric-key cryptography.                                                                                                                         |
| [[Authentication#Multifactor Authentication\|Multifactor Authentication (MFA)]]            | An authentication process that takes into account multiple factors.                                                                                                                                     |
| Multitenancy                                                                               | A term in software architecture referring to the serving of many users from a single instance of an application.                                                                                        |
| [[OAuth]]                                                                                  | An open standard for authorization. See linked for details.                                                                                                                                             |
| [[OpenID Connect (OIDC)]]                                                                  | An open standard for authentication. Built on top of OAuth. See linked for details.                                                                                                                     |
| [[Authentication#Passwordless\|Passwordless]]                                              | A form of authentication based on tokens, most commonly received and sent through SMS, email, or biometric sensors.                                                                                     |
| Role                                                                                       | An aspect of a user's identity that gives them certain permissions.                                                                                                                                     |
| [[Authorization#Role-Based Access Control (RBAC)\|Role-Based Access Control (RBAC)]]       | A model for authorization based on users gaining certain permissions based on their roles.                                                                                                              |
| [[Security Assertion Markup Language (SAML)]]                                              | An authentication and authorization standard commonly found in the enterprise, SAML differs from OpenID in that it does not dynamically discover and accept authentication from new identity providers. |
| [[Single Sign-On (SSO)]]                                                                   | A subset of federated identity management, a means through which authentication and interoperability can be achieved in a federated system.                                                             |
| [[Identity Provider (IdP)#Social Identity Provider\|Social Identity Provider]]             | A term used to refer to identity providers originating in social services like Facebook, Google, X, etc.                                                                                                |
| [[Software-as-a-Service (SaaS)]]                                                           | A model for software purchasing that relies on a monthly subscriptions rather than the one-time purchase of a license.                                                                                  |
| [[Digital Identity]]                                                                       | Identifying characters                                                                                                                                                                                  |
| [[Identity Federation#WS-Federation\|WS-Federation]]                                       | A federated standard or common infrastructure for identity, used both by web services and browsers on Windows Identity Foundation.                                                                      |
|                                                                                            |                                                                                                                                                                                                         |
## SSO and AuthX
### Authentication
A good [[Authentication|authentication]] experience can seem at odds with properly implemented security. Many organizations require a strong password, and some even ask the users to change their password every interval. 

Keeping up with these requirements for one application is inconvenient enough, but doing so for five or ten applications leads users to adopt some pretty bad practices like reusing the same password for each app, writing down their passwords on a sticky note and taping on their monitor, and so on.

Authentication experience is simplified for the user, while the organization benefits from better security.
### Authorization
Ensuring the right level of access is very important and is difficult to do in a non-SSO implementation. Different applications present different levels of granularity when it comes to user permission which makes [[Authorization|authorization]] even more difficult. SSO aims to solve this authorization component of identity by providing a centralized source of truth for each individual user. Once a user is authenticated, the IdP can send each application the users' identity permissions for each application. IT admins now have a single location where they can manage user roles and permissions for the entire organization. This makes it easier to audit and ensure the right users have the right access at all times.

Authorization experience is handled from a centralized location and can be easily managed.
## Federation
SSO provides a solution for all components related with authentication and authorization. Through [[Identity Federation]], an IT administrator can provision and deprovision user accounts once, grant them varying levels of access for each app, and enforce security requirements all from a single source of truth.
## Identity Protocols and Providers
Let's highlight some of the common protocols used in SSO, their benefits and downsides, and examples where these protocols are used in:
- [[Security Assertion Markup Language (SAML)]]
- [[OAuth]]
- [[OpenID Connect (OIDC)]]
## Customer Perspective for Implementing SSO
### Advantage
The big reasons to buy an identity management platform is that you can get your solution up-and-running in no time. Saving time versus building, testing, quality-assuring, and deploying a home-grown solution can mean be very slow. 
### Disadvantage
The disadvantage to buy an identity management platform for SSO is that you use some control. The customer's identity data is stored in a third-party server. It also means you are adding another dependency to the technology stack. It may not also be customizable to your needs.
## Implementation
#ToDo

