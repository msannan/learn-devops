# Agile vs DevOps

- DevOps is a practice of bringing development and operations teams together whereas Agile is an iterative approach that focuses on collaboration, customer feedback and small rapid releases.
- DevOps focuses on constant testing and delivery while the Agile process focuses on constant changes.
- The target area of Agile is Software development whereas the Target area of DevOps is to give end-to-end business solutions and fast delivery.
- DevOps focuses more on operational and business readiness whereas Agile focuses on functional and non-function readiness.

# Define CI, Continuous Delivery & Continuous Deployment

### Continuous Integration (CI):

practice of frequently merging code changes done by developers.

### Continuous Delivery (CD)

Continuous Delivery is a practice of continuously maintaining code in a deployable state.
 
### Continuous Deployment:

Continuous Deployment is the practice of deploying small code changes to production.

# What are the benefits of Cloud Computing?

Cloud computing offers your business many benefits. It allows you to set up what is essentially a virtual office to give you the flexibility of connecting to your business anywhere, any time. With the growing number of web-enabled devices used in today's business environment (e.g. smartphones, tablets), access to your data is even easier.

There are many benefits to moving your business to the cloud:

- Reduced IT costs
- Scalability
- Business continuity
- Collaboration efficiency
- Flexibility of work practices
- Access to automatic updates

# Difference b/w Git & Github

The key difference between `Git` and `GitHub` is that Git is an `open-source` tool developers install `locally` to manage source code, while `GitHub` is an `online service` to which developers who use Git can connect and upload or download resources.

# Stages of Git

Files in a repository go through `three` stages before being under version control with git:

### 1. Untracked:
    the file exists, but is not part of git's version control
### 2. Staged:
    the file has been added to git's version control but changes have not been committed
### 3. Committed:
    the change has been committed

# What are 3 methods of git reset?

1. `--soft`: uncommit changes, changes are left staged (index).
1. `--mixed` (default): uncommit + unstage changes, changes are left in working tree.
1. `--hard`: uncommit + unstage + delete changes, nothing left.