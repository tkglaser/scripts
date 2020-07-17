# Ep 1: Fast Change - How architecting a web application has changed in the last 10 years

## Abstract

This is the first episode of thomas' and Nosqlgeek's tech podcast. We are starting with a light-weighted (or not?) topic by trying to find an answer to the question 'How did architecting a web application change in the last 10 years?'.

## Info

|Detail|Value|
|---|---|
|Episode|1|
|Name|Fast Change|
|Sub-title|How architecting a web application has changed in the last 10 years|
|Speaker|Thomas|
|Moderator|David a.k.a NoSQLGeek|
|Planned duration|1h|

## Script

|Section|Sub-section|Notes|Speaker|Duration|
|---|---|---|---|---|
|Intro|Intro Topic|Explain the today's topic; David starts and Thomas kicks in|David + Thomas|1m|
||Question|Thomas, glad to have the chance to record this episode with you. Please tell us a bit about you!|David|30s|
||Intro Thomas|Hi I am Freelance Full Stack Engineer and Architect. I have worked for companies like Symantec, Actian and McLaren to name just a few. So I have been writing Software since 2004 and I specialised on web technologies since 2011, primarily focused on the Microsoft Stack and Angular. In my spare time I enjoy reading, walking and travelling.|Thomas|2m|
||Intro David|Thanks Thomas! My name is David (a.k.a NoSQLGeek) and I worked in several roles, including the ones as Software Engineer, Software Architect, Consultant, Solutions Architect and in Technical Enablement. Besides of the fact that I have a small company that's called NoSQLGeeks, the name was chosen because I worked with a bunch of modern database companies (e.g., Ingres -> Actian [RDBMS + Columnar], Sones [GraphDB], Couchbase [DocumentDB], Redis Labs [KV/Data Structure Store]). I am working currently very closely with Redis Labs, where I am responsible for several technical education programs. So I love Redis and I will indeed also use this Podcast to express my love from time to time. However, I would call myself a developer by heart (So I developed for instance migration tools, a storage engines, demo applications, ECM-based archieve solutions, knowledge base solutions), but Thomas is having much more hands-on experience with full-stack development.|David|2m|
|Example Application|Let's get started|So let's get started. Why don't we start with an application example? Any idea what could be discussed?|David|30s|
||Requirements ToDo App|Tasks can be created/deleted/ticked off; Accessible via the web; Login needed (aut); Non-functional: minimum hosting costs, fully secure, good performance, no scaling limits (up to millions of users)|Thomas|1m|
|Past Architecture|Question|So how would you have architected such an application in the pre-Cloud era?|David|30s|
||Answer|SQL-database; Server-side code like ASP/MVC; Login: Hashed password / ASP Identity; Scaling: Monolithic approach, so need to scale almost the entire stack together; (Assess against PASS ME perf/avail/sec/scal/maint/exten)|Thomas|7m|
||Comment|I see, we have to repeat that you are more a .NET guy. I used to develop more Java code. There we would have used e.g., Java Server Pages or MVC frameworks like Struts (just in case that you don't know what ASP is.|David|1m|
|Today's Architecture|Question|So how did it change? How does it look like today and why where specific decisions made?|David|30s|
||Answer|This is a good case for an SPA, for example Angular; If you build a SPA, you need an API, we'll come to that; Use an external IDP like Azure Active Directory B2C and OpenID Connect; Database: Use NoSql like DynamoDB, CosmosDB or Redis; Typically the SPA will access the NoSql cluster DIRECTLY using a resource token (explain); This means all the API needs to do is the token exchange|Thomas|10m|
||Comment|Let me talk a bit about NoSQL in this context. You already mentied some services as kind of given. I think that it comes finally down to a microservices architecture (e.g. seeing the identity mangement as a service). Your application might leverage multiple of such services and services might even communicate with each other behind the scenes. This could be abstracted away by from the application by using an API gateway. But back to the database. We learned that monolithic applications often used a single RDBMS. If we talk about a microservices architecture (which is a bit out of scope of our original example), then we also need to talk about polyglot persistence. Different services might have different sets of requirements. Some services might need to be very transactional and so they might stick with an RDBMS, but other services have scalability as their dominant requirement. Such a service should then use a NoSQL database system which scales very well. This 'the service uses the DBS which fits best' is called 'Polyglot persistence'. It allows you to scale the persistence layer independently from other services (with less agressive scalability requirements). BTW: Not all NoSQL systems scale equally well, because they are built for specific purposes. A KV-store scales best because of the simplicity of the underlying data model (primary-key access and the hash-based sharding). You mentioned CosmosDB. CosmosDB is a so-called multi-model database system because it has multiple ways to present the data (Graph, Wide-colum, Document and so on). I am not a CosmosDB expert, but Redis can be also interpreted as such a multi-model DBS. It's first a KV-Store, which you can use for session stores or just caching. It has much more to offer because it's in the next step a data strucutre store. It's very developer-friendly. Data-structures basically provide the same structures that are used by developers (lists, sets, dicts) on side of the DBS. In addition, you can extend it with modules to turn it into a native GraphDB, TimeSeries DB, FTS Engine and more. But enough about Redis ... Just thought that it might make sense to talk about the DB aspect of modern applications :-D.|David|7m|
|Azure|Question|So Thomas, I know you are a Microsoft fan boy ;-) . How would our example application be implemented on Azure?|David|30s|
||Answer|Host the SPA directly out of Azure Storage; Connect Azure CDN for speed and HTTPS;Use Azure Active Directory B2C (other IDPs are available); Use CosmosDB for data storage;Use Azure API Management (proxy) to offload authentication; Use Azure App Service to host the API (could use Azure Functions); Secure using a certificate, or (cheaper) basic Authentication with a long secret;Use Azure Key Vault to store secrets|Thomas|3m|
||Comment|Just a side note: Similar services are also available on AWS or GCP. We just talked more about Azure because Thomas has more experience with this Cloud|David|30s|
||Question|If someone wants to start creating this app now, which costs should be expected?|David|30s|
||Answer for Dev|Free tiers for CosmosDB, App Service, API Management, AD B2C (some have the first N interactions free);£0.77 per month|Thomas|2m|
||Answer for Prod|Prod with 100,000 active users: No more free tiers because we want SLAs; £367.07 per month; This means you need to earn roughly £0.004 per user to cover the hosting costs|Thomas|5m|
||Follow-up question|Man, those are quite concrete numbers. Do you actually host such an app or how did you calculate them?|David|30s|
||Answer|I have a similar app; A calorie counter that works with the same principle; If I find time and there is interest, I'd like to build this ToDo app out end to end and record tutorials on how to do it. What I have used to get to these numbers is the Azure Calculator with some assumptions (don't guess your traffic). The Calorie App is only used by me and costs me about £0.01 per month|Thomas|2m|
||Question|What is next for you?|David|30s|
||Answer| Recently got certified as Azure Architect; Now working on AWS Certification; Took some time off with the corona thing, now looking to get back into consulting. |Thomas|2m|
||Question| How about you, what's next for you?|Thomas|30s|
||Answer| David to answer |David|2min|
|||||**52m**|
