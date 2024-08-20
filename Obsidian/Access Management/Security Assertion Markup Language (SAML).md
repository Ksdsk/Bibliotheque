> SAML is a login standard that helps users access applications based on sessions in another context. it's a [[Single Sign-On (SSO)]] login method offering more secure authentication than usernames and passwords.

[[Security Assertion Markup Language (SAML)]] is one of the most widely used protocols when it comes to SSO implementations. It exchanges authorization and authentication data in XML format. 

The three components to this data exchange are the:
- User,
	- Who requests a resource from the service provider
- Identity Provider, and
	- Who checks with the identity provider if the user should have access to this resource
- Service provider
	- Who acts as the single source of truth, verifying the user identity and asserting back to the service provider that the user should have access along with the user's identity.

The XML request and response assertions are self-encompassing and independent of the protocol used to transfer them so developers can send these requests in the body of a POST request for example or wrap them in a SOAP binding.

