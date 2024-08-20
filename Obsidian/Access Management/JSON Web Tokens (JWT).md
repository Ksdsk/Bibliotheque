> JSON Web Token, or JWT for short, is a standard for safely passing claims in space constrained environments. It has found its way into all major web frameworks. Simplicity and compactness and usability are key features of its architecture.

It is an open, industry standard `RFC 7519` method for representing claims securely between two parties. However, arguably the most important aspect of this is the standardization effort in the form of a simple, optionally validated, and encrypted, container format. 

Some of its applications include:
- [[Authentication]],
- [[Authorization]],
- [[Identity Federation]],
- Sessions, and
- Secrets
## Structure
### Visualization
A standard JWT looks kind of like this:
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

On closer look, they are three strings separated by dots `.`. They actually mean a sequence of objects like so:
```css
<Header>.
<Payload>.
<Signature>
```

When decoded, you will find the following:
```json
{
	{
	  "alg": "HS256",
	  "typ": "JWT"
	},
	{ // Claims
	  "sub": "1234567890",
	  "name": "John Doe",
	  "iat": 1516239022
	}
}
```
## Stateless Sessions
Well, these stateless sessions are in fact nothing more than just client-side data. The key aspect of this application lies in the use of signing and encryption to authenticate and protect the contents of the session. JWS (JSON Web Signature) and JWE (JSON Web Encryption) provides the JWT with those ability. However, **client-side data is subject to tampering**.
## Security Considerations
### Signature Stripping
A common method for attacking a signed JWT is to simply remove the signature:
![[Pasted image 20240820000021.png]]
### Cross-Site Request Forgery (CSRF)
CSRF attacks attempts to perform requests against sites where the user is logged in by tricking the user's browser into sending a request from a different site. For example, say we have an HTML code:
```html
<img src="http://target.site.com/add-user?user=name&grant=admin">
```
The above `<img>` tag will send a request to `target.site.com` every time the page that contains it is loaded.  If the user has previously logged into the `target.site.com` and the site used a cookie to keep the session active, this cookie will be sent as well.  This means that the query strings could go through.
### Cross-Site Scripting (XSS)
XSS attacks attempt to inject JS in trusted sides. Injected scripts can then steal tokens from cookies and local storage.
## JWTs in Auth Protocols
### OAuth 2.0
Although [[OAuth]] 2.0 makes no mention of the format of its tokens, JWTs are a good match for its requirements. Signed JWTs make good access tokens, as they can encode all the necessary data to differentiate access levels to a resource, can carry an expiration date, and are signed to avoid validation queries against the authorization server. Several federated identity providers issue access tokens in JWT format.
### OIDC
[[OpenID Connect (OIDC)]] defines several flows which return data in different ways. Some of this data may be in JWT format:
- Authorization flow: The client requests an [[Authorization|authorization]] code to the authorization endpoint `/authoirze`. This code can be used against the token endpo