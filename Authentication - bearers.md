# bearers

Term
## Client ID: 
the code that the api or oauth provider supplies to determine who registered the app.
## Client Secret   
this is the code that's used to hash the details (both you and the api / oauth provider decrypt using this)
Authentication Endpoint: where you go to 
## Access Token Endpoint
Clients obtain identity and access tokens from the token endpoint in exchange for an OAuth 2.0 grant. The grant is a recognised credential which lets the client access the requested resource (web API) or user identity.
## API Endpoint 
this is the url that the api or github autho wants us to hit with our code and secret with a get request for a token
## Authorization Code
is what I am looking for in response from the github after the user clicks "use github to sign in" 
## Access Token
this is like the wrist band that shows you've already been authenticated and you don't need to do that again until it expires.