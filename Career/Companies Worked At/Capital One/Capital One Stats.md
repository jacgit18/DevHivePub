---
tags:
  - career
  - employment
  - CapitalOne
  - favorite
author:
  - jacgit18
Purpose: This documentation discusses work done at current company.
Status: Perpetual
Started: 2023-12-14
EditDate: 
Relates: 
dg-publish:
---
## Experience
#todo/BAU/Career/Doc
- [ ] Revisit [Credit Card Data and Stock trading use case analysis](https://chatgpt.com/share/680a5be4-9274-800d-858f-0847742b1e90)
- [ ] [Merger Buisness Cases Study](https://chatgpt.com/share/680bea65-c684-800d-b17b-900161bd4eb8)




“I’m working on ensuring our collections automation can scale with new compliance rules and customer workflows.”

I’ve worked across different team models. As a **QA Engineer**, I worked on a product team supporting an internal credit card servicing application, where I focused on expanding front-end test coverage. Later, I joined a collections-focused team where I built AWS Step Function workflows defining key parts of the offer enrollment process, coordinating across multiple upstream and downstream services.


The QA role supported a specific product team, while the collections work was part of a team owning a defined slice of the business workflow.



“I’ve been on both the software and governance sides of fintech—building automation at Capital One, upskilling engineers at TD, and working hands-on in full-stack at a fintech startup.”

“I’ve worked across fintech—from credit card servicing and collections at Capital One to governance at TD Bank and full-stack development at a construction fintech startup. Each role has given me a different perspective on how software drives business impact.”


“At Capital One, I’m working on the intersection of architecture, automation, and regulatory complexity—essentially, making sure our systems scale with new compliance and business rules post-merger.”






## work convo 

Showing up in a meeting say that you know you're interrupting but and continue with your point  
  
Detach like one critiquing something like oh this resume needs a little bit of clarity in this area instead of mentioning the word you in your criticism  
  
Im curious if you were me what would you do reframe things when asking for people's opinions

Don't have virtual backgrounds have stuff in the background that bring up conversation during Zoom



“I work on **automating the collections process**—essentially making sure the system knows when and how to reach out to customers, what options they have, and how we scale that across millions of accounts.”

“I work on business automation for collections, where we design systems that scale across millions of accounts while staying compliant with financial regulations.”


“The work I do ensures that collections are handled efficiently and fairly, using automation to reduce errors, personalize outreach, and optimize recovery processes.”






## Current 
Worked under Card tech for both teams at capital one. The first being in QA for PainKillers under **Empath** platform which deals with customer relations using streams in terms of data sources collection.  
  
**Stream** data sources encapsulates platforms and systems that produce data or change oriented events of interest to collections business processes. Stream data is exclusively published And subscribed to use the OneStream platform  

Now on Real-time intelligence Collection(RTIC) surge team who align with SOC - System and organization controls.

This team focus on [[Credit Card Collections]], delinquency, and stuff like payment plans. The focus of the work will center around maintaining and up-scaling process and services for capital one and future discovery customers as part of the Capital One Discovery merger.

We're building Arctic offers out for the next 6 month i may be working with AWS while   

Cloud orchestration processes from Scheduled hook Rtic to step functions

Arctic uses DynamoDB and utilizes AWS server-less architecture focusing on things like lambda and Step-Up which is no code.

Credit card collection the main mission is to help customers who are off track get back on track of their payments the way this happens is through offers or specifically rtic offers  
  
this includes payment plans maybe reducing apy or other different plans etc..  

Might be enhancing dialing through offers
  
Splunk  
  
Talk about learning about splunk and some best practice and managing technical debt

Ease and empath are clients and offers enrollment LLD  
  
  
  
Decisioning act as a recommendation agent to ensure proper treatment and surface at any given time

Arctic decisioning generates contract  
  
  
Were focus on enrollment


Alot of the work centered around contract related stuff


ASV application service version  
  
  
Rules lab is basically a internal tool that is used by business analyst to update credit policy without having to have software engineers mess around with codebases to do this just in terms of Simple Rules that you see on a website specifically for a credit card terms and policies and many other things around credit cards

Get people out of credit card delinquency and catch Bad actors

Currently working on the customer resume Department  
  
  
Before I was under contact center enablement Department

5 bpa workflows

Another common use case with aws lambda is glue Logic for step function workflows  


Lambda subscribe to things like sns when it comes to asynchronous process but there are more options now Like sqs  


Fms fuffilment management service  
  
AMA auditability monitoring and Analytics

## Old


Worked on Painkiller under mojitos on a vertical team which could be mentioned if you work with more teams

Performed integration testing in a micro frontend architecture using the Vue.js testing library and internal tools, ensuring seamless front-end functionality and an optimal user experience for Capital One agents using the Empath application.  
  
Executed thorough testing across high-priority credit card types (Primary Consumer, CreditWise, Small Business) to validate complex workflows involving account managers and authorized users, ensuring accuracy across all user interactions.  
  


Conducted integration testing in a micro frontend architecture with Vue.js and internal tools for the Empath application, used by Capital One agents to resolve credit card customer cases. Performed comprehensive testing across high-priority credit card types (Primary Consumer, CreditWise, Small Business) to validate complex workflows involving account managers and authorized users, ensuring accurate and consistent user interactions and enhancing the overall user experience.


Enhanced test coverage for the "Update Citizenship" workflow across various account types, achieving a 73.51% increase in function coverage and a 14.46% increase in statement and line coverage.


## Stabilizing build


In our integration testing, we encountered timeout issues when running tests in parallel, likely due to resource contention or network latency. To address this, we switched to running the tests sequentially, which allowed us to isolate potential bottlenecks and reduce the chance of timeouts caused by concurrent processes.

We also experimented with implementing retry mechanisms, which helped mitigate intermittent failures, especially when external services were involved. Additionally, we played around with different timeout configurations, adjusting them based on the complexity and expected runtime of each test. By balancing the number of retries and fine-tuning timeout settings, we were able to stabilize the tests without excessively delaying the feedback loop.

  
  
Loe level of effort



Abstracting out LLD for better business audience understand then create other diagrams that are more for devs that goes more into technical details

  
  

Worked on test coverage initiative to increase test coverage for  Empath application an internal credit card servicing application used by capital one agents

  

Dealing with Jenkins builds

  
  

Then worked in the credit card collections for automating business Salient events that supported Offer Enrollment for customers who account were in delinquency 

  

contract adherence might not be worth mentioning 

  

Contract presentment working around prioritization and calculation 

  

Splunk querying 

  

deployed and documented process around calculation lambda deployment to localstack ephemeral environment  

  
  
  

Plans with contracts and promises to pay on the capital one specifically under the credit card payments portion

  
  Hooks process generate a bse  

Was in enrollment process around workstreams around offer enrollment  specifically ptp workflow


MVP Min Viable Product 
KT Knowledge Transfer  
LLD Low Level Design

Each repo have a section of the aws infrastructure and one deployed interact with existing infrastructure


Cloudwatch monitor DLQ  
  
  
  
DLQ is for lambda failure to eventually try again maybe in a hour or so or at least human manual intervention in terms of a retry  

## Dev tip 


Story points are important in terms of velocity and looking good
  
Document the names of future teams to better reach out to them in the future  
  
Push more frequently for aws experiments


Build something that shows you understand business and Technical side of things

Comments should be added for why something is there


Mention Just a nit pick in pr

mention TBD  in code for debug giving brief description

Documenting can cause or help with identifying flaws in logic


If you're working on something like how you were with the step functions always look for opportunities where there are people who are working on something similar or that may start out similar to copy off of their work instead of doing the effort

POC point of contact


Thats my psa on that 

elmo enough lets move on


Set MVE - Minimum viable expectations


Doc test 

  Delete colima and reinstall for broken localstack

Incremental push to main for code change

  

Working out of qa in console

  

Small pr probably go to feature branch

  
  

Tie to small specific failing test

  

Make fork up to date





This isnt a logic question its a decision question 

Long story short 

Sorry im trying to formulate my thought
  

"Then" in gurken are treated as assertion


Live dependency test no mock data


Network request can have multiple headers


idea 
How would you go about Creating a GitHub Follow the Leader script for pulling in changes from teammate on a regular basis


create script ideas to use for work and share with coworkers 



You can use yaml over json if things are too bulky and not the best in terms of readability depending on the context of what you're using that file for and if it is reasonable


LocalStack can be confusing because it sometimes treats data as a **string** when it should be **JSON**. As a result, you may need to explicitly parse the value before you can work with it as an object.

If a property isn’t accessible as expected (for example, trying to read a field on an object and getting `undefined`), it often indicates that the data is in a different format than you assume—most commonly a JSON string rather than a parsed object—and therefore needs to be parsed first.



**Only push placeholder code if it's actively helping you solve a problem or you're stuck and need to share context with teammates.**  
Avoid pushing placeholders that serve no functional purpose or are just there to "fill in space." These can clutter the codebase, cause confusion during reviews, and make the commit history harder to follow. If something is incomplete but you're working through a problem or need feedback on your approach, a clearly labeled placeholder with a meaningful comment is acceptable. Otherwise, it's better to keep local stubs or notes to yourself until the implementation is ready or necessary.


When you think you are done with implementing whatever feature Etc then raise the pr avoid raising it when you are experimenting and you have like placeholders and 100% sure on the requirements if so ask for help ask questions to get clarification then when you think it's actually what it needs to be then raise PR instead of using it for people to read your code and you to correct it accordingly without thinking

## June

7ps capital one testing platform will be doing behavior driven test


Make file that creates aws resources in local stack


Agent or customer enters empath or ease(maybe cap one mobile app) platforms which starts a process with an event through the exchange which is a internal digital asset manger and marketplace were capital one employees can publish, manage, find and use data. the exchange contains API's, streams, datasets and features that can be discovered and consumed by user. features can combine multiple datasets to produce calculated or relative datasets.

when you trigger event through the exchange you hit an API kicking off BFF Lambda. the customer account is locked then the enrollment synchronous workflow is started




## May Notes

Working under customer resiliency specifically credit card



No response from ptp  
  
Should be synchrous after payment then ptp call regardless out failure  
  
Ama(Relates to Auditing) is done doing cloudwatch  
  
  
Maybe delet payments from payment scheduler Rt which is a second call but also fulfillment can check  
  
Ptp send a response for bff weather payment is successful




Data lambda pass thru update  
  
  
Bff call payments and payments invoke ptp  
  
  
Ptp is legacy track agent metric  
  
Short term use case  
  
Will eventually phased out but agents need it  
  
  
Ptp called after payments  
  
Originally doing manual payments which ptp is apart of





  
  

  





When a agent or who ever initiate contract offer from Empath 

goes rules lab coming back with true or false 

Can only process one contract at a time which comes from a frontend through the exchange through the public API invoker getting things like contract id, contract info, and account id along with contract draft which gets sent to rules lab which determines contract eligibility if eligible we update the UCP(*Unified customer profile*) with the status to enroll and set the payments and publish to one stream for the eventual workflow and do a audit and send a response back to the client this is the immediate workflow. 

When comes to Payments still being decided were its being sent to.  

We just schedule when hooks fire


A hook is a event that is configured to fire in the future. Hooks manage the schedule invocations of business processes by capturing identification information to trigger events at specific future times  
  
  
Hooks are created when tasks are performed by business process automation when a decision is made to reevaluate the customer at a later time  
  
Hooks are deleted when tasks are performed by BPA in response to Broad exclusion where where we don't know when or if we will be able to engage with a customer in the future


One streams sends to aws and clodwatch logs are triggered for sqs repo


There is a list of actions associated with each contract which also has one offset we need to separate  those actions by the offset meaning immediate actions fired on the same day and eventual actions which are triggered by hooks based on offset date.

Data lambda => JSON => Enrollment Async Step Function

an offset is 


Does offset has to do with sending offers offers to people in delinquency depending on their level of delinquency








### Logging 

Okay — thanks for clarifying — this helps a lot.  
  
You’re saying:  
  
Your real-world goal is send CloudWatch Logs to Splunk.  
  
For now, you’re experimenting by sending CloudWatch Logs through Kinesis (Splunk will come later).  
  
You want to prove the concept — that you can stream/process logs.  
  
Important: For the final production version, you want to use Step Functions, avoid using Lambda as much as possible.  
  
  
  
---  
  
Here's the real situation you're dealing with:  
  
CloudWatch Logs → [Processing] → Splunk (eventually)  
  
You’re trying to insert Kinesis in the middle now, then later replace or add Splunk as a destination.  
  
  
---  
  
The Challenge  
  
CloudWatch Logs cannot directly push to Kinesis.  
  
Step Functions cannot pull from CloudWatch Logs.  
  
SNS can't pull from CloudWatch Logs either.  
  
  
Normally Lambda acts as the “glue” to pull logs and push them into Kinesis.  
If you want no Lambda, then you need something else to move data from CloudWatch to Kinesis.  
  
  
---  
  
Good Proof-of-Concept Plan  
  
Here’s what I suggest for your experiment:  
  
[1] CloudWatch Logs subscription filter → Kinesis directly (via a Firehose or native subscription)  
  
CloudWatch Logs CAN send logs directly to Kinesis Data Firehose via a subscription filter.  
  
NO Lambda needed.  
  
Firehose can then put records into:  
  
S3 (temporary bucket),  
  
Kinesis Stream (optionally),  
  
Later you can point Firehose to Splunk.  
  
  
  
You don’t even need Step Functions at this stage.  
  
  
---  
  
Production version  
  
Later, when you add Step Functions, Step Functions would orchestrate monitoring and flow control — not pull logs directly.  
  
  
---  
  
Example Architecture (No Lambda)  
  
For now:  
  
CloudWatch Log Group  
→ Subscription Filter  
→ Kinesis Data Firehose  
→ S3 Bucket (temporary storage for now)  
  
Later (production):  
  
CloudWatch Log Group  
→ Subscription Filter  
→ Kinesis Data Firehose  
→ Splunk Endpoint  
  
Optional Step Function (Production Monitoring/Orchestration):  
  
Step Function  
→ Waits for S3 delivery confirmation (or Kinesis checkpoint)  
→ Invokes a "success" or "retry" path  
  
But notice: Step Functions manage orchestration, not the direct data movement.  
  


