# SSL Pinning

SSL : Secure Socket Layer

## What is SSL Pinning?
SSL Pinning is the process of associating a host with its certificate or public key.


## Why do we need SSL Pinning?
In a client server communication, SSL Pinning allows clients to trust only the servers with valid and pre-defined certificate
or public key. While making a secure connection to remote host, using SSL pinning clients can pin the certificate or public
key to the host and only procees with connection with those valid.

It's a security mechanism to prevent *man in the middle (MITM)* attacks. SSL pinning works by validating
server's SSL certificate.

## What are types of SSL Pinning methods?

### 1. Embedding the Certificate OR Certificate SSL pinning
In this approach, remote server's certificate itself is embedded in client or app's bundle.

### 2. Embedding the Public Key OR Public Key pinning
In this approach remote server's certificate's public key is defined in code or kept in client or app's bundle.
In this approach as long as the public key remains same, client will trust the remote even if certificate changes.
In cases where server's certificates changes frequently then public key pinning is preferred.
There is also a concept of *dynamic SSL pinning* where public key is not hardcoded in client code
instead the public key is retrieved from server in initial handshake and then client can cache it for further
usage,

## Digital Certificate

A Digital Certificate is a file which encapsulates certain information about the server owning the certificate or the
server to which the certificate stands for.

Digital Certificates uses *X.509* standards. *X.509* is defined by the *International Telecommunication Unions’s*
standardisation sector. Usually a *Certificate Authority(CA)* issues a certificate. A Digital Certificate
contains following information :
- Subject
- Serial Number
- Issuer
- Valid From
- Valid To
- Public Key
- Algorithm Identifier
- Digital Signature
- Version
- Time Stamp


## How to implement SSL Pinning in iOS Application?

1. SSL Certificate/Public Key/Root Cert
First one needs to decide if to embed certificate or the public key in the app bundle. Then based on choice get the cert
or key and bundle in the app.

2. Networking Layer handling for SSL Pinning
In iOS applications one can use *URLSession* APIs for implementing SSL pinning. 
To do so one needs to implement *URLSessionDelegate* protocol and specifically the method

```
optional func urlSession(
    _ session: URLSession,
    didReceive challenge: URLAuthenticationChallenge,
    completionHandler: @escaping @Sendable (URLSession.AuthChallengeDisposition, URLCredential?) -> Void
)
```

This delegate callback gets called when server presents any authentication challenge.
In this callback, is received a *URLAuthenticationChallenge* having instance property *protectionSpace*.
This *protectionSpace* which is of type *URLProtectionSpace* has an instance property *serverTrust* which represents server's
SSL transaction state.
This propery *serverTrust* is only not nil if the authentication challenge callback received is for server trust.

*protectionSpace* provides information whether the authentication challenge is asking one to provide the user’s credentials
or to verify the TLS credentials provided by the server.

||Server Trust|Users Credentials|
|---|---|---|
|serverTrust|NOT NIL|nil|


## Issues and remedies while implementing SSL Pinning

### 1. Certificate Expiry
Probably most common issue could be certificate expiry itself. If the embedded certificate expires, the app will fail to
establish connection with server.

Reason for expiry
- All issued certificates have an expiry date and need to be renewed updated periodically.

Possible remedies
- Pin certificates public key instead of certificate itself
- Create and follow a schedule to update certificates before expiry and release new app build
- Bypass SSL pinning temporariy and notify users to update app. (TODO: Is this possible?)

### 2. User device issue

## What is the default SSL pinning enforced by App Transport Security.
By default, SSL implementation in an iOS app will trust any server with certificate trusted by the operating system’s
trust store. This is true for other client server communications as well. All operating systems have a trust store which
includes a bunch of certificates.