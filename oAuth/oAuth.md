# oAuth


## Authentication vs. Authorization
One might slip in these terms interchangeably, HOWEVER, fundamentally Authentication and Authorization are different.

*Authentication* is to do with verifying who the user is.
*Authorization* is to do with verifying what all access user has.

|Authentication|Authorization|
|---|---|
|Determines if user is who they claim to be|Determines what all user can access|
|It's before Authorization|This follows after Authentication is successfull|
|Usuallu results in ID Token|Usually results in Access Token|
|Follows OpenID Connect (OIDC) protocol|Follows OAuth 2.0 framework|
|This identifies user to check access to system|This checks user to proved access to a resource within system|


## oAuth 2.0
OAuth 2.0 is a widely used authorization protocol that allows third-party applications to access a user's resources without 
having to know their credentials. This replaces oAuth 1.0 protocol.
