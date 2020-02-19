API guidelines
This page regroups good practices / principles / guidelines for designing APIs, that should be followed for exposed APIs whenever possible (Please documents variations on these principles).

It was made from existing sources, internal and external – see references at bibliography.

Main API Principles
·         Internal and external services are the same

·         Consumer agnostic (but target main use cases first)

·         Stateless whenever possible

·         Idempotent services whenever possible: calling service multiple times has the same effect

·         Affordance: API should be self explaining and intuitive:

o    Use english

o    Use standard, concrete and shared terms, not BIL specific terms/acronyms

·         No different ways to achieve the same action

·         Tolerant reader, conservative writer (Postel’s law)

·         Prefer asynchronous backend (through decoupling component if critical)

·         Design RESTful services, using HTTPS and JSON (+ specify Content-Type and Accept headers to application/json)

·         Responses should be enveloped in a common structure (generalized or project specific)

o    Avoid JSON hijacking

o    Enable meta-data enrichment

o    Pagination

o    Links to other resources

·         API First approach: API stability is more important than internal implementation.

o    as a conclusion, we recommend not to expose services publicly using Spring Data REST, because it relays the internal DB implementation in the API (even if it can be used for POCs or internal short-term needs)

Main REST principles
Verb

Effect

Idempotent

Safe

GET

Request data

X

X

POST

Create a resource+ Can also be used to Trigger an action (i.e. https://server/api/config/refresh)

PUT

Update a resource, or create it if it doesn’t exist

X only for main resource(not metadata like creation date)

DELETE

Removes a resource, or make it un-reachable(Meaning forthcoming access will issue a 404)

X for resource(but not for return code)

HEAD

Same as GET but no response body. Useful for retrieving headers meta-data

X

X

OPTIONS

Retrieve the HTTP methods supported by a specific URL. Useful for CORS

X

X

PATCH

Applies partial modifications to a resource (not often used, for huge resources)

X

Legend:

* idempotent: multiple requests will have the same effect
* Safe: do not modify resources
Examples
Resource

GET (read)

POST (create)

PUT (update)

DELETE

/cars

Returns a list of cars

Create a new car

Bulk update of cars

Delete all cars

/cars/711

Returns a specific car

Method not allowed (405)

Updates a specific car

Deletes a specific car

Service Names Conventions:

* Use noun instead of verbs for resources (/cars but not /getAllCars), except when we need a “non-resource” service (see non-resource services)
* Use plurals (/cars)
Case conventions
For URLs: it is better to not rely on case sensitivity (because of Windows servers), so we propose to use hyphen-separated words, called spinal-case or kebab-case.

Example:

/user-certificates/<id>
For JSON body: to be consistent with current Java tools, we propose to keep the lower camel case approach.

Example:

{
  "body": {},
  "statusCode": "100",
  "statusCodeValue": 0
}
Sub Resources
Use sub-resources when relations.

Example:

GET /cars/711/drivers
But use optimal granularity for resources, to on the one hand avoid performance issues if client need to call multiple services, and on the other hand avoid too much coupling resources:

·         Group resources that are accessed together

·         Limit embedded collections if number of elements is high

Non-Resource services
If it’s not possible/adapted to expose a service as a resource, but you need an action, use a verb in the URL (after the resource path if there is one) and use POST method.

This use case below is specific : the blocking of a card can be irreversible, so this case is not just a change of status (PUT request to change the status), but it is a specific action which will be applied to our resource.

Example:

POST /cards/{cardNumber}/block
Prefer standard HTTP verbs if possible.

Sorting, filtering, pagination
These are optional and depend on the services, volumes, use cases.

They are supported by using query parameters.

Pagination
Services can support paging, according to volumes.

In the query, pass a size and page parameters:

/resources?size=20&page=1
The response can contain the links to next (and potentially previous) calls for next/previous pages (see HATEOAS section).

This would fetch the resources from offset 21 to 40 (because page 1 starting at 0)

No state of paging is kept on the service (service is still stateless).

Please validate pagination size (avoid user asking for thousands or millions of entries), especially if the API is open to the outside world. for example: limit size to 250 (For spring boot microservices this can be set with the following property: spring.data.web.pageable.max-page-size=250). This is application specific.

Filtering
In case it is useful to allow filtering to restrict the queried resources, use the field name directly as a query parameter:

/payments?type=webbanking
Sorting
In case it is useful to return sorted results, the query should contain multiple sort parameters with the names of the attribute(s) for sorting. In case the sorting order should be specified then the attribute name can be followed by a “,X” where X is either asc (for ascending) or desc (for descending). Example for sorting payments by date (asc) and amount (desc):

/customers/<id>/payments?sort=date&sort=amount,desc
Field selection
If resources are big and clients have low bandwith, it is possible to specify the fields that should be returned on a resource by using fields parameter:

/resources/<id>?fields=firstname,name
You can also exclude some fields with the exclude query paremeter

/resources/<id>?exclude=firstname,name
Handle Errors with HTTP Status Codes
Codes

Meaning

2xx

Success

200

Ok

201

Created

204

No Content

3xx

Redirection

304

Not Modified

4xx

Client errors

400

Bad Request

401

Unauthorized

403

Forbidden

404

Not Found

410

Gone

5xx

Server errors

500

Internal Server Error

503

Service unavailable

Responses
Error responses
Errors response varies whether they are generated by the framework you are using, or whether you are catching them and generate your own business errors with a specific payload.

Standard Spring errors are of the following form:

{
  "timestamp": "2018-11-06T11:48:57.038+0000",
  "status": 501,
  "error": "Not Implemented",
  "message": "bar",
  "path": "/foo"
}
Custom errors could be of the following form (let's say for validation):

{
  "data": null,
  "error": {
    "code": "400",
    "message": "The string you provided is not Base64 valid"
  },
  "page": null
}
Messages are not mandatory, sometimes it's easier and safer to just respond with a HTTP status code and no more. In the example above you could just issue a HTTP 400 and stop there. It can be useful in development to return error messages.

No golden rule here.

OK responses
Valid responses as said before should use some kind of envelope where metadata can be added.

We propose that the envelope look like this:

{
  "data": ...,
  "error": null,
  "page": {
    "pageNumber": ...,
    "pageSize": ...,
    "offset": ...,
    "sort": {
      "sorted": ...,      // true / false
      "directions": ...,  // ommitted if empty
    },
    "totalPages": ...,
    "totalElements": ...
  }
}
For example let's say that we call an API which return bank cards at http://localhost:8080/cards/1/movements?size=2 :

{
  "data": [
    {
      "id": 1,
      "date": "2018-11-06T12:08:21.329+0000",
      "amount": 4.95,
      "label": "Frapuccino Double Chocolatey Chips",
      "recipient": "Starbucks"
    },
    {
      "id": 2,
      "date": "2018-11-06T12:08:21.335+0000",
      "amount": 2.99,
      "label": "Creamy Bagel",
      "recipient": "Starbucks"
    }
  ],
  "error": null,
  "page": {
    "pageNumber": 0,
    "pageSize": 2,
    "offset": 0,
    "sort": {
      "sorted": false
    },
    "totalPages": 2,
    "totalElements": 3
  }
}
We specifically asked for pages of data containing only two elements per page, thus the metadata of our envelope returns various information that are sufficient for you to build some kind of pagination. It says totalPages: 2 and totalElements: 3.

Now if you ask for the second page (page = 1, starting at 0 like arrays/list) at http://localhost:8080/cards/1/movements?size=2&page=1

{
  "data": [
    {
      "id": 3,
      "date": "2018-11-06T12:08:21.336+0000",
      "amount": 5100.00,
      "label": "Omega Seamaster Aqua Terra \"Skyfall\"",
      "recipient": "Omega"
    }
  ],
  "error": null,
  "page": {
    "pageNumber": 1,
    "pageSize": 2,
    "offset": 2,
    "sort": {
      "sorted": false
    },
    "totalPages": 2,
    "totalElements": 3
  }
}
You can see that response is different, the data returned is the last page with new information.

Now you can also ask to sort results by label ascending and amount descending like this http://localhost:8080/cards/1/movements?sort=label,ASC&sort=amount,DESC

{
  "data": [
    {
      "id": 2,
      "date": "2018-11-06T12:08:21.335+0000",
      "amount": 2.99,
      "label": "Creamy Bagel",
      "recipient": "Starbucks"
    },
    {
      "id": 1,
      "date": "2018-11-06T12:08:21.329+0000",
      "amount": 4.95,
      "label": "Frapuccino Double Chocolatey Chips",
      "recipient": "Starbucks"
    }
  ],
  "error": null,
  "page": {
    "pageNumber": 0,
    "pageSize": 2,
    "offset": 0,
    "sort": {
      "sorted": true,
      "directions": {
        "label": "ASC",
        "amount": "DESC"
      }
    },
    "totalPages": 2,
    "totalElements": 3
  }
}
Domain Names
For Production, for API accessible externally, use:

https://api.bil.com/<domain>/<resource>
The Developer portal (PSD2) will be available at:

https://developer.bil.com
And the Customer SSO will be available at:

https://login.bil.com
HATEOAS
Hypermedia As The Engine Of Application State is a principle that hypertext links should be used to create a better navigation through the API.

It may be useful to expose HATEOAS links for some kinds of clients, but it is not mandatory.

Syntax

Current Spring Syntax:

"links": [ {
   "rel": "self",
   "href": "http://localhost:8080/product/3"
 },
 {
   "rel": "product.search",
   "href": "http://localhost:8080/product/search"
} ]
Other syntaxes exist, and could be studied:

·         check HAL IETF draft see https://tools.ietf.org/html/draft-kelly-json-hal-08

·         check how to use HAL with Spring: see https://www.logicbig.com/tutorials/spring-framework/spring-hateoas/enable-hypermedia-support-hal.html

·         add HTTP verb?

·         …

Decision 19/10/18: we propose to not specify common syntax for now, but wait until some services where it makes sense expose HATEOAS services, in order to gain in maturity on the subject.

Swagger / Open API
Swagger is an open source software framework backed by a large ecosystem of tools that helps developers design, build, document, and consume RESTful Web services.

With Spring Boot
BIL Spring Boot Commons
A project has been created to handle these kind of configurations automatically, please see: https://bf-gitlab/gitlab/DigitalBanking/bil-spring-boot-commons

Maven specific
For Spring Boot microservices you can easily add Swagger and Swagger UI to your project by relying on the springfox-swagger + springfox-swagger-ui Maven artifacts.

<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>2.9.2</version> <!-- check versions on maven central repo -->
</dependency>
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>2.9.2</version> <!-- check versions on maven central repo -->
</dependency>
Spring configuration
You'll also need some configuration to make your API more readable for other developers.

This is an example of Spring's config bean for Swagger configuration:

@Configuration
@EnableSwagger2
public class SwaggerConfig {
    private final TypeResolver typeResolver;
 
    @Autowired
    public SwaggerConfig(TypeResolver typeResolver) {
        this.typeResolver = typeResolver;
    }
 
    @Bean
    public Docket api() {
        return new Docket(DocumentationType.SWAGGER_2)
            .groupName("YOUR_SERVICE")
            .select()
            .apis(RequestHandlerSelectors.any())
            .paths(PathSelectors.regex("/(myservice|public)/.*")) // expose only /myservice/* and /public/*
            .build()
            .directModelSubstitute(LocalDate.class, String.class) // Susbstitute Java's LocalDate with String (for IO)
            .genericModelSubstitutes(ResponseEntity.class) // Substitute Spring's ResponseEntity content with their content
            .ignoredParameterTypes(AuthenticationPrincipal.class, Authentication.class) // Ignore Authentication parameters (since we're using Headers for JWT)
            .alternateTypeRules(
                    newRule(typeResolver.resolve(DeferredResult.class,
                            typeResolver.resolve(ResponseEntity.class, WildcardType.class)),
                            typeResolver.resolve(WildcardType.class))); // Try to retrieve generic parameters and expose them in the generated Swagger doc
    }
}
Additional documentation for this project can be found at the following URL: https://springfox.github.io/springfox/docs/current/

For your Spring REST controller please use @RestController instead of @Controller. Please use shortcuts like @GetMapping, @PostMapping and so on instead of @RequestMapping, or at least be specific about the method, otherwise they will show up multiple times in the Swagger generated documentation.

Swagger annotations
Use Swagger specific annotations to help describe your operations.

·         ApiOperation

·         ApiResponses

·         ApiParam

·         …

Versioning
It may depend on API Manager, but the major idea would probably be to use “2 digits semantic versionning”, like “1.1” or “2.0”:

1.   MAJOR version when you make incompatible API changes,

2.   MINOR version when you add functionality in a backwards-compatible manner, and

3.   : not needed because internal changes do not appear in API

Authentication
Customer Authentication
Target: Use Open ID Connect with BIL SSO

Transition: Use BIlnet “SSO Light”

Employee Authentication
Target: Employee SSO

Transition: Use LDAP authentication directly. In the context of BLSNet, use BLSNet's SSO.

Internal Systems Authentication
Still to be decided: Use Mutual authentication., or API Keys, or technical JWT.

Swagger Documentation Recommendation for successfull API Registration
Document the contact detail as follow :

"info": {
    "contact": {
        "email": "mvp_project_xccx@bil.com", 
        "name": "XCCX", 
        "url": "http://wiki-it/display/MVPFCCE/MVP+X-Channel+Customer+eXperience"
    }, 
    "description": "Cash accounts & transactions", 
    "license": {}, 
    "termsOfService": "www.bil.com", 
    "title": "Cash account", 
    "version": "1.0"
},
Do and Don't
Are recommended :

·         Adding examples for your models

·         Limit operations to GET, PUT, POST, DELETE (e.g. avoid PATCH or OPTION)

·         Use technical ID(s) (e.g. java UUID) for your ressources identifiers instead of Logical ID(s) (e.g. IBAN / PAN).

·         Remove Technical API(s) from your swaggers such as actuators, ping, etc

·         Meaningfull domain names for your api (e.g. cards-ms VS guepe)

Are considered as bad practices :

·         Exposing Language specific objects (e.g java stack traces, List<>, DTOs)

·         …

Bibliography / Sources
·         10 Best Practices for Better RESTful API : https://blog.mwaysolutions.com/2014/06/05/10-best-practices-for-better-restful-api/

·         Design a REST API (Octo): https://blog.octo.com/en/design-a-rest-api/

·         Tolerant Reader (Martin Fowler): https://martinfowler.com/bliki/TolerantReader.html

·         REST: Good practices for API Design: https://medium.com/hashmapinc/rest-good-practices-for-api-design-881439796dc9

·         BIAN https://bian.org/servicelandscape-5-0/

·        
Use generics when possible

·         Develop to an interface, not an implementation

·         Use delegation over inheritance

·         Use final

·         Use the latest Date and Time API (JSR 310)

o    Both the Date and Calendar classes are not thread safe

o    New API comes with a consistent model for dates, times, durations and periods

o    New API makes it easier and safer to work with time zones.

o    Use Joda Time if you have no other choice

·         Learn some functional programming

o    Use immutability

o    Use the Stream API

o    Use lambdas, extract complex lambdas into named functions

o    Return Optional or any equivalent if needed (vavr Option)

o    Consider using vavr for any usage

·         Avoid null

o    Return empty collections instead of null

o    Do not take null inputs

