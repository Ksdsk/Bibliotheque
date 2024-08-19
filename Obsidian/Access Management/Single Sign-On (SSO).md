> Single Sign-On is a type of authentication in which a user logs in to one system and is automatically granted access to other services.. Rather than having an employee create a separate set of credentials for each app, they simply login once and can access any app the IT administrator has given them access to.

You've likely experienced SSO before. For example, when you sign up for Gmail, you are automatically authenticated to YouTube, AdSense, Analytics, and more. Likewise, if you log out of your Gmail or other Google apps, you are automatically logged out of all the apps.
## How it works
With an example for a typical SSO:
![[Pasted image 20240818230045.png]]
The **authorization server** lives on `domain3`. `domain1` and `domain2` interface with `domain3` to both [[Authentication|authenticate]] a user and also to verify that the user is authenticated. In this implementation, the user will still log in with one of the above-mentioend authentication types. However, they will 