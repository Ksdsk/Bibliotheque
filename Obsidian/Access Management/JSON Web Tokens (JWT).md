> JSON Web Token, or JWT for short, is a standard for safely passing claims in space constrained environments. It has found its way into all major web frameworks. Simplicity and compactness and usability are key features of its architecture.

It is an open, industry standard `RFC 7519` method for representing claims securely between two parties. However, arguably the most important aspect of this is the standardization effort in the form of a simple, optionally validated, and encrypted, container format.
## Structure
### Visualization
A standard JWT looks kind of like this:
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```
On closer look, they are three strings separated by dots `.`. When decoded, you will find the following:
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
