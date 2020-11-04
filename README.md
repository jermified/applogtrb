# Application Logging Selection an Inform – Speaking Points

1. Introduction
   - Introduce Self and Team
2. Why Are We Talking About This?

   - What Application Logging Is
     - Rendering of an application’s activity to store it
     - Activity data takes different forms
   - Why we need Logs
     - To review activity when an application doesn’t work as expected
     - One of the first places we turn to for troubleshooting issues

3. Business Capability Model
   - Tie into Information Technology
   - Delivers on larger Business Operational Capabilities
   - Supports Broader Mission Goals
4. Objectives
   - Technologies and challenges invovled
   - Evaluation, testing and selection
   - Next Steps on Datadog and how teams can engage
5. How we do this today
   - We log in different ways to different places (file system, database, cloud)
   - Hidden and not well documented process
   - Confusing and hard to correlate data
     - Engineers Challenges
       - Configuring an app to log is not an easy matter
       - Logs can be difficult to work with
       - As a result, not all apps get logged
       - Having to SSH/login directly to a machine
   - Because of these difficulties, we don't do it well as we could
6. Can someone go get the logs?
   - logs come into play during incidents and outages
     - “pressure cooker” situation
     - Logs are needed immediately
   - Frictions points faced:
     - how to access logs
     - how to understand the logs
     - difficulties in using the logging platform
   - All this leads to applications being down longer than they need to be
   - Distracts us from making great impacts
7. POD – logs UI Story
   - Describe POD and where the logs are stored
   - Pain Points
     - Persistence issues on log query results
     - Difficulties in correlating data due to log formats
8. Current Landscape
   - Scope and Metrics
     - 358 apps
     - 1208 server
     - 16 kubeclusters
       - Kubernetes Quick Describe
9. What do we do and How Do we Make it Better?
   - SRE Team Principles
   - Stop doing it (if we can help it)
   - Simple is Better
   - Automate the Right Thing
   - Applying Principles
     - Stop logging in different ways to different places
     - Introduce a simple, flexible and easy to use platform
     - Codify logging configuration
     - Document through Code
10. Intended Benefit
    - Drive maximum impact through reducing incidents and outages
      - Collect logs more easily and quickly
      - Increase visibility on why issues occur
      - Faster time to insights on issues
      - Resolve issues faster
11. What did we Evaluate
    - Current Tools and Maturity States
    - Industry/Current Market Offerings/Themes
12. How did we Evaluate
    - Use cases and technical requirements
    - Prototypes
    - Scored on Evaluation Criteria
      - General ease of use and UI experience
      - Supports all logging scenarios
      - Maturity states
      - Automation friendly
13. SCOM
    - Tooling we use for monitoring
    - Built with the datacenter in mind
    - Highly transactional and doesn’t hold its data as long as other tools
    - Not suited for well for cloud apps
14. Azure Log Analytics Workspace
    - Microsoft’s natural progression from SCOM to include cloud resources
    - Supports all base use cases (on prem and cloud)
    - Agents have limitations
    - Log analytics is only storage location
    - POD support experience has shown working with log analytics can be better
    - Difficult to manage at scale since agents hold their own unique config
15. New Relic Logs
    - Good tie in between monitoring and logging capabilities
    - Logs is a new feature
    - Configuration requires more effort and carries more dependencies than other tools
16. Splunk Evaluation
    - Defacto SIEM tool
    - Mature in logging space. Index and searching is great on it
    - Steep learning curve and not the easiest of tools to work with
    - [Talk about how some application data has seeped in the tool and we don’t want that anymore] [Separation of App vs SIEM Data]
      - Keep Splunk as our dedicated SIEM
      - Industry Standard to separate App and SIEM data
17. Rollbar
    - More of a complimentary tool
    - Strength lies in correlating log data to code base
    - Doesn’t fit the bill since it only supports app logging scenarios
18. Datadog
    - Log exploration is amazing and pulls telemetry info well
    - Found to be the easiest to setup
    - Carries the most integrations with different data sources (55 are Azure related)
    - Delivered immediate value with IDM
19. Next Steps – Datadog
    - Deploy to all SRE Services
    - Onboard a few teams to POC
    - Evaluate opportunities to consolidate Observability Suite
    - Return to TRB to propose an enterprise standard
