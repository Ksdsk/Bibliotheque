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

On closer look, they are three Base64 strings separated by dots `.`. They actually mean a sequence of objects like so:
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
### Header
Every JWT carries a header, also known as a JOSE header, which claims about itself. These claims establish the algorithms used, whether the JWT is signed or encrypted, and how to parse the rest of the JWT.

Claims:
- `alg`: The main algorithm in use for signing and decrypting this JWT. 
	- This must be set to `none` for unencrypted JWTs.
- `typ`: The media type of the JWT itself.
	- This parameter is only meant to be used as a help for uses where JWTs may be mixed with other objects carrying a JOSE header. In practice, this rarely happens. When present, this claim should be set to the value `JWT`.
- `cty`: The content type.
### Payload
The payload is the element where all the interesting user data is usually added. In addition, certain claims defined in the spec may also be present. Just like the header, the payload is a JSON object.  No claims are mandatory.

Claims:
- `iss`: Issuer. A case-sensitive string or URI that uniquely identifies the party that issued the JWT.
- `sub`: Subject. A case-sensitive string or URI that uniquely identifies the party that this JWT carries information about.
	- The claims contained in this JWT are statements about this party. 
- `aud`: Audience. Either a single case-sensitive string or URI or an array of such values that uniquely identify the intended recipients of this JWT.
	- When this claim is present, the party reading the data in this JWT must find itself in the `aud` claim or disregard the data contained in the JWT.
- `exp`: Expiration time. A number representing a specific date and time in UNIX timestamp.
- `nbf`: Not Before time. The opposite of the `exp` claim. A number representing a specific date and time in the UNIX timestamp.
- `iat`: Issued-at time. A number of representing a specific date and time at which this JWT was issued.
- `jti` from JWT ID. A string representing a unique identifier for this JWT.
### Signature
JWS are probably the single most useful feature of JWTs. The purpose of the signature is to allow one or more parties to establish the authenticity of the JWT. Authenticity in this context means the data contained in the JWT has not been tampered with. In other words, any party that can perform a signature check can rely on the contents provided by the JWT. 

However, it does not prevent other parties from *reading* the contents inside the JWT. 

The process of checking a signature of a JWT is known as *validation*. A token is considered valid when all the restrictions specified in its header and payload are satisfied.

Some of the algorithms used for JWTs are:
- `HS256`
- `RS256`,
- `ES256`, and
- `RSASSA-PSS + MGF1 + SHA256`

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
- **Authorization flow:** The client requests an [[Authorization|authorization]] code to the authorization endpoint `/authoirze`. This code can be used against the token endpoint `/token` to request an ID token in JWT format, an access token, or a refresh token.
- Implicit Flow: The client requests tokens directly from the authorization endpoint `/authorize`. The tokens are specified in the request. If an ID token is requested, it is returned in JWT format.
- Hybrid Flow: The client requests both an authorization code and certain tokens from the authorization endpoint `/authorizartion`. If an ID token is requested, it is returned in JWT format. If an ID token is not requested at this step, it may later by requested directly from the token endpoint `/token`.
## Unsecured JWT
(Pushing from tablet!!)