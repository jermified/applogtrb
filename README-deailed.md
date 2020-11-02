Events TRB Deck – Speaking Points

1. Introduction
   a. Introduce Self
   b. Hi I’m Jeremy Cheung and on behalf of the SRE Team, I am here to present on the topic of Application and Systems Logging Tool Selection as an Inform

2. Why Are We Talking About This?
   a. We’re in the business of managing a set of complex and interconnected services
   i. To do that well, we need capabilities to discern meaningful information from our apps and systems
   b. It's VERY IMPORTANT to realize the distinction between application data and SIEM/security related data. Both data types are invaluable to the organization and have distinct use cases and appropriate holding places
   c. Logging application and systems data has shown to be a difficult experience here and as an organization, we don’t uniformly collect logs on our apps and systems
   d. When we lack sufficient application and systems insights we fall into a reactive versus proactive stance in our response to incidents and outages
   i. This leads to confusion on investigations and triage of issues
   ii. Burns more time and cycles to reach resolution for all parties involved
   e. There’s no prescriptive guidance or supported patterns on how to pull events and logs data.
   i. Current methods for collecting application and systems events don’t scale well.

3. Business Capability Model
   a. Application and Systems Logging fits into Information Technology as an Operational Capability which in turn helps to deliver on larger Business Operational Capabilities
   i. Supporting Broader Mission Goals

4. Objectives
   a. Inform on the technologies and challenges involved
   b. Inform on the evaluation, testing and selection process SRE underwent
   c. Inform on the next steps with our selection of Datadog and how teams might want to engage

5. What is Application and Systems Logging?
   a. A methodology and process to monitor, aggregate and make sense of disparate events that occur through the IT Infrastructure and the Services within.

6. How we do this today?
   i. (pain point) We currently collect events and logs in different ways, with different platforms and that data gets stored in different mediums. Unfortunately, this lends to some confusion and makes it difficult to correlate data for acting upon.

ii. (pain point) There’s a general gap in knowledge and varying levels of expertise in collecting events and logs. Many times, the operator asked to pull up logs faces difficulties in finding those logs, and connecting those logs to how the application or system works.
iii. (pain point) Pulling events and log data is currently a hidden and high touch process that’s not well understood or documented.

7. Can someone go get the logs? (Slide Title)
   To help paint this picture, I’d like to share about a Service Engineer’s experience when incidents or outages arise with applications.
   a. When these situations occur, one of the early questions asked is “Can someone go get the logs?” a Service Engineer can experience a “pressure cooker” situation where she/he needs to come up with logs immediately to troubleshoot and triage.  
   b. Unless they are intimately aware and have expertise of the inner workings of the application/system, and the logging solution at hand (assuming logging is even setup), Service Engineers face friction points due to:
   i. Lack the “know how” in retrieving the logs
   ii. Don’t know how to read or deciper the logs
   iii. Experience difficulty in discerning how the application/system is supposed to work from the log data presented.
   iv. Hampered in their ability to interact with the data effectively due to usability issues with the logging solution.

8. POD – logs UI Story

Let me share a more precise example with a Service Engineer’s reflections in working with the logs for the application POD, also known as the Porfolio Overview Dashboard.

a. Tool that supports Annual Planning and Strategy Reviews by displaying a visualization of the body of work portfolio for a given strategy. Used by all programmatic teams, ELT and co-chairs.
b. Events from it currently are logged within Azure’s Log Analytics Workspace
c. Some of the paint points observed with working with the POD logs include:

1. UI and query results persistence issues, where queried data would last only for a finite amount of time on the results screen. The query would need to be run repeatedly to bring back the desired data.
2. Issues with the log data format has made correlation difficult and, in some cases, required exporting of the data to better work with it in other tools.

3. Current Landscape
   a. It’s important to also note that Application and Systems Logging applies to the larger landscape where we currently manage and monitor:
   i. 358 applications, that are hosted amongst our collection of 1208 servers (on prem and in the clouds), and 16 kubeclusters to go with it.

4. What do we do and How Do we Make it Better?
5. SRE Team

We apply our Site Reliability Engineering Principles.

a. Stop doing it (if we can)
i. (paint point) We currently collect events and logs in different ways and that data gets stored in different mediums. Unfortunately, this lends to confusion and makes it hard to correlate data.
b. Simple is Better
i. Move forth with a straightforward, common approach and framework to consolidate the collection of events and logs.  
c. Automate the right thing
i. We’ll reduce human error by codifying the event collection experience, which we also get the added benefit of documentation through the code and that gets stored in our source code management.

12. Intended Benefit
    What is the intended benefit here for everyone? At the core, we’re talking about driving maximum impact through the reduction of outages and incidents by:
    Reduce time to insight of issue
    Decrease mean time to resolution
    Reduce the time and effort to collect events and logs
    Increase visibility into knowing why issues occur
13. What did we Evaluate

[Speak to it from an Industry Perspective. We looked at our state and our maturity state. We looked at the Market in the last few years. When we first looked at monitoring space, it was in the positions, where we were best served by a variety of toolkits]

We first evaluated our current tool sets and our maturity state. And then we looked at the Industry Perspective in what the current Markets’ toolsets offer as far as capabilities go. Our big takeaway is that application logging and the ability to tie that to telemetry collected is becoming key in gaining rich insights for solving problems quickly. All the candidates we looked at, share this common thread.

14. How did we Evaluate
    a. Collected technical requirements and established use cases
    b. Built prototypes to garner feedback
    c. Measured and scored upon multiple criteria across the candidates
    i. The criteria included:
1. ease of use, install, and configuration of the tooling
1. whether the tooling supports system level and native apps logging contexts
1. whether the tools leant themselves nicely towards automation
1. the log exploration experience… to highlight a few

1. SCOM Evaluation – built and centered around on premise metrics and events collection. More transactional in nature. Does not hold data for long retention periods as its really a monitoring tool and not so much a log collecting solution. Heavily focused on persistent/traditional workloads and applications. We found that it does not accommodate for cloud apps and resources well.
1. Azure’s Log Analytics and Workspace Evaluation – Microsoft’s natural progression of SCOM but also incorporates cloud assets like, Azure VMs, Azure apps and Azure resources like AKS Clusters. Supports system level and native apps logging contexts. It does have limitations as it’s agent can ONLY log events to the Log Analytics workspace medium. Azure storage accounts and Event Hub are not supported mediums currently. Managing agents at scale becomes difficult as well since each agent holds its own unique configuration.
1. New Relic Evaluation – log collection is a new feature to the platform and configuration requires more effort and carries more dependencies than other tools. New to the logging collection space compared with other vendors.
1. Splunk Evaluation – Mature tool in the logging space. Experience with it so far is that its hard to get instrumented if you don’t have deep knowledge already in how Splunk works. Need to know what you what to collect on ahead of time. Once data is in the platform, indexing and searching on it is great. There is generally high involvement with Splunk Support to setup configurations. It's also where we're storing all our SIEM and some application data. This by the way is not a good and sustainable pattern for us as it's unwieldly to get new applications instrumented against Splunk and pumping more app data in has storage and performance implications on Splunk's primary use case for us, which is centered upon SIEM activities. We want to begin delineating and separating app data from SIEM data and have Splunk be the primary provider and holding place for just SIEM data.
1. Rollbar Evaluation – Great complimentary tool in nature and best utilized to further enrich the logging experience. Handles correlation between events and logs data to code base for applications very well. It’s one of the few tools on the market that offers a SDK for interacting with Salesforce Apex applications. It however does not support a systems level logging context and because of that, it does not fit the bill as a stand alone tool in this space.
1. Datadog Evaluation – logs exploration is amazing. Pulls telemetry information well. Easy to setup and configure for system level and native apps logging contexts. Has the most built in integrations with diverse data sources compared to other tools. Has 55 Azure related integrations. The SRE Team recently found tremendous value in this tool in helping solve for performance and scaling challenges faced with new IDM workloads that were introduced to our CICD tooling in Drone.

And with that, the SRE Team feels Datadog to be the best fit for purpose tool to meet Application and Systems Logging needs of IT.

21. Next Steps – Datadog
22. Questions
