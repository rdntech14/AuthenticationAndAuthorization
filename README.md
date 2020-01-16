# Authentication and Authorization

**Authentication = login + password (who you are)**

**Authorization = permissions (what you are allowed to do)**

## Authentication
Authentication is the practice of validating the identity of a registered user attempting to gain access to an application, API, microservices or any other data resource. 

## Authorization
In contrast, once you are authenticated, authorization is about deciding whether an individual is permitted to perform a given action on a specific resource.

Once you are authenticated to the website, then authorization policies kick in to determine what resources you can access.

There are now many different authentication processes that can be used that can be used to validate a user’s identity.

**Single Sign-On (SSO)** allows a user to leverage a single set of login credentials to access multiple applications. Think using your **Facebook or Google** log in to access several different applications. A technique called **federation** is used by SSO systems when the applications you are logging into are spread across different domains. Industry standards like **Security Assertion Markup Language (SAML)** and **OpenID Connect (OIDC)** facilitate this process.

Multi-Factor Authentication (MFA) requires multiple means of authentication. One example is logging into a website with your username and password but then you are asked to provide a one-time access code that the website sends to the user’s cell phone. The goal is to create multiple security layers to provide a higher level of assurance during the authentication step.


## Auth

The server sends back a header stating it requires authentication for a given realm. The user provides the username and password, which the browser concatenates (username + ":" + password), and base64 encodes. This encoded string is then sent using a "Authorization"-header on each request from the browser. Because the credentials are only encoded, not encrypted, this is highly insecure unless it is sent over https.

https://medium.com/@vivekmadurai/different-ways-to-authenticate-a-web-application-e8f3875c254a

## how to handle authentication on RESTful APIs.

* Cookie-Based authentication
* Token-Based authentication
* Third party access(OAuth, API-token)
* OpenId
* SAML



## Cookie-Based authentication

**Cookie based authentication** has been the default method for handling user authentication for a long time. From the below diagram you can clearly see the client posts the login credential to the server, server verifies the credential and creates session id which is stored in server(state-full) and returned to client via set-cookie. On subsequent request the session id from the cookie is verified in the server and the request get processed. Upon logout session id will be cleared from both client cookie and server.

![alt text](tokenbasedauthe.png)

## Token based authentication
On the other hand **Token based authentication** is gaining in popularity because of the rise in single page applications(SPA) and statelessness(RESTful API’s)of the application. There are different ways to implement token based authentication, we will focussing on most commonly used JSON Web Token(JWT). On receiving the credentials from client the server validates the credentials and generates a signed JWT which contains the user information. Note, the token will never get stored in server(stateless). On subsequent request the token will be passed to server and gets verified(decoded) in the server. The token can be maintained at client side in local storage, session storage or even in cookies.

## Third party access

API 
1) API-Token
2) Open Authentication ( OAuth ) : OAuth can be implemented by either OAuth 1.0 or OAuth 2.0
  2.a) OAuth 1.0
  2.b) OAuth 2.0
  
**Third party access**, if we have a need to expose our API’s outside of our system like third party app or even to access it from mobile apps we end up in two common ways to share the user information.Via API-token which is same as JWT token, where the token will be send via Authorization header which will get handled at API gateway to authenticate the user. And the other option is via Open Authentication(OAuth),OAuth is a protocol that allows an application to authenticate against server as a user. The recommendation is to implement OAuth 1.0a or OAuth 2.0. OAuth 2.0 relies on HTTPS for security and it currently implemented by Google, Facebook, Twitter etc., OAuth 2 provides secured delegate access to a resource based on user. OAuth 2 does this by allowing a token to be issued by Identity provider to these third party applications, with the approval of user. The client then uses the token to access the resource on behalf of that user.


## OpenID is about authentication

## SAML - both authentication and authorization, SAML can provide single sign-on functionality on its own., SAML is older than OAuth

## OAuth, which requires an additional layer like OpenID Connect to perform authentication

https://www.csoonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-works.html
