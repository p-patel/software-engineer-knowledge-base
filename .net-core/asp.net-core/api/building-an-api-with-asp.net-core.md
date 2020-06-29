# Building An API With ASP.NET Core
https://app.pluralsight.com/library/courses/building-api-aspdotnet-core/

## Building Your First API
- Use `ControllerBase` as controller base class (used for API and MVC controllers)
- Use `[ApiController]` attribute on Controller class
- Use `Route("api/[controller]")` attribute on Controller class to define the endpoint URI
- Consider `async` controller actions where appropriate
- Use `[HttpGet]` on the get controller action method to explicitly define the request type to handle
- Action returns `ActionResult` type, use `OK()`, `NotFound()` to return common status code or return a status code explicitly

### Implementing Searching
- Use `[HttpGet("search")]` to define the route of a controller action when required



## Modifying Data
### Model Binding
- Use `[ApiController]` attribute to set controller as an API controller and enable model binding on requests
- Model binding will then attempt to bind data in the request to controller action parameters

### Implementing POST
- Use AutoMapper to map bound model to Entity and then to create model to return to client of the saved Entity
- POST returns status 201, location of created object in HTTP header and created object on success (Use `LinkGenerator` class to generate newly created resource's URI)
- Use controller's `Created() helper method to form a valid POST method response
- Return an appropriate error response if resource creation fails

## Implementing PUT
- Use to update all values of an existing resource
- Returns OK/200 on successful request
- Use AutoMapper to update object retrieved from db and then save it
