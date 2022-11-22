# CRUD

## Status Codes Based On REST Methods

1. In your own words, describe what each group of status code represents:

100’s = Informational
200’s = Success
300’s = Redirection
400’s = Client Error
500’s = Server Error

2. What is a status code 202?
   * Accepted - Often used for asynchronous processing. This code tells the client that the request was valid, but its processing will finish sometime in the future.
3. What is a status code 308?
   * Permanent Redirect - This tells the client to use another URL to access the resource and not use the current URL anymore.
4. What code would you use if an update didn’t return data to a client?
   * 204 No Content
5. What code would you use if a resource used to exist but no longer does?
   * 204 No Content?
6. What is the ‘Forbidden’ status code?
   * 403 Forbidden

## Build A REST API With Node.js, Express, & MongoDB

1. Why do we need to pull our MongoDB database string out of our server and put it into our .env?
   * Because it is sensitive information that we don't want to be made public.
2. What is middleware?
   * Code that runs after the server gets a request, but before it gets passed to your route.
3. What does app.use(express.json()) do?
   * Let's the server accept JSON as a body.
4. What does the /:id mean in a route?
   * The `:` means `id` is a parameter that we can access later.
5. What is the difference between PUT and PATCH?
   * `patch` only updates based on what the user passes, while `put` updates all the information all at once, not just what was passed.
6. How do you make a default value in a schema?
   * Use the `default:` property in the schema object.
7. What does a 500 error status code mean?
   * Server Error
8. What is the difference between a status 200 and a status 201?
   * Status 200 is just a "success" message, while Status 201 is more specific meaning that something was successfully created.
