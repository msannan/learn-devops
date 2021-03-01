Devops Essentials:

DevOps = Development + Operations

Aims:
1. Shorter Development Cycles
2. Increaseed Deployment Frequency
3. more Dependable releases
4. In close alignment with business objectives

Culture of Collaborations between developers and operations people

Shared Goals part of DevOps Culture
 - Development and Operations --- Speed <> Stability
 - Fast TTM (time-to-market)
 - Few production failures
 - Immediate recovery from failures

 Devops Concepts and Practices:

 1. Build Automation:
Automation of process of preparing code for deployment to a live environment.
e.g. compilation, linted, minified, transformed, unit tests, etc.
Why? It's fast, consistent, repeatable, portable, and more reliable.

2. Continuous Integration (CI):
practice of frequently merging code changes done by developers
Tools: Jenkins, TravisCI, Bamboo

3. Continuous Delivery (CD) and Continuous Deployment:
Continuous Delivery is a practice of continuously maintaining code in a deployable state
Continuous Deployment is the practice of deploying small code changes to production

4. Infrastructure as Code (IaC):
manage and provision infrastructure through code and automation.

5. Configuration Management:
Automated management of infrastructure - maintaining and changing state of pieces of infrastructure in a consistent, maintainable, and stable way
Tools: Ansible, Chef, Puppet, Salt

6. Orchestration:
automation that supports processes and workflows, such as provisioning resources.
e.g. scaling up and down, stability, save time, self service, granual insight into resource usage
Tools: Docker Swarm, Kubernetes, Zookeeper (Apache), Terraform (Orchestration + Infrastructure as Code)

7. Monitoring:
Collection and presentation of data about the performance and stability of services and infrastructure.
collect data such as memory usage, cpu, disk i/o, other resources over time, application logs, network traffic, etc.
real-time notifications (e.g. shrinking resources)
Postmortem analysis (something crashed last night, logs can be used to look for issues)
Fast Recovery, Better root cause analysis, visibility across teams, automated response
Can be used together with Orchestration tools
Tools: NewRelic, SenSu, AppDynamics

8. Microservices:
A microservice architecture breaks an application up into a Collection of small, loosely-coupled services.
Modularity, technological flexibility.

DevOps Tools:
Periodic Table: xebialabs.com/periodic-table-of-devops-tools

IaaS = Infrastructure as a service
PaaS = Platform as a service
SaaS = Software as a service
Serverless = FaaS = Function as a service
