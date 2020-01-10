## Step by step for workshop 02

```
npm i compression express express-range mongodb uuid --save
```

```
mongoimport --file zips.json --host localhost -d cities -c cities --drop
```

## Worksheet 2

1. 

* Allows for separation of concerns

If we try to put everything together to work as a whole, without splitting into modular is impossible to port the things we do to another domain.

* Stateless

As per the REST architecture, a RESTful Web Service should not keep a client state on the server. This restriction is called Statelessness. It is the responsibility of the client to pass its context to the server and then the server can store this context to process the client's further request.

* Cache

Caching is the ability to store copies of frequently accessed data in several places along the request-response path. When a consumer requests a resource representation, the request goes through a cache or a series of caches (local cache, proxy cache, or reverse proxy) toward the service hosting the resource. If any of the caches along the request path has a fresh copy of the requested representation, it uses that copy to satisfy the request. If none of the caches can satisfy the request, the request travels all the way to the service (or origin server as it is formally known).


* Uniform Interface 

The central feature that distinguishes the REST architectural style from other network-based styles is its emphasis on a uniform interface between components (Figure 5-6). By applying the software engineering principle of generality to the component interface, the overall system architecture is simplified and the visibility of interactions is improved.

* Layered System

REST allows you to use a layered system architecture where you deploy the APIs on server A, and store data on server B and authenticate requests in Server C, for example. A client cannot ordinarily tell whether it is connected directly to the end server, or to an intermediary along the way.


2. a. /api/customers

   b.  

```
[{
    first_name: "Kenneth",
    last_name: "Phang",
    email_address: "a@a.com"
    ....
},
{
    first_name: "Kenneth",
    last_name: "Lim",
    email_address: "a@a.com"
    ...
}]
```

c. /api/customers?city=Singapore&job_title=Accountant

d. Its an READ operation. You can use POST to do this. The HTTP spec does not prohibit it. By using GET you are more accurately representing the characteristics of the request. If you use POST, an intermediary cannot tell that you are performing a safe, idempotent request, even though you are. That may limit the benefits you get from certain intermediaries. You will not be able to take advantage of a cached response by using POST.

e. Pagination and range filter.

3. My solution will be as follows:-

We defined the following three endpoints:

* GET /api/videos - this endpoint fetches all the videos available
* GET /api/video/:id - this endpoint will receive the details of a single video. It will be called when the video is ready to be displayed.
* POST /api/save-video/:assemblyId - this endpoint saves our videos during encoding. Here, it might seem like magic is happening, so allow me to give you a breakdown:

Tracking of usage and subscription will be on the save video endpoint. (/api/save-video/:assemblyId)