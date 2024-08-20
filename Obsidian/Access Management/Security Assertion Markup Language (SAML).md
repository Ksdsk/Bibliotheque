> SAML is a login standard that helps users access applications based on sessions in another context. it's a [[Single Sign-On (SSO)]] login method offering more secure authentication than usernames and passwords.

This protocol is one of the most widely used protocols when it comes to SSO implementations. It exchanges [[Authorization]] and [[Authentication]] data in XML format. 

The three components to this data exchange are the:
- User,
	- Who requests a resource from the service provider
- Identity Provider, and
	- Who checks with the identity provider if the user should have access to this resource
- Service provider
	- Who acts as the single source of truth, verifying the user identity and asserting back to the service provider that the user should have access along with the user's [[Digital Identity]].
## Characteristics of SAML
The XML request and response assertions are self-encompassing and independent of the protocol used to transfer them so developers can send these requests in the body of a POST request for example or wrap them in a SOAP binding.
## Benefits
One of the major benefits of SAML is that the protocol is only concerned with handing the exchange between the [[Identity Provider (IdP)]] and the service provider. The [[Authentication|authentication]] aspect is not defined in the protocol, so developers are free to choose how users authenticate.

> For example, if you have an existing database of users, you can have them validate against the database rather than rebuilding your identity management system from scratch.

With SAML, you are not limited to the number of identity or service providers. One IdP can interact with many service providers and one service provider can interact with many identity providers. This capability ensures that your organization will be able to interact with not just your own internal applications, but also third-party applications.

