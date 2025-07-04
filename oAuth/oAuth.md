# oAuth


## Authentication vs. Authorization
One might slip in these terms interchangeably, HOWEVER, fundamentally Authentication and Authorization are different.

*Authentication* is to do with verifying who the user is.
*Authorization* is to do with verifying what all access user has.

| **Authentication**                                        | **Authorization**                                      |
|-----------------------------------------------------------|--------------------------------------------------------|
| Determines if the user is who they claim to be            | Determines what the user can access                    |
| Happens before authorization                              | Happens after successful authentication                |
| Usually results in an **ID Token**                        | Usually results in an **Access Token**                 |
| Follows **OpenID Connect (OIDC)** protocol                | Follows **OAuth 2.0** framework                        |
| Identifies the user to check access to the system         | Checks the user's permissions to access specific resources |


## What is oAuth 2.0?
OAuth 2.0 is a widely used authorization protocol that allows third-party applications to access a user's resources without 
having to know their credentials. This replaces oAuth 1.0 protocol.


## What problem oAuth aims at solving?
Think of a traditional client-server model. Client needs some resource which is owned by resource owner. These resources
are hosted on server. So basically client needs resource hosted on server which is owned by some resourse owner. Here the
way to access resourse will be to have client authenticate with server using credentials of resource owner. Once authenticated
client can access the resource.

*So what's the problem?*

Well, here the problem lies in handling the credentials of resource owner to the client. For e.g. lets suppose there is an
application processing images. To process a image one can choose image from device itself or choose to pick one from Google
Photos. In order to access a photo from Google photos the app will need to sign-in into user's google account and then access
the photo. So the app will have to take user's credentials and authenticate with Google and then access the photos. Here
credentials which are sensitive to user are getting shared with a third-party to user and Google which is the app. The issues
this approach create:-

1. Sharing credentials with third-party applications. If third party applications are compromised, credentials sharing can pose security concerns
2. Servers will need to support credential authentication.
3. Access to user's resources to third-party application.
4. Access can't be revoked once granted, unless credentials are changed, which will impact every third-party application.
5. The role of client and resource owner is blurred, as client is somewhat granted full access by sharing password. oAuth
separated these roles and creates a clear distinction between client and resource owner.


## How oAuth fixes the issue?
oAuth introduces an authorization layer and also separates the role of client from acting as resource owner. So with oAuth
client doesn't need user OR resource owner's credentials. With oAuth, client will request access for resource it needs from
server and it will get issued a different credential than what resource owner has. So client instead of using user's credentials
it receives an access token with some expiry. Access tokens are issues by authorization server after approval from resource
owner.
So in a nutshell oAuth:
- Introduces authorization layer
- Issues different set of credentials to client - access token

*Now going back to our app's Google problem discussed before, let's see how oAuth2.0 fixes that*

OAuth 2.0 introduces a secure delegation mechanism where:
	•	The app never sees or handles the user’s credentials (username/password).
	•	The user authenticates directly with Google (the Authorization Server) in a secure environment (usually via a browser or system web view).
	•	After successful login, Google asks the user for consent:
➔ “Do you allow this app to access your Google Photos?”

🔐 The Flow in Simple Steps:
	1.	The app redirects the user to Google’s Authorization page.
	2.	User logs in to Google securely (credentials are only shared with Google, not the app).
	3.	User grants permission for the app to access Google Photos.
	4.	Google issues an Access Token to the app (short-lived, limited in scope).
	5.	The app uses this Access Token to call Google Photos API and fetch the user’s photos.

👉 The app only has the Access Token, not the password.

🔄 Benefits of OAuth 2.0 in this scenario:

| **Problem Without OAuth 2.0**                              | **Solution with OAuth 2.0**                                 |
|------------------------------------------------------------|-------------------------------------------------------------|
| App knows the user’s password                               | App never sees the user’s password                           |
| No way to limit what the app can access                     | Access is limited to specific scopes (e.g., Photos)          |
| No way to revoke app access without password reset          | User or Google can revoke token anytime                      |
| App could misuse the credentials                            | Token-based, time-limited, minimal access                    |


🔑 Key Takeaways:
	•	OAuth 2.0 decouples Authentication from Authorization.
	•	The app doesn’t need to “impersonate” the user—it receives limited permission via tokens.
	•	User remains in control of what the app can and cannot do.



## Roles in oAuth

### 1. Resource Owner
Owns the resource and hence is capable of granting access to the protected resource.

### 2. Resource Server
Resource server is the server hosting the protected resources.

### 3. Client
This is the application which needs access to the protected resource.

### 4. Authorization Server
Issues access tokens to the client after successful authentication.


## Are authorization server and resource server same or different?
These can be same or different.

![oAuth2.0 Basic Flow](resources/oAuth2PointOBasicFlow.png "oAuth2.0 Basic Flow")


## Authorization Grant
Authorization Grant is a credential which represents resource owner's authorization given to client to get access token to
further use token for accessing its protected resources. Following are types of authorization grants available:

### 1. Authorization Code
Authorization Code grant type is flow where client receives a authorization code from the authorization server and then
further uses it to exchange it for an access token.

### 2. Implicit
In implicit grant type flow, access token is issued directly, instead of involving authorization code first. So in this flow
there is no exchange of access token for authorization code.

### 3. Resource Owner Password Credentials
In this grant type, resource owner's credentials i.e. username and password are used directly to obtain access token.

### 4. Client Credentials
This is usually a grant type when client is itself the resource owner.


## Access Token
Access Token is a credential which enables a third party application to access a protected resource owned by resource owner.
Access tokens have a specific scope and duration of access, and will expire eventually.

oAuth2.0 doesn't specifies any format for access token. Most commonly used format of access token is in form of
JSON Web Token (JWT). This format usually consists of three parts separated by dots. Advantage of this format is that one
can also include some data in the token itself.

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c

```

These three parts are Header, Payload and Signature.
Here Header and Payload are base64 encoded JSON objects. Signature part is generated using client's secred and some cryptographic
algorithm.


## Client ID and Client secret
When one registers app with auth provider, then the app is issues a client ID which uniquely identifies the app.
*Client ID* is public identifier for apps. It is public but still its not in format of a readable string which are guessable.

*Client secret* for a public app should not be issued. While registering one's app the auth provider will ask to categorise
the app be it public or confidential etc.
A public app like an iOS mobile app release on app store should not be having *Client secret* in the app binary or bundle
as it might be reverse engineered and leaked.


## What are some practical use cases of oAuth2.0?

### 1. Social media authentication
Many apps, websites enable user to sign-in using their existing social media accounts like Google, Facebook, Twitter etc
instead of creating a new account.

### 2. Single Sign-On (SSO)
oAuth2.0 though isn't designed keeping SSO in mind, however can be used to achieve SSO where multiple applications are set
up using same authorisation server, thus user authenticating with any one application can be free to use any other
applications as well without the need to sign in again.


## What is the format for authorisation server endpoint?
Following is the format of authorisation server endpoint.

```
https://your-auth-server.com/auth?response_type=code&client_id=CLIENT_ID&redirect_uri=REDIRECT_URI&scope=SCOPE&state=STATE
```

Query params :

1. response_type
response_type identifies the authorisation flow client wants to use. For example in the URL mentioned above the value passed
is *code* which means to use authorisation code flow.
Similarly one can pass value as *token* when using implicit grant type.

2. client_id
This is the client id assigned to app when it was registered against authorisation server.

3. redirect_uri
The URI where the authorisation server will redirect to once authorisation is completed.

4. scope
Value of scope parameter limits the rights of access token which is issued. The possible values are determined by the service
being accessed. For example some values can be read, write, profile etc.

5. state
*state* is optional. This is a security measure which is employed to prevent CSRF (Cross Site Request Forgery) attacks.
The way *state* works is by having a unique value passed in *state* param for each authorisation request. The response coming
back from authorisation server returns back same value which is validated back at client side to confirm authenticity of
the response.
This prevents CSRF attacks in way that if some attacker tricks user into clicking a malicious formed URL which creates and
sends request to authorisation server. Now the authorisation server when redirects back to client, the client has no idea
if the response is due to authorisation request client itself initiated. This can be mitigated by including a state in the
authorisation request which is maintained at client end. When the response from authorisation server is received then client
can compare to verify the response received is actually the result of request client only initiated.


## TODOs

- [ ] Check https://supertokens.com/blog/what-is-jwt
- [ ] Add notes for JWT
