---
tags: [azure, course]
aliases: []
description:
public: true
dg-publish: true
created: 2023-03-06
---

# AZ-400-Get started on a DevOps transformation journey

## Sessions  

- 2023-04-16
  - Start: 12-52
  - Finish:

## Links

- [AZ-400: Get started on a DevOps transformation journey - Training | Microsoft Learn](https://learn.microsoft.com/en-us/training/paths/az-400-get-started-devops-transformation-journey/)
- [Azure DevOps Services Pricing | Microsoft Azure](https://azure.microsoft.com/en-gb/pricing/details/devops/azure-devops-services/)
- [Summary - Overview](https://dev.azure.com/makszin/PartsUnlimited)

## Introduction to DevOps

### What is DevOps?

![image](./media/devops-cycle-98924900.png)

OODA (Observe, Orient, Decide, Act) loop

### Shorten your cycle time

When you adopt DevOps practices:

- You shorten your cycle time by working in smaller batches.
- Using more automation.
- Hardening your release pipeline.
- Improving your telemetry.
- Deploying more frequently.

### Explore the DevOps journey

Remember, the goal is to shorten cycle time. Start with the release pipeline. How long does it take to deploy a change of one line of code or configuration? Ultimately, that is the brake on your velocity.

Continuous Integration drives the ongoing merging and testing of code, leading to an early finding of defects. Other benefits include less time wasted fighting merge issues and rapid feedback for development teams.
Build succeeded. Completed.

Continuous Delivery of software solutions to production and testing environments helps organizations quickly fix bugs and respond to ever-changing business requirements.
Continuous Delivery of software solutions to production and testing environments and phases image.

![image](./media/devops-continuous-delivery-4d3ba30a.png)

Remember, the goal is to shorten cycle time. Start with the release pipeline. How long does it take to deploy a change of one line of code or configuration? Ultimately, that is the brake on your velocity.

Continuous Integration
drives the ongoing merging and testing of code, leading to an early finding of defects. Other benefits include less time wasted fighting merge issues and rapid feedback for development teams.
Build succeeded. Completed.

Continuous Delivery
of software solutions to production and testing environments helps organizations quickly fix bugs and respond to ever-changing business requirements.
Continuous Delivery of software solutions to production and testing environments and phases image.

Version Control,
usually with a Git-based Repository, enables teams worldwide to communicate effectively during daily development activities. Also, integrate with software development tools for monitoring activities such as deployments.
Master, feature 1, and feature 2 branches representation.

Use Agile planning and lean project management techniques to:

- Plan and isolate work into sprints.
- Manage team capacity and help teams quickly adapt to changing business needs.
- A DevOps Definition of Done is working software collecting telemetry against the intended business goals.
-

Kanban board
with columns to-do, in progress, ready to code, in progress, ready, in progress, review, and done.

Monitoring and Logging of running applications. Including production environments for application health and customer usage. It helps organizations create a hypothesis and quickly validate or disprove strategies. Rich data is captured and stored in various logging formats.
Charts example.

Public and Hybrid Clouds
have made the impossible easy. The cloud has removed traditional bottlenecks and helped commoditize Infrastructure. You can use Infrastructure as a Service (IaaS) to lift and shift your existing apps or Platform as a Service (PaaS) to gain unprecedented productivity. The cloud gives you a data center without limits.
Public cloud.

Infrastructure as Code (IaC): Enables the automation and validation of the creation and teardown of environments to help deliver secure and stable application hosting platforms.
Infrastructure as Code (IaC) representation.

Use Microservices architecture to isolate business use cases into small reusable services that communicate via interface contracts. This architecture enables scalability and efficiency.
Monolithic and microservices representation.

Containers are the next evolution in virtualization. They're much more lightweight than virtual machines, allow much faster hydration, and easily configure files.
Containers.

DevOps may hurt at first.

Version Control, usually with a Git-based Repository, enables teams worldwide to communicate effectively during daily development activities. Also, integrate with software development tools for monitoring activities such as deployments.
Master, feature 1, and feature 2 branches representation.

Continue: <https://learn.microsoft.com/en-us/training/modules/introduction-to-devops/5-explore-shared-goals-define-timelines>

### Explore shared goals and define timelines

## Choose the right project

### Explore greenfield and brownfield projects

A common misconception is that DevOps is only for greenfield projects and suits startups best. However, DevOps can also succeed with brownfield projects.

### Decide when to use greenfield and brownfield projects

- greenfield projects
- brownfield projects

### Decide when to use systems of record versus systems of engagement

Systems that provide the truth about data elements are often-called systems of record. Systems of record emphasize accuracy and security.Example: banking.

Systems of engagement are modified regularly. Usually, it is a priority to make quick changes over ensuring that the changes are correct.

DevOps practices apply to both types of systems. The most significant outcomes often come from transforming systems of record.

### Identify groups to minimize initial resistance

In discussions around continuous delivery, we usually categorize users into three general buckets:

- Canary users voluntarily test bleeding edge features as soon as they're available.
- Early adopters who voluntarily preview releases, considered more refined than the code that exposes canary users.
- Users who consume the products after passing through canary and early adopters.

It's also important to roll out changes incrementally. There is an old saying in the industry that any successful large IT system was previously a successful small IT system.

### Identify project metrics and key performance indicators (KPIs)

While there is no specific list of metrics and KPIs that apply to all DevOps Projects, the following are commonly used:

Faster outcomes

- Deployment Frequency. Increasing the frequency of deployments is often a critical driver in DevOps Projects.
- Deployment Speed. It is necessary to reduce the time that they take.
- Deployment Size. How many features, stories, and bug fixes are being deployed each time?
- Lead Time. How long does it take from the creation of a work item until it is completed?

Efficiency

- Server to Admin Ratio. Are the projects reducing the number of administrators required for a given number of servers?
- Staff Member to Customers Ratio. Is it possible for fewer staff members to serve a given number of customers?
- Application Usage. How busy is the application?
- Application Performance. Is the application performance improving or dropping? (Based upon application metrics)?

Quality and security

- Deployment failure rates. How often do deployments (or applications) fail?
- Application failure rates. How often do application failures occur, such as configuration failures, performance timeouts, and so on?
- Mean time to recover. How quickly can you recover from a failure?
- Bug report rates. You do not want customers finding bugs in your code. Is the amount they are seeing increasing or lowering?
- Test pass rates. How well is your automated testing working?
- Defect escape rate. What percentage of defects are being found in production?
- Availability. What percentage of time is the application truly available for customers?
- Service level agreement achievement. Are you meeting your service level agreements (SLAs)?
- Mean time to detection. If there is a failure, how long does it take for it to be detected?

## Describe team structures

### Explore agile development practices

- Waterfall. Customers often don't know what they want until they see it or can't explain what they need.
- Agile methodology constantly emphasizes adaptive planning and early delivery with continual improvement.

Manifesto for Agile software development.

They said that:

- Development needs to favor individuals and interactions over processes and tools.
- Working software over comprehensive documentation.
- Customer collaboration over contract negotiation.
- Respond to changes over following a plan.

### 12 Principles Behind the Agile Manifesto

- Our highest priority is to satisfy the customer through the early and continuous delivery of valuable software.
- Welcome changing requirements, even late in development. Agile processes harness change for the customer's competitive advantage.
- Deliver working software frequently, from a couple of months to a couple of weeks, with a preference for a shorter timescale.
- Businesspeople and developers must work together daily throughout the project.
- Build projects around motivated individuals. Give them the environment and support they need and trust them to get the job done.
- The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.
- Working software is the primary measure of progress.
- Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
- Continuous attention to technical excellence and good design enhances agility.
- Simplicity - the art of maximizing the amount of work not done - is essential.
- The best architectures, requirements, and designs emerge from self-organizing teams.
- The team regularly reflects on how to become more effective, then tunes and adjusts its behavior accordingly.

### Define organization structure for agile practices

- horizontal teams
- vertical teams

Vertical teams have been shown to provide more good outcomes in Agile projects. Each product must have an identified owner.

### Explore ideal DevOps team members

Types of agile coach

- technical experts
- focused on agile processes

### Enable in-team and cross-team collaboration

All meetings should have strict timeframes and, more importantly, have a plan. If there is no plan, there should be no meeting.

### Select tools and processes for agile practices

These tools usually include:

- Project planning and execution monitoring abilities (including how to respond to impediments).
- Automation for stand-up meetings.
- Management and tracking of releases.
- A way to record and work with the outcomes of retrospectives.
- Many include Kanban boards and detailed sprint planning options.

## Choose the DevOps tools

### What is Azure DevOps?

What does Azure DevOps provide?
Azure DevOps includes a range of services covering the complete development life cycle.

- Azure Boards: agile planning, work item tracking, visualization, and reporting tool.
- Azure Pipelines: a language, platform, and cloud-agnostic CI/CD platform-supporting containers or Kubernetes.
- Azure Repos: provides cloud-hosted private git repos.
- Azure Artifacts: provides integrated package management with support for Maven, npm, Python, and NuGet package feeds from public or private sources.
- Azure Test Plans: provides an integrated planned and exploratory testing solution.

### What is GitHub?

GitHub is a Software as a service (SaaS) platform from Microsoft that provides Git-based repositories and DevOps tooling for developing and deploying software.

GitHub provides a range of services for software development and deployment.

- Codespaces: Provides a cloud-hosted development environment (based on Visual Studio Code) that can be operated from within a browser or external tools. Eases cross-platform development.
- Repos: Public and private repositories based upon industry-standard Git commands.
- Actions: Allows for the creation of automation workflows. These workflows can include environment variables and customized scripts.
- Packages: The majority of the world's open-source projects are already contained in GitHub repositories. GitHub makes it easy to integrate with this code and with other third-party offerings.
- Security: Provides detailed code scanning and review features, including automated code review assignment.

### Explore an authorization and access strategy

Tools like Visual Studio and Azure DevOps natively support the use of Microsoft Accounts and Azure AD.

- personal access tokens
- Security groups
- Multifactor authentication

As part of a Conditional Access policy, you might require:

- Security group membership.
- A location or network identity.
- A specific operating system.

### Migrate or integrate existing test management tools

- Azure Test Plans
- Test feedback extension
- Apache Jmeter (load testing)
- SoapUI is another testing framework for SOAP and REST testing.

### Design a license management strategy

If you have multiple teams building their solutions, you don't want to wait in the queue to start building yours.

[Azure DevOps Services Pricing | Microsoft Azure](https://azure.microsoft.com/en-gb/pricing/details/devops/azure-devops-services/)


https://learn.microsoft.com/en-gb/training/modules/plan-agile-github-projects-azure-boards/

### Link GitHub to Azure Boards

The integration is created using the Azure Boards App, acting as a bridge between Azure Boards and GitHub. 
[Azure Boards · GitHub Marketplace · GitHub](https://github.com/marketplace/azure-boards)

### Configure GitHub Projects


- Create project
- Add description and name 
- Add issue 
- Add custom field
- Manager permissions 


### Manage work with GitHub Project boards 

- Create iteration field 
- Add new iteration

### Customize Project views in GitHub 


- Switch to board view 
- Create multiple views 


### Lab Agile Planning and Portfolio Management with Azure Boards 

1. Create new project
2. Task 1: Manage teams, areas, and iterations


## Introduction to source control


Continue: 
https://microsoftlearning.github.io/AZ400-DesigningandImplementingMicrosoftDevOpsSolutions/Instructions/Labs/AZ400_M01_L01_Agile_Planning_and_Portfolio_Management_with_Azure_Boards.html#review
https://learn.microsoft.com/en-gb/training/modules/introduction-to-source-control/