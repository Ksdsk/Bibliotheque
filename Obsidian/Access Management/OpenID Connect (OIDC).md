> OpenID Connect is an interoperable authentical protocol based on the [[OAuth]] 2.0 framework of specifications. It simplifies the way to verify the identity of users based on the [[Authentication|authentication]] performed by an [[Authorization|authorization]] server to obtain user profile information in an interoperable and REST-like manner. [How OpenID Connect Works - OpenID Foundation](https://openid.net/developers/how-connect-works/)

It enables developers to launch sign-in flows and receive verifiable assertions about users across web-based, mobile, and JS clients. It also provides a secure and verifiable answer to the question of "What is the identity of the person currently using the application that is connected?" while removing the responsibility of setting, storing, and managing passwords which is frequently associated with credential-based data breaches.
## How it works
OpenID Connect enables an internet identity ecosystem through easy integration and support, security, and privacy-preserving configuration, interoperability, wide support of clients and devices, and enabling any entity to be an OpenID Provider.

The OpenID Connect protocol follows these steps:
1. End user navigates to a website or web application via a browser.
2. End user clicks sign-in and types their username and password.
3. The relying party (RP), which is the Client, sends a request to the OpenID Provider (OP).
4. The OP authenticates the User and obtains authorization.
5. The OP responds with an Identity Token and usually an Access Token,
6. The RP can send a request with the Access Token to the User device.
7. The UserInfo Endpoint returns Claims about the End User.
## Example
Many organizations use OIDC to enable secure authentication across web and mobile apps:
- When a user signs up for a Spotify account, they are offered three choices: Sign up with Facebook, Google, or your Email address. Users who choose to sign up with Facebook or Google are using OIDC to create an account. They will be redirected to whichever OP they selected (Facebook or Google) and then once they've signed in, the OP will send Spotify basic profile details. The user doesn't have to create a new account for Spotify and their passwords remain protected.