> Single Sign-On is a type of authentication in which a user logs in to one system and is automatically granted access to other services.. Rather than having an employee create a separate set of credentials for each app, they simply login once and can access any app the IT administrator has given them access to.

You've likely experienced SSO before. For example, when you sign up for Gmail, you are automatically authenticated to YouTube, AdSense, Analytics, and more. Likewise, if you log out of your Gmail or other Google apps, you are automatically logged out of all the apps.
## How it works
With an example for a typical SSO:
![[Pasted image 20240818230045.png]]
The **authorization server** lives on `domain3`. `domain1` and `domain2` interface with `domain3` to both [[Authentication|authenticate]] a user and also to verify that the user is authenticated. In this implementation, the user will still log in with one of the above-mentioned authentication types. However, they will only have to provide this set of credentials once. The SSO system will take care of granting authentications.
## Glossary

| Term                                                                                       | Definition                                       |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------ |
| Access Management                                                                          | Administering the logins and apsswords of users  |
| [[Authentication]]                                                                         |                                                  |
| [[Authorization]]                                                                          |                                                  |
| Back-end Server                                                                            |                                                  |
| Claim                                                                                      |                                                  |
| Client                                                                                     |                                                  |
| Credentials                                                                                |                                                  |
| Delegation                                                                                 |                                                  |
| Domain                                                                                     |                                                  |
| Factor                                                                                     |                                                  |
| [[Identity Federation#Federated Identity Management\|Federated Identity Management (FIM)]] |                                                  |
| [[Identity Federation#Federation Provider\|Federation Provider]]                           |                                                  |
| Forest                                                                                     |                                                  |
| Identification                                                                             |                                                  |
| [[Identity Provider (IdP)]]                                                                |                                                  |
| [[Kerberos]]                                                                               |                                                  |
| [[Authentication#Multifactor Authentication\|Multifactor Authentication (MFA)]]            |                                                  |
| Multitenancy                                                                               |                                                  |
| [[OAuth]]                                                                                  |                                                  |
| [[OpenID Connect (OIDC)]]                                                                  |                                                  |
| [[Authentication#Passwordless\|Passwordless]]                                              |                                                  |
| Role                                                                                       |                                                  |
| [[Authorization#Role-Based Access Control (RBAC)\|Role-Based Access Control (RBAC)]]       |                                                  |
| [[Security Assertion Markup Language (SAML)]]                                              |                                                  |
| [[Single Sign-On (SSO)]]                                                                   |                                                  |
| [[Identity Provider (IdP)#Social Identity Provider\|Social Identity Provider]]             |                                                  |
| [[Software-as-a-Service (SaaS)]]                                                           |                                                  |
| [[Digital Identity]]                                                                       |                                                  |
| [[Identity Federation#WS-Federation\|WS-Federation]]                                       |                                                  |
|                                                                                            |                                                  |
