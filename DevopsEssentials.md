# Devops Essentials

DevOps = `Development` + `Operations`

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

    Automation of process of preparing code for deployment to a live environment.<br />
    e.g. compilation, linted, minified, transformed, unit tests, etc.
    Why? It's fast, consistent, repeatable, portable, and more reliable.

2. Continuous Integration (CI):

    practice of frequently merging code changes done by developers<br />
    Tools: Jenkins, TravisCI, Bamboo

3. Continuous Delivery (CD) and Continuous Deployment:

    Continuous Delivery is a practice of continuously maintaining code in a deployable state<br />
    Continuous Deployment is the practice of deploying small code changes to production

4. Infrastructure as Code (IaC):

    manage and provision infrastructure through code and automation.

5. Configuration Management:

    Automated management of infrastructure - maintaining and changing state of pieces of infrastructure in a consistent, maintainable, and stable way<br />
Tools: Ansible, Chef, Puppet, Salt

6. Orchestration:

    automation that supports processes and workflows, such as provisioning resources.
    e.g. scaling up and down, stability, save time, self service, granual insight into resource usage<br />
    Tools: Docker Swarm, Kubernetes, Zookeeper (Apache), Terraform (Orchestration + Infrastructure as Code)

7. Monitoring:

    Collection and presentation of data about the performance and stability of services and infrastructure.<br />
    collect data such as memory usage, cpu, disk i/o, other resources over time, application logs, network traffic, etc.<br />
    real-time notifications (e.g. shrinking resources)<br />
    Postmortem analysis (something crashed last night, logs can be used to look for issues)<br />
    Fast Recovery, Better root cause analysis, visibility across teams, automated response<br />
    Can be used together with Orchestration tools<br />
    Tools: NewRelic, SenSu, AppDynamics

8. Microservices:

    A microservice architecture breaks an application up into a Collection of small, loosely-coupled services.<br />
    Modularity, technological flexibility.

DevOps Tools:

Periodic Table: xebialabs.com/periodic-table-of-devops-tools

IaaS = Infrastructure as a service
PaaS = Platform as a service
SaaS = Software as a service
Serverless = FaaS = Function as a service
