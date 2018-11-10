---
layout: post
title: GraphQL Fundamentals
subtitle: First day on GraphQL
tags: [GraphQL, programming]
---

## So first, what is GraphQl? (for some novices like me)

 - A new API that was developed by **Facebook**
 - Allows **declarative data fetching** (where a client can specify excatly what data it needs from an API)
 - GraphQL server exposes single endpoint and responds with a specific data that a client asked for



## How GraphQL becomes an alternative way to REST
 - Stateless servers and structured access to resources
 - REST is inflexible to keep up with the rapidly changing requirements on the clients that access them

## For example in REST API:

The client sends a GET request to the server, in some conditions we only need the user id, but the server responds a lot of non-use data.

~~~
{
	"user": {
		"id" : "er4ggf2ht6"
		"name" : "John"
		"address" : "..."
		"dob" : "1992 May 2"
	}
}
~~~

## However, GraphQL can easily solves this problem:

In GraphQL on the other hand, you’d simply send a single query to the GraphQL server that includes the concrete data requirements. 
The server then responds with a JSON object where these requirements are fulfilled.

~~~
query{
	User(id: "er4ggf2ht6") {
		name
	}
}
~~~

## The Schema Definition Language (SDL)

GraphQL has its own type system that’s used to define the schema of an API. The syntax for writing schemas is called Schema Definition Language (SDL).

 - Here is an example how we can use the SDL to define a simple type called Person:

~~~
type Person {
  name: String!
  age: Int!
}
~~~

 - An example query that a client could send to a server:

~~~
{
  allPersons {
    name
  }
}
~~~

The allPersons field in this query is called the root field of the query. Everything that follows the root field, is called the payload of the query. 
The only field that’s specified in this query’s payload is name.

 - The return results:

~~~
{
  "allPersons": [
    { "name": "Johnny" },
    { "name": "Sarah" },
    { "name": "Alice" }
  ]
}
~~~


## GraphQL Advantages


**No Overfetching with GraphQL**

GraphQL minimizes the data needs to be transferred over the network -> more efficient in data loading

**GraphQL for React, Angular, Node and Co.**

GraphQL can be used with any **programming languages**. For example: React, Angular, Node and Co.

**Provides various fronted frameworks and platforms on the client side.**


**Ecosystems of GraphQL**

There are not only integrations for the strongly typed nature of GraphQL for editors and IDEs, but also standalone applications for GraphQL itself.

What you may remember as Postman for REST APIs is now GraphiQL or GraphQL Playground for GraphQL APIs.



## GraphQL Disadvantages


**GraphQL Rate Limiting**

Whereas in REST it is simpler to say “we allow only so many resource requests in one day”, it becomes difficult to make such a statement for individual GraphQL operations, because it can be everything between a cheap or expensive operation.

That’s where companies with public GraphQL APIs come up with their specific rate limiting calculations which often boil down to the previously mentioned maximum query depths and query complexity weighting.


**GraphQL Caching**

Implementing a simplified cache with GraphQL is more complex than implementing it in REST. 

In REST, resources are accessed with URLs, so you can cache on a resource level because you have the resource URL as identifier. 

In GraphQL, this becomes complex because each query can be different, even though it operates on the same entity. You may only request just the name of an author in one query, but want to know the email address in the next. 

That’s where you need a more fine-grained cache at field level, which can be difficult to implement. However, most of the libraries built on top of GraphQL offer caching mechanisms out of the box.


## Resources from:
 - https://www.howtographql.com/basics/0-introduction/
 - https://www.howtographql.com/basics/1-graphql-is-the-better-rest/
 - https://www.howtographql.com/basics/2-core-concepts/
 - https://www.howtographql.com/basics/3-big-picture/
 - https://www.robinwieruch.de/why-graphql-advantages-disadvantages-alternatives/

