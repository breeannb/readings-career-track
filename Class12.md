# Class 12: User Auth 

## [Why you should use bcrypt](https://medium.com/@danboterhoven/why-you-should-use-bcrypt-to-hash-passwords-af330100b861)
- Bcrypt used to hash passwords 
- Hashed password solutions fall short
    - Plain text passwords
        - a plain text password makes use of only letters.
        - if a  hacker gains access, they can pose as a user in the system
        - plain text passwords are often replicated across other logins, that gives hackers access to other applications 
    - One way hash
        - a server does not store plain text passwords to authenticate a user.
        - a password has a hashing algorithm applied to it to make it more secure. While in theory, this is a far better password solution, hackers have found ways around this system as the algorithm used is not exactly a one-way option at all.
    - ‘Salting’ the password
        - a ‘salt’ adds a very long string of bytes to the password.
        - So even though a hacker might gain access to one-way hashed passwords, they should not be able to guess the ‘salt’ string.
        - but if a hacker has access to your source code, they will easily be able to find the ‘salt’ string for passwords.
    - Random ‘salt’ for each user
        - a random ‘salt’ string could be added for each user, created on the generation of the user account.
        - This will increase encryption significantly as hackers will have to try to find a password for a single user at a time.
        - Again, even though it means they will have to spend more time cracking the passwords for multiple users, they will still be able to gain access to your resources. It just takes longer.
    - The BCrypt Solution
        - BCrypt is based on the Blowfish block cipher cryptomatic algorithm and takes the form of an adaptive hash function.
        - Using a Key Factor, BCrypt is able to adjust the cost of hashing.
        - With Key Factor changes, the hash output can be influenced. In this way, BCrypt remains extremely resistant to hacks, especially a type of password cracking called rainbow table.
        - This Key Factor will continue to be a key feature as computers become more powerful in the future. Why? Well, because it compensates for these powerful computers and slows down hashing speed significantly. Ultimately slowing down the cracking process until it’s no longer a viable strategy.

## [Understanding bcrypt](https://auth0.com/blog/hashing-in-action-understanding-bcrypt/)
- The bcrypt hashing function allows us to build a password security platform that scales with computation power and always hashes every password with a salt.
- 

## [Where to store JWT](https://auth0.com/docs/tokens/concepts/token-storage)
- Token Storage
    - Securing single page apps (SPAs) that make API calls come with their own set of concerns. You'll need to ensure that tokens and other sensitive data are not vulnerable to cross-site scripting and can't be read by malicious JavaScript.
- Next.js static site scenarios
    - When you're building a Next.js application, authentication might be needed in the following cases:
        1. When accessing a page
        2. When accessing an API route
        3. When your application calls an API hosted outside of your Next.js application on behalf of the user
    - Where a server is available, your app can handle the interaction with Auth0 and create a session, but in this model, we don't have a backend. All of the work happens on the frontend:
        1. The user is redirected to Auth0.
        2. When the user is successfully signed in, they will be redirected back to the application.
        3. The client-side will complete the code exchange with Auth0 and retrieve the user's id_token and access_token which will be stored in memory.
- Traditional Web app scenarios 
    - If your app is using a sign in scenario that doesn't require API calls, only an ID Token is required. There is no need to store it. You can validate it and get the data from it that you required.
    - If your app needs to call APIs on behalf of the user, Access Tokens and (optionally) Refresh Tokens are needed. These can be stored server-side or in a session cookie. The cookie needs to be encrypted and have a maximum size of 4 KB. If the data to be stored is large, storing tokens in the session cookie is not a viable option.
    - Use the following flow types in these scenarios:
        - [Authorization Code Flow](https://auth0.com/docs/flows/concepts/auth-code)
        - R[egular Web App Quickstarts](https://auth0.com/docs/quickstart/webapp)
- Native/Mobile app scenarios
    - Store tokens in a secure storage that the OS offers and limit access to that storage. For example, leverage KeyStore for Android and KeyChain for iOS.
    - Use the following flow types in these scenarios:
        - [Authorization Code Flow with Proof Key for Code Exchange](https://auth0.com/docs/flows/concepts/auth-code-pkce)
        - [Saving and Renewing Tokens for Android](https://auth0.com/docs/libraries/auth0-android/save-and-refresh-tokens) 
        - [Saving and Renewing Tokens for Swift](https://auth0.com/docs/libraries/auth0-swift/save-and-refresh-jwt-tokens)
        - [Native/Mobile Apps Quickstarts](https://auth0.com/docs/quickstart/native)
- Single-page app scenarios
    - When the SPA calls only an API that is served from a domain that can share cookies with the domain of the SPA, no tokens are needed. OAuth adds additional attack vectors without providing any additional value and should be avoided in favor of a traditional cookie-based approach. For an overview of this approach and an example implementation, see SPA Authentication Using Cookies.
    - When the SPA calls multiple APIs that reside in a different domain, access and optionally refresh tokens are needed.
        - If the SPA backend can handle the API calls, handle tokens server-side using:
            - [Authorization Code Flow](https://auth0.com/docs/flows/concepts/auth-code)
            - [Authorization Code Flow with Proof Key for Code Exchange (PKCE)](https://auth0.com/docs/flows/concepts/auth-code-pkce)
            - [Hybrid Flow](https://auth0.com/docs/api-auth/grant/hybrid)
        - If the SPA backend cannot handle the API calls, the tokens should be stored in the SPA backend but the SPA needs to fetch the tokens from the backend to perform requests to the API. A protocol needs to be established between the backend and the SPA to allow the secure transfer of the token from the backend to the SPA.
        - If you have a SPA with no corresponding backend server, your SPA should request new tokens on login and store them in memory without any persistence. To make API calls, your SPA would then use the in-memory copy of the token.
- 
