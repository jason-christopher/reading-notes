# Authentication

## What is OAuth

1. What is OAuth?
   * OAuth is an open-standard authorization protocol or framework that describes how unrelated servers and services can safely allow authenticated access to their assets without actually sharing the initial, related, single logon credential.
2. Give an example of what using OAuth would look like.
   * Using a separate, third-party service to authenticate a user. 
3. How does OAuth work? What are the steps that it takes to authenticate the user?
   1. The first website connects to the second website on behalf of the user, using OAuth, providing the user’s verified identity.
   2. The second site generates a one-time token and a one-time secret unique to the transaction and parties involved.
   3. The first site gives this token and secret to the initiating user’s client software.
   4. The client’s software presents the request token and secret to their authorization provider (which may or may not be the second site).
   5. If not already authenticated to the authorization provider, the client may be asked to authenticate. After authentication, the client is asked to approve the authorization transaction to the second website.
   6. The user approves (or their software silently approves) a particular transaction type at the first website.
   7. The user is given an approved access token (notice it’s no longer a request token).
   8. The user gives the approved access token to the first website.
   9. The first website gives the access token to the second website as proof of authentication on behalf of the user.
   10. The second website lets the first website access their site on behalf of the user.
   11. The user sees a successfully completed transaction occurring.
   12. OAuth is not the first authentication/authorization system to work this way on behalf of the end-user. In fact, many authentication systems, notably Kerberos, work similarly. What is special about OAuth is its ability to work across the web and its wide adoption. It succeeded with adoption rates where previous attempts failed (for various reasons).
4. What is OpenID?
   * OpenID is about authentication: as a commenter on StackOverflow pithily put it: "OpenID is for humans logging into machines, OAuth is for machines logging into machines on behalf of humans."

   <https://www.csoonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-works.html>

## Authorization and Authentication flows

1. What is the difference between authorization and authentication?
   * Authentication is the process of verifying who a user is, while authorization is the process of verifying what they have access to.
2. What is Authorization Code Flow?
   ![Authorization Code Flow](https://images.ctfassets.net/cdy7uua7fh8z/2nbNztohyR7uMcZmnUt0VU/2c017d2a2a2cdd80f097554d33ff72dd/auth-sequence-auth-code.png)
3. What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?
   ![PKCE](https://images.ctfassets.net/cdy7uua7fh8z/3pstjSYx3YNSiJQnwKZvm5/33c941faf2e0c434a9ab1f0f3a06e13a/auth-sequence-auth-code-pkce.png)
4. What is Implicit Flow with Form Post?
   ![Implicit Flow with Form Post](https://images.ctfassets.net/cdy7uua7fh8z/6m0uE4E7Hpzbdhyh9dEuYK/e36c910ff47a7540bf27e23c02822624/auth-sequence-implicit-form-post.png)
5. What is Client Credentials Flow?
   ![Client Credentials Flow](https://images.ctfassets.net/cdy7uua7fh8z/2waLvaQdM5Fl5ZN5xUrF2F/7a6750b784493042d073de709cccd843/Client_Credentials_flow.png)
6. What is Device Authorization Flow?
   ![Device Authorization Flow](https://images.ctfassets.net/cdy7uua7fh8z/1A6jpG3W1H6SC9ZK92NyKd/40af53209f90a7c392f621f329fb4424/auth-sequence-device-auth.png)
7. What is Resource Owner Password Flow?
   ![Resource Owner Password Flow](https://images.ctfassets.net/cdy7uua7fh8z/4EeYNcnVX1RFcTy5z4lP4v/c3e4d22e6f8bf558caf07338a7388097/ROP_Grant.png)
<https://auth0.com/docs/get-started/authentication-and-authorization-flow>
