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

## Token based authenticatio
On the other hand **Token based authentication** is gaining in popularity because of the rise in single page applications(SPA) and statelessness(RESTful API’s)of the application. There are different ways to implement token based authentication, we will focussing on most commonly used JSON Web Token(JWT). On receiving the credentials from client the server validates the credentials and generates a signed JWT which contains the user information. Note, the token will never get stored in server(stateless). On subsequent request the token will be passed to server and gets verified(decoded) in the server. The token can be maintained at client side in local storage, session storage or even in cookies.
