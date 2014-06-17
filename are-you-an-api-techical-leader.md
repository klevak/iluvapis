
# Application Programming Interface Technical Leadership Survey - a.k.a APIGeek

Are you are a technical leader or API evangelist looking to make a huge impact?  

If so, we know how much of a rare breed you are and are delighted that you've been sent to this repo.  

The purpose of this markdown file is to gauge the affinity between your API geek experience 
and our API program. Basically, if we turn out to be speaking the same language you might be a good fit
and we should talk more.

Here is our idea of someone who be the ideal APIGeek

## APIGeek required experiences :

- Solid experience with RESTful service design and development
  
  "Solid" means you've spent at least a decade either "designing" and "coding" apis 
  between multiple complex systems.  Naturally, during this journey you surely would have spent 
  years of your life in *writing* and *reading* API specifications.  
  
  If this is the case I'd expect a near expert level knowledge of the folliwng of one, preferably more
  of the following:
  
  API Blueprint - http://apiblueprint.org/
  Swagger - https://helloreverb.com/developers/swagger
  RAML - http://raml.org/
  WADL - https://wadl.java.net/

  
  Designing APIs requires authoring one or more of these specifications by hand.  So yo should have a 
  good command of the syntax.  In addtion, you've used and written tools to integrate the processing
  of these SPECs into your development workflow.
  
  "Solid" means your API designs have been implemented by a team of rock star developers at a rapid pace.
  
  API Developers are a very rare compostion of precision and pragmatism.  Technical leading a crew of 
  talented API Developers takes a true [Protagonist](http://en.wikipedia.org/wiki/Protagonist).


- Solid experience with Javascript, specifically Node.js.
- Solid experience with web technology -- specifically request/response protocols/payloads.
- Solid experience developing JSON and XML schemas.
- Experience using SoapUI, JUnit, and JMeter for testing.
- Experience working in a fast-paced, Agile (Scrum) development environment.

# Preferred but not required:
- API gateway experience (Apigee preferred, Mashery, Layer7, IBM CastIron acceptable).
- Experience with Continuous Integration tools preferably Jenkins.
- Experience with Source Code Management preferably Git.
- Experience with Configuration Management preferably Maven.
- Scrum master experience.
- Ecommerce industry experience.

# Key responsibilities include:
API specification development -- payload/interface design, error/exception handling, security, performance, research existing back-end services.

API user story elaboration, task definition, categorization, assignment, estimation and scheduling.
Act as team development lead including monitoring, supervision, code review, training, problem resolution.

Work with QA team members, API product owner(s), and security analysts.
Review and contribute to API and development process documentation. 
Research/assign/resolve production and development defects.



# API Technical Leader Interview Questions

# Topic 1. :  Solid experience with RESTful service design and development is required for this position.  This demands a strong grasp of API terminology and nomenclature.  

API Lingo - source apiglossary.com
Please define the following Terms:

## Question 1: Header
> A header is what's sent before the body of an HTTP request or response.


## Question 2: HATEOAS
> Hypermedia as the Engine of Application State is feature of the REST architecture allowing the client to navigate through hypermedia exposed by the API.

## Question 3: OAuth
> Open standard authorization framework. Grants access on behalf of an end-user without directly sharing credentials.

## Question 4: Rate-Limiting
> Limiting the consumption of an API to a certain number of requests per period of time.

## Question 5: Resource
> A resource is some object or entitity that has a URI where it can be manuiplulated through HTTP requests.

## Question 6: Status Code
> HTTP status codes are what the server sends back to the client with the response in regards to the status of the request.

## Question 6 (Bonus): Define 200, 201, 302, 400, 401  

> 200 OK The request has succeeded.

> 201 Created - The request has been fulfilled and resulted in a new resource being created.

> 302 Found - The requested resource resides temporarily under a different URI.

> 400 Bad Request - The request could not be understood by the server due to malformed syntax. The client SHOULD NOT repeat the request without modifications.

> 401 Unauthorized - The request requires user authentication.

## Question 7: Media Type
> Identifier used to indicate the type of data that a file contains.


# Topic 2. : APRESTful service design expertise
The L.L.Bean API Teams primary responsibility is to provide consistent information resource to it’s consumer apps.  This requires APIs originally designed by various team must be represented is a cohesive, consumable and developer friendly manner.  

Common tooling we use for describing API’s include:
- API Blueprint: http://apiblueprint.org/
- Swagger https://github.com/wordnik/swagger-spec
- RAML http://raml.org/
- WADL http://www.w3.org/Submission/wadl/


Your command of these RESTful service design specifications is critical in order to technical lead the API program.  The following questions where devised in order to gauge your experience and attention to detal. 

API Blueprint Questions

## Question 8 (API Blueprint).  Please provide the api blueprint markdown syntax for an a "hello world" API using the content type text/plain.


```
# GET /message
+ Response 200 (text/plain)
      
      Hello World!
```


## Question 8 (RAML).  Please provide the RAML syntax for an a "hello world" API using the content type application/json.


```
#%RAML 0.8
 
title: Hello World API
baseUri: http://api.llbean.com/{version}
version: v1
/message:
   description: Retrieve a specific book title
     get:
      responses:
        200:
           body:
             application/json:
              example: |
                 {
                   "hello": "world"
                 }
```

## Question 8 (Swagger).  Please provide the Swagger JSON for an a "hello world" API using the content type application/json.


```
{
  "apiVersion": "1.0",
  "swaggerVersion": "1.2",
  "basePath": "http://api.llbean.com",
  "resourcePath": "/v1",
  "produces": [
    "application/json"
  ],
  "apis": [
    {
      "path": "/message",
      "operations": [
        {
          "method": "GET",
          "summary": "Get Messages",
          "responseMessages": [
            {
              "code": 200,
              "message": "No Messages"
            }
          ]
        }
      ]
    }
  ]
}
```



## Question 9.  Please prodive the bluprint of the same api to provide JSON response for an 500 error

```

+ Response 500
Response returned if the update operation was not successful. It specifies that update for the specific login preference has failed.

    + Headers

            Content-Type: application/json
   
    + Body
    
            {
                "fault": {
                    "faultstring": "Internal server error",
                    "detail": {
                        "errorcode": "500"
                    }
                }
            }

```




## Topic 3. The techical lead for the API Program must perform many code reviews to ensure quality and security across api design and development.  Please review the following api specification and and answer questions below.


```

FORMAT: 1A
HOST: https://api.llbean.com

# LLBean My Account API

## Summary
The L.L.Bean My Account API allows developers to manage resources directly associated to a user account. It first requires authentication with login resource to establish a cookie-based session, which then enables subsequent calls to access resources such as change of the secret question, password, payment methods (coupons, credit cards, etc.), and email preferences. 


# Group My Account Login Resources

## Login [/v1/account/login]
Authenticates a user given a login id and password, the response will grant access to other protected resources, returning a cookie-based session that can be leveraged from subsequent calls.

+ Model

    + Headers

            key: yourconsumerkey==

    + Body

            {
                "login_id" : "joesmith@address.com",
                "password": "puppies&ponies"
            }

    + Schema

            {
              "type": "object",
              "required": ["login_id","password"]
              "properties": {
                "login_id": {
                  "type": "string",
                  "required": true
                },
                "password": {
                  "type": "string",
                  "required": true
                }
              }
            }

### Login [POST]
Establishes a session to access my account resources.

+ Request

    [Login][]

+ Response 200

    + Headers

            Content-Type: application/json

    + Body

            {
                "class": "user-authentication",
                "properties": {
                    "customer_id": "00644422566"
                },
                "actions": [],
                "links": [
                    {
                        "rel": [
                            "self"
                        ],
                        "href": "https://api.llbean.com_TODO/v1/account/login"
                    }
                ]
            }

    + Schema

        {
              "type": "object",
              "required": true
        }

+ Response 401

    + Headers

            Content-Type: application/json

    + Body

            {
                "fault": {
                    "detail": {
                        "errorcode": "401",
                        "href": "https://developer.llbean.com/errors/LLB-0401",
                        "message": "The password you entered is incorrect. Please note that passwords are case sensitive."
                    },
                }
            }

    + Schema

            {
              "type": "object",
              "required": [
                "fault"
              ],
              "properties": {
                "fault": {
                  "type": "object",
                  "required": [
                    "faultstring",
                    "detail"
                  ],
                  "properties": {
                    "faultstring": {
                      "type": "string"
                    },
                    "detail": {
                      "type": "object",
                      "required": [
                        "errorcode"
                      ],
                      "properties": {
                        "errorcode": {
                          "type": "string"
                        }
                      }
                    }
                  }
                }
              }
            }

+ Response 403 (application/json)
Method Not Found

    + Body

            {
              "fault":  {
                "faultstring": "Method not found. Only POST method allowed.",
                "detail":  {
                  "message": "Method not found.",
                  "href": "http://developer.llbean.com/api-errors#my-account-api-403-method-not-found",
                  "errorcode": "403"
                }
              }
            }

    + Schema

            {
              "type": "object",
              "required": [
                "fault"
              ],
              "properties": {
                "fault": {
                  "type": "object",
                  "required": [
                    "faultstring",
                    "detail"
                  ],
                  "properties": {
                    "faultstring": {
                      "type": "string"
                    },
                    "detail": {
                      "type": "object",
                      "required": [
                        "errorcode"
                      ],
                      "properties": {
                        "errorcode": {
                          "type": "string"
                        }
                      }
                    }
                  }
                }
              }
            }

+ Response 500 (application/json)
Internal Server Error

    + Body

            {
              "fault":  {
                "faultstring": "Internal Server Error Occurred",
                "detail":  {
                  "href":"http://developer.llbean.com/api-errors#my-account-api-500-error",
                  "errorcode": "500"
                }
              }
            }

     + Schema

            {
              "type": "object",
              "required": [
                "fault"
              ],
              "properties": {
                "fault": {
                  "type": "object",
                  "required": [
                    "faultstring",
                    "detail"
                  ],
                  "properties": {
                    "faultstring": {
                      "type": "string"
                    },
                    "detail": {
                      "type": "object",
                      "required": [
                        "errorcode","href"
                      ],
                      "properties": {
                        "errorcode": {
                          "type": "string"
                        }
                      }
                    }
                  }
                }
              }
            }
            
```


## Question 11.  Using your curl, please make a request to the described API that would result in a 200 response code.


```
curl --request POST \
     --header "key: yourconsumerkey==" \
     --data-binary '{
    	"login_id" : "joesmith@address.com",
    	"password": "puppies&ponies"
	}' \
    https://apitechlead.apiary-mock.com/v1/account/login
```

## Question 12. If the described API response with a 401 what would the response be?

```
{
    "fault": {
        "detail": {
            "errorcode": "401",
            "href": "https://developer.llbean.com/errors/LLB-0401",
            "message": "The password you entered is incorrect. Please note that passwords are case sensitive."
        },
    }
}
```


## Question 13. If the following response was validation according the to JSON Schema provded what sort of issues would be found.

> Answer - "fault.detail.errorcode" "instance type (integer) does not match any allowed primitive type (allowed: ["string"])
> Answer - "fault.detail.href" is object has missing required properties ([\"href\"])
> Answer - faultstring" is missing a preceding double quote 
> Answer - instance type (array) does not match any allowed primitive type (allowed: [\"object\"])
> Answer Bouns - Invalid JSON.  Faultstring is missing a quote.


```
{
  "fault": [
    {
      faultstring": "Internal Server Error Occurred",
      "detail": {
        "errorcode": "500",
        "href": "test"
      }
    }
  ]
}
```

# Topic 4: Solid experience with Javascript, specifically Node.js.
Technically leading the API program team towards sucess building API facades requires a solid command of JavaScript spe a good foundational understanding of the event driven programming paradigm used with Node.js.  The following are some common questions to gauge your experience with Node.js 

## Question 14. What is the command that is used in node.js to import external libraries?

> Command “require” is used for importing external libraries, for example, “var http=require (“http”)”.  This will load the http library and the single exported object through the http variable.


## Question 15. What is ‘Callback’ in node.js?

> Callback function is used in node.js to deal with multiple requests made to the server. Like if you have a large file which is going to take a long time for a server to read and if you don’t want a server to get engage in reading that large file while dealing with other requests, call back function is used. Call back function allows the server to deal with pending request first and call a function when it is finished.

## Question 16. What is the advantage of using node.js?

> It provides an easy way to build scalable network programs
> Generally fast
> Great concurrency
> Asynchronous everything
> Almost never blocks

## Question 17. Who is Ryan Dahl?
> Ryan Dahl is the creator of Node.js

## Question 18: Why do you think node.js is quickly gaining attention from JAVA programmers?

> Node.js is quickly gaining attention as it is a loop based server for JavaScript. Node.js gives user the ability to write the JavaScript on the server, which has access to things like HTTP stack, file I/O, TCP and databases.







Interview Questions
You have been tasked with providing a mobile interface to a business application. You have many options available to do so. Please describe a guidance framework you may use decide between these options.

Please describe a framework broken into four related parts:

- How would you select an approach?
- Describe mobile consumer app models (a.k.a clients) you would want to support?
- Provide some proposed approaches to integrating mobile clients to back end?
- What would be your considerations for selecting infrastructure?

What’s import to understand our requirements and constraints:

- Requirements may impact decisions.  No one solution fits all business and technical requirements.
Business factors 


Prework: Understand your requirements and constraints:
Requirements impact decisions: No one solution fits all requirements.
Business factors: Budget, timing, audience, scope and marketing.
Technology factors: Back-end architecture, integration, offline, endpoint independence, synchronization, security, scalability, deployment and user experience.

Part 1 - How would you select an approach?



TODO:

  Add Agile / Scrum questions
  Add JIRA / Confluence Questions
  Add Git / SCM Model questions
