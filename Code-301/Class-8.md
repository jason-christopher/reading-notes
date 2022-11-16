# APIs

## API Design Best Practices

1. What does REST stand for?
   * Representational State Transfer
2. REST APIs are designed around a ____.
   * resource
3. What is an identifier of a resource? Give an example.
   * A URI that uniquely identifies that resource. For example, the URI for a particular customer order might be: `https://adventure-works.com/orders/1`.
4. What are the most common HTTP verbs?
   * GET retrieves a representation of the resource at the specified URI. The body of the response message contains the details of the requested resource.
   * POST creates a new resource at the specified URI. The body of the request message provides the details of the new resource. Note that POST can also be used to trigger operations that don't actually create resources.
   * PUT either creates or replaces the resource at the specified URI. The body of the request message specifies the resource to be created or updated.
   * PATCH performs a partial update of a resource. The request body specifies the set of changes to apply to the resource.
   * DELETE removes the resource at the specified URI.
5. What should the URIs be based on?
   * Nouns (the resource) and not verbs (the operations on the resource).
6. Give an example of a good URI.
   * `https://adventure-works.com/orders`
7. What does it mean to have a ‘chatty’ web API? Is this a good or a bad thing?
   * APIs that expose a large number of small resources. Such an API may require a client application to send multiple requests to find all of the data that it requires. Instead, you might want to denormalize the data and combine related information into bigger resources that can be retrieved with a single request. However, you need to balance this approach against the overhead of fetching data that the client doesn't need.
8. What status code does a successful `GET` request return?
   * 200 (OK)
9. What status code does an unsuccessful `GET` request return?
   * 404 (Not Found)
10. What status code does a successful `POST` request return?
   * 201 (Created)
11. What status code does a successful `DELETE` request return?
   * 204 (No Content)  
   
<https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design>
