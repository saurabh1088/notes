# oAuth


## Authentication vs. Authorization
One might slip in these terms interchangeably, HOWEVER, fundamentally Authentication and Authorization are different.

*Authentication* is to do with verifying who the user is.
*Authorization* is to do with verifying what all access user has.

|Authentication|Authorization|
|---|---|
|Determines, if the user is who they claim to be|Determines, what all user can access|
|It's before Authorization|This follows after Authentication is successfull|
|Usually results in ID Token|Usually results in Access Token|
|Follows OpenID Connect (OIDC) protocol|Follows OAuth 2.0 framework|
|This identifies user, to check access to system|This checks user, to provide access to some resource within system|


## oAuth 2.0
OAuth 2.0 is a widely used authorization protocol that allows third-party applications to access a user's resources without 
having to know their credentials. This replaces oAuth 1.0 protocol.


## What problem oAuth aims at solving?
Think of a traditional client-server model. Client needs some resource which is owned by resource owner. These resources
are hosted on server. So basically client needs resource hosted on server which is owned by some resourse owner. Here the
way to access resourse will be to have client authenticate with server using credentials of resource owner. Once authenticated
client can access the resource.

So what's the problem?

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


## TODOs

- [ ] Check https://supertokens.com/blog/what-is-jwt
- [ ] Add notes for JWT
