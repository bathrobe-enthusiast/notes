---
title: "REST"
date: 2020-05-21T17:43:33+08:00
categories: ["internet"]
tags: ["REST"]
draft: false
---

Representational State Transfer (REST) style is an abstraction of the architectural elements within a distributed hypermedia system. REST: a set of design constraints - first identified in Roy Fielding's 2000 dissertation on software architecture.
- client-server
- statelessness
- caching
- layering
- uniform interface

- hypermedia as the engine of application state

### Client-server
Separation of UI concerns from data storage concerns improves portability of UI across multiple platforms and improves scalability by simplifying server components. Most importantly, this separation allows components to evolve independently and thus support Internet-scale requirements of multiple organization domains.

### Statelessness
Each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server. Session state is therefore kept entirely on the client.

Hence:
- Visibility: single request carries its own context
- Reliability: recovering from partial failures is easier
- Scalability: not having to store state between requests frees up resources; not having to manage resource usage across requests simplifies implementation

Tradeoff:
- Increase in repetitive data -> decrease in network performance

### Caching
Resources can declare themselves cacheable or not; performance improves.

### Layering
So a client cannot ordinarily tell whether it is connected directly to the end server, or to an intermediary along the way. Shared caching within a layered system may offset reduction in performance.

### Uniform Interface
The central feature that distinguishes the REST architectural style from other network-based styles!

Uniform Interface <-> Metadata encapsulating shared understanding of data types between client and server

A distributed hypermedia architect has only three fundamental options: 1) render the data where it is located and send a fixed-format image to the recipient; 2) encapsulate the data with a rendering engine and send both to the recipient; or, 3) send the raw data to the recipient along with metadata that describes the data type, so that the recipient can choose their own rendering engine.

1) Information about true nature of data remains hidden in server -> client implementation easier BUT limited, and scalability problems as most of the processing load is on the sender
2) Provides information hiding while enabling specialized processing of the data via its unique rendering engine, but limits the functionality of the recipient to what is anticipated within that engine and may vastly increase the amount of data transferred.
3) Allows the sender to remain simple and scalable while minimizing the bytes transferred, but loses the advantages of information hiding and requires that both sender and recipient understand the same data types.


> REST provides a hybrid of all three options by focusing on a shared understanding of data types with metadata, but limiting the scope of what is revealed to a standardized interface. REST components communicate by transferring a representation of a resource in a format matching one of an evolving set of standard data types, selected dynamically based on the capabilities or desires of the recipient and the nature of the resource. Whether the representation is in the same format as the raw source, or is derived from the source, remains hidden behind the interface. 

Anyway, efficient for large-grain hypermedia data transfer, which is the common use case of the Web.

---

3 technologies make this possible: URI, HTTP, HTML.

### URI: Universal Resource Identifier

Resource:
- Key *abstraction* of information in REST
- Any *concept* that might be the target of a hypertext reference must fit within the definition of a resource i.e. a resource is...
- A conceptual mapping to a set of entities, NOT the entity that corresponds to the mapping at any point in time.

A resource *R* is a temporally varying membership function *M*r(*t*), which for time *t* maps to a set of entities, or values, which are equivalent. The values in the set are called *resource representations* or *resource identifiers*.

A resource can map to the empty set, which allows (hypertext) references to be made to a concept before any realization of that concept exists.

> This abstract definition of a resource enables key features of the Web architecture. First, it provides generality by encompassing many sources of information without artificially distinguishing them by type or implementation. Second, it allows late binding of the reference to a representation, enabling content negotiation to take place based on characteristics of the request. Finally, it allows an author to reference the concept rather than some singular representation of that concept, thus removing the need to change all existing links whenever the representation changes (assuming the author used the right identifier).

### HTTP: Hypertext Transfer Protocol
...works on HTTP message entities, a specific instance of a *representation*.

Representation: captures the current/intended state of that resource, and comprises:
- data
- metadata describing the data
- METADATA describing the METADATA - usually for verifying message integrity

**HTTP: a standard describing the actions a client can take on a resource.**  
The client has no direct control over resource state on the server, but is able to manipulate it by sending HTTP requests to URLs identifying a resouce - this HTTP request can include a representation eg. in a POST request, and the server can sends back a representation as well of the resource (State).

### HTML: Hypertext Markup Language
...writes *hypermedia*, which informs clients about the kind of HTTP requests they're allowed to make.

Hypermedia: media defined by the presence of application control information embedded within, or as a layer above, the presentation of information.

Hypermedia controls have three jobs:
- They tell the client how to construct an HTTP request: what HTTP method to use, what URL to use, what HTTP headers and/or entity-body to send.
- They make promises about the HTTP response, suggesting the status code, the HTTP headers, and/or the data the server is likely to send in response to a request.
- They suggest how the client should integrate the response into its workflow;  describe the relationships between resources. 

**Hypermedia is the engine of application state**  
i.e. we all navigate the Web by filling out links. Application state: which web page the client is on; hypermedia: the method a server uses to explain to a client what it can do next. State transitions on both client and server are effectede by hypermedia links.

---
**References**
Fielding, Roy Thomas. *Architectural Styles and the Design of Network-based Software Architecture*. Doctoral dissertation, University of California, Irvine, 2000.
