# DevOps interview preparation roadmap

## Role

DevOps Engineer

## Experience Level

Intermediate/Mid DevOps Engineer

## Key Concepts

## Artifact Management

- Artifactory, Nexus, GitHub Packages, AWS CodeArtifact, and Azure Artifacts
- Storing build artifacts, container images, libraries, and release packages
- Versioning artifacts so deployments can be repeated and rolled back
- Promoting artifacts between environments such as dev, staging, and production
- Controlling access to artifacts and cleaning up old versions

## Static Code Analysis and Security Scanning

- Static code analysis checks code quality, bugs, vulnerabilities, and bad patterns before deployment
- Tools include SonarQube, Snyk, Trivy, Checkov, Semgrep, and GitHub code scanning
- Scans can run in CI/CD pipelines before code is merged or deployed
- Container image scanning helps detect vulnerable packages inside Docker images
- Infrastructure scanning checks Terraform, Kubernetes manifests, and cloud configuration files

## Network Access Control

- Network access control decides which users, systems, ports, and services can communicate
- Examples include firewalls, security groups, NACLs, routing rules, private subnets, and VPNs
- Access should follow least privilege and only allow required traffic
- Production services should not be open to the internet unless there is a clear need
- Network policies in Kubernetes can control pod-to-pod communication

## Key Management System

- A Key Management System protects encryption keys used for data, secrets, disks, and applications
- Examples include AWS KMS, Azure Key Vault, Google Cloud KMS, and HashiCorp Vault
- KMS helps with encryption at rest, key rotation, access control, and audit logs
- Keys should not be stored directly in code, images, or plain text configuration files

## Data and Database Management

- Data management covers backups, retention, recovery, encryption, migration, and access control
- Database management includes performance tuning, replication, patching, indexing, and monitoring
- Important topics include RPO, RTO, snapshots, point-in-time recovery, and disaster recovery
- Managed databases reduce operational work because the cloud provider handles many maintenance tasks
- Self-managed databases give more control but require stronger operational discipline

## Advanced Object Storage

- Object storage is used for unstructured data such as backups, logs, images, videos, static assets, archives, and data lakes
- Examples include Amazon S3, Azure Blob Storage, Google Cloud Storage, and MinIO
- Storage classes help control cost based on how often data is accessed
- Hot storage is used for frequently accessed data, while cold or archive storage is used for rarely accessed data
- Lifecycle policies can automatically move objects between storage classes or delete old data after a defined period
- Intelligent tiering can automatically move objects to cheaper tiers based on access patterns
- Versioning protects against accidental deletion or overwrite, but it can increase storage cost if not managed
- Object lock and retention policies can help protect critical data from deletion or ransomware
- Encryption, access policies, bucket policies, private endpoints, and audit logs are important for security
- Cost optimization should include lifecycle rules, compression, cleanup of old versions, monitoring, and access pattern review

## VPN and Private Connectivity

- VPNs create secure encrypted connections between networks or users and private infrastructure
- Client VPN allows engineers to access private resources securely
- Site-to-site VPN connects two networks, such as an office network and a cloud VPC
- VPN setup requires routing, authentication, encryption, and firewall rules
- Alternatives include private links, direct connections, and bastion hosts

## Advanced Server Security

- Disable root login, use SSH keys, control sudo access, and enforce least privilege
- Keep servers patched and remove unused packages, users, ports, and services
- Use auditing tools such as `auditd`, system logs, and centralized logging
- Harden SSH, enable firewall rules, and limit access by IP where possible
- Use backups, monitoring, vulnerability scanning, and incident response procedures

## Container Runtimes

- Docker is a popular container platform used for building and running containers
- containerd and CRI-O are container runtimes commonly used by Kubernetes
- Kubernetes does not need Docker directly; it uses runtimes through the Container Runtime Interface
- A DevOps Engineer should understand images, containers, registries, tags, volumes, networks, and runtime security

## Configuration Management

- Configuration management tools automate server setup and application configuration
- Examples include Ansible, Chef, Puppet, and SaltStack
- Ansible is agentless and commonly used for provisioning, patching, deployments, and configuration changes
- Configuration management helps reduce manual server changes and improves repeatability

## Kubernetes and Orchestration

- Kubernetes manages containerized applications across a cluster of nodes
- Important objects include Pods, Deployments, Services, ConfigMaps, Secrets, Ingress, Jobs, and StatefulSets
- Kubernetes handles scheduling, self-healing, scaling, service discovery, and rolling updates
- Intermediate knowledge should include probes, resource requests and limits, namespaces, RBAC, storage, and networking
- CKA and CKAD topics are useful for building strong Kubernetes knowledge

## Load Balancing

- Load balancers distribute traffic across multiple application instances
- Application Load Balancers work at layer 7 and understand HTTP/HTTPS routing
- Network Load Balancers work at layer 4 and handle TCP/UDP traffic with high performance
- Common algorithms include round robin, least connections, weighted routing, and IP hash
- Health checks are important so traffic is not sent to unhealthy backends

## API Gateway

- An API Gateway manages access to backend APIs
- It can handle routing, authentication, authorization, rate limiting, request transformation, and logging
- Open-source examples include Apache APISIX, Kong, KrakenD, and Tyk
- Cloud examples include AWS API Gateway, Azure API Management, and Google API Gateway
- API Gateways are useful in microservice environments where many services expose APIs

## Secrets Management

- Secrets include passwords, API keys, tokens, certificates, SSH keys, and database credentials
- Secrets should not be stored in Git, Docker images, or plain environment files without protection
- Tools include HashiCorp Vault, AWS Secrets Manager, Azure Key Vault, Google Secret Manager, and Kubernetes Secrets with encryption
- Good secrets management includes rotation, access control, audit logs, and separation between environments

## CI/CD and Automation

- CI/CD automates build, test, scan, approval, deployment, and rollback workflows
- Tools include Jenkins, GitHub Actions, GitLab CI, Azure DevOps, AWS CodePipeline, and Argo CD
- Pipelines should use secrets securely, produce artifacts, run tests, and support repeatable deployments
- Intermediate engineers should understand approvals, deployment strategies, rollbacks, and environment promotion

## Logging, Monitoring, and Alerting

- Logs help explain what happened inside systems and applications
- Metrics show the health and performance of systems over time
- Alerts notify teams when something needs attention
- Important signals include latency, traffic, errors, saturation, CPU, memory, disk, uptime, and error logs
- Tools include Prometheus, Grafana, Loki, ELK/OpenSearch, CloudWatch, Azure Monitor, and Google Cloud Monitoring

## Cost Optimization

- Cost optimization means reducing waste without hurting reliability or performance
- Cloud examples include right-sizing instances, reserved capacity, autoscaling, storage lifecycle policies, and deleting unused resources
- On-premise examples include capacity planning, virtualization, hardware utilization, and power management
- Cost should be monitored with budgets, tags, reports, and alerts

## Agile Workflow

- DevOps work often connects with Agile tasks, sprint planning, incidents, releases, and postmortems
- Tools include Jira, Azure Boards, GitHub Issues, Linear, and Trello
- Good workflow includes clear tickets, ownership, acceptance criteria, documentation, and communication
- DevOps tasks should be visible so developers, QA, security, and operations understand progress and blockers

## Identity and Access Management

- IAM controls who can access what and what actions they can perform
- Important concepts include users, groups, roles, policies, service accounts, MFA, and least privilege
- Cloud IAM should avoid long-lived credentials where possible and prefer roles or workload identity
- Access should be reviewed regularly and removed when no longer needed

## Infrastructure as Code

- Infrastructure as Code manages infrastructure through files and automation
- Tools include Terraform, CloudFormation, Pulumi, Bicep, and Crossplane
- Intermediate concepts include remote state, locking, modules, workspaces, drift detection, imports, and policy checks
- IaC should be reviewed, versioned, tested, and applied through controlled pipelines

## Web Application Firewall

- A Web Application Firewall protects web applications from common attacks
- It can block SQL injection, cross-site scripting, bad bots, suspicious requests, and known attack patterns
- Examples include AWS WAF, Azure WAF, Cloudflare WAF, ModSecurity, and Google Cloud Armor
- WAF rules should be monitored carefully to avoid blocking legitimate users

## Service Mesh Basics

- A service mesh manages service-to-service communication inside a microservice environment
- It can provide mTLS, traffic routing, retries, observability, and policy enforcement
- Examples include Istio, Linkerd, Consul, Cilium, and Calico for networking and network policy
- Service mesh adds power but also complexity, so it should solve a real operational need

## GitOps and Argo CD

- GitOps uses Git as the source of truth for infrastructure and application deployment
- Argo CD watches Git repositories and syncs Kubernetes clusters to match the desired state
- This improves auditability, rollback, environment consistency, and deployment visibility
- GitOps works well with Kubernetes manifests, Helm charts, and Kustomize

## Tracing and Observability

- Tracing follows a request as it moves across services
- It is useful in microservices because one user request may pass through many services
- Traces help identify slow services, failed dependencies, and bottlenecks
- Tools include Jaeger, Zipkin, Tempo, OpenTelemetry, Datadog, and New Relic

## Microservices

- Microservices split applications into smaller services that can be built, deployed, and scaled independently
- Important topics include service discovery, API communication, retries, timeouts, observability, and deployment strategy
- Microservices require strong monitoring, logging, tracing, CI/CD, and network security
- They can improve flexibility but add operational complexity

## Synthetic Monitoring

- Synthetic monitoring tests applications from a user's point of view
- It can check login flows, APIs, checkout pages, uptime, and response times
- Synthetic tests run on a schedule and can alert teams before real users report problems
- Tools include Grafana Synthetic Monitoring, Datadog Synthetics, Pingdom, Checkly, and New Relic

## Caching and Queuing

- Caching stores frequently used data so applications can respond faster and reduce database load
- Tools include Redis, Valkey, Memcached, and CDN caches
- Queuing systems allow services to process work asynchronously
- Tools include RabbitMQ, Kafka, SQS, Azure Service Bus, and Google Pub/Sub
- Queues help with retries, background jobs, traffic spikes, and decoupling services

## Incident Management

- Incident management is the process of detecting, responding to, resolving, and learning from production issues
- Important practices include severity levels, escalation, communication, runbooks, timelines, and postmortems
- A good incident response focuses on restoring service first and then finding root cause
- Postmortems should be blameless and should produce practical follow-up actions

## Root Cause Analysis

- Root Cause Analysis is the process of finding the real reason an incident or failure happened
- It should go beyond the immediate error and identify the underlying system, process, configuration, or human factor
- Common methods include the 5 Whys, timeline review, log analysis, metrics review, and incident postmortems
- A good RCA should include what happened, impact, root cause, contributing factors, resolution, and prevention steps
- The goal is not to blame people but to prevent the same issue from happening again

## Standard Operating Procedure

- A Standard Operating Procedure is a clear step-by-step guide for performing a repeated operational task
- SOPs are useful for deployments, server patching, backups, access requests, incident response, and rollback procedures
- A good SOP should include purpose, scope, prerequisites, steps, validation checks, rollback steps, and ownership
- SOPs reduce confusion, improve consistency, and make it easier for team members to perform tasks safely
- SOPs should be reviewed and updated whenever tools, systems, or processes change

## Documentation

- Documentation records how systems, processes, deployments, and troubleshooting steps work
- Good documentation helps teams collaborate, onboard faster, reduce repeated questions, and recover from incidents
- Important DevOps documentation includes architecture diagrams, runbooks, SOPs, deployment guides, incident reports, and environment details
- Documentation should be simple, accurate, easy to find, and updated as systems change
- Poor or outdated documentation can create operational risk during incidents or handovers

## Container Registries

- Container registries store and distribute container images
- Examples include Docker Hub, GitHub Container Registry, Amazon ECR, Azure Container Registry, and Google Artifact Registry
- Good registry management includes image tagging, scanning, access control, retention policies, and promotion between environments

## SIEM Tools

- SIEM means Security Information and Event Management
- SIEM tools collect security logs, detect suspicious activity, and help with investigation
- Examples include Splunk, Microsoft Sentinel, Elastic Security, IBM QRadar, and Google Chronicle
- SIEM is useful for audit trails, threat detection, alerting, and compliance

## Helm

- Helm is a package manager for Kubernetes
- It uses charts to define and deploy Kubernetes applications
- Helm helps manage templates, values, releases, upgrades, and rollbacks
- It is commonly used to install tools like ingress controllers, monitoring stacks, and application workloads
- A Helm chart usually contains templates, default values, chart metadata, and optional dependencies
- `values.yaml` is used to customize deployments across environments such as dev, staging, and production
- Helm releases make it easier to track what was installed, upgrade applications, and roll back failed deployments
- Intermediate knowledge should include `helm install`, `helm upgrade`, `helm rollback`, `helm uninstall`, `helm template`, and `helm lint`
- Helm should be used carefully with secrets, environment-specific values, and chart versioning

## Kubernetes Security

- Kubernetes security includes RBAC, namespaces, network policies, secrets, image scanning, and pod security controls
- Containers should run with least privilege and avoid root when possible
- Resource limits should be used to reduce noisy-neighbor problems
- Cluster access should be controlled with strong authentication, authorization, and audit logs

## Advanced Networking

- Intermediate networking includes routing, subnetting, NAT, VPNs, private links, DNS, TLS, load balancing, and network troubleshooting
- Important tools include `curl`, `dig`, `nslookup`, `traceroute`, `ip`, `ss`, `tcpdump`, and `mtr`
- A DevOps Engineer should be able to trace traffic from user request to DNS, load balancer, firewall, server, container, and application

## Deployment Strategies

- Intermediate DevOps Engineers should understand more than basic deployment
- Common strategies include rolling deployment, blue-green deployment, canary deployment, feature flags, and shadow deployment
- Rolling deployments update instances gradually, reducing downtime but requiring good health checks
- Blue-green deployments keep two environments and switch traffic when the new version is ready
- Canary deployments release to a small percentage of users first, then increase traffic if metrics look healthy
- Feature flags allow teams to deploy code without immediately exposing the feature to everyone
- Good deployment strategy should include rollback, monitoring, release notes, and ownership

## Release Management

- Release management controls how software moves from development to production
- It includes versioning, approvals, release notes, change windows, rollback planning, and stakeholder communication
- Intermediate engineers should understand semantic versioning, artifact promotion, environment promotion, and release tagging
- A release should be traceable from Git commit to artifact to deployed environment
- High-risk releases should have a tested rollback plan and clear success criteria

## Reliability, SLOs, and Error Budgets

- Reliability means the system performs correctly and consistently for users
- SLIs are measurable indicators such as request latency, error rate, availability, and throughput
- SLOs are reliability targets, such as 99.9% availability or 95% of requests under 300ms
- Error budgets define how much failure is acceptable before reliability work must take priority
- These concepts help balance feature delivery with production stability

## Disaster Recovery and Business Continuity

- Disaster recovery focuses on restoring systems after serious failures
- Important terms include RPO and RTO
- RPO means how much data loss is acceptable
- RTO means how quickly the system must be restored
- Recovery planning should include backups, replication, snapshots, restore testing, failover steps, and documentation
- Backups are only reliable when restore has been tested

## Policy as Code and Governance

- Policy as Code means defining rules as code so infrastructure and deployments can be checked automatically
- Tools include Open Policy Agent, Conftest, Sentinel, Checkov, and cloud policy tools
- Policies can enforce tagging, approved regions, encryption, restricted ports, image sources, and least privilege
- Governance should guide teams without slowing delivery unnecessarily
- Automated policy checks are useful in CI/CD and Infrastructure as Code workflows

## Software Supply Chain Security

- Software supply chain security protects the process of building, packaging, and deploying software
- Important practices include dependency scanning, image scanning, signed commits, signed images, SBOMs, and trusted build pipelines
- Teams should know where dependencies come from and whether they contain vulnerabilities
- Build systems should avoid exposing secrets and should produce traceable artifacts
- Tools include Snyk, Trivy, Grype, Cosign, Syft, Dependabot, and GitHub Advanced Security

## Advanced Kubernetes Operations

- Intermediate Kubernetes knowledge should include scheduling, taints, tolerations, affinity, resource quotas, and autoscaling
- Horizontal Pod Autoscaler scales Pods based on metrics such as CPU, memory, or custom metrics
- Cluster Autoscaler adds or removes nodes based on pending Pods and resource needs
- Probes help Kubernetes know when a container is ready, healthy, or needs restart
- PodDisruptionBudgets help protect availability during maintenance or node upgrades
- Engineers should understand how to troubleshoot image pull errors, CrashLoopBackOff, pending Pods, DNS issues, and failed rollouts

## Advanced CI/CD Patterns

- Intermediate pipelines should include artifact promotion, environment approvals, security gates, and rollback steps
- Pipelines should separate build once from deploy many
- Matrix builds can test across multiple versions or environments
- Manual approvals may be required before production deployments
- Pipelines should avoid long-lived credentials and prefer short-lived tokens or workload identity where possible
- Deployment status should be visible to developers and operations teams

## Advanced Observability

- Observability should help answer why a system is failing, not only whether it is up or down
- Good observability combines logs, metrics, traces, events, dashboards, and alerts
- Alerts should be actionable and tied to user impact where possible
- Runbooks should be linked to important alerts
- High-cardinality labels and noisy alerts should be controlled to avoid cost and alert fatigue
- Teams should monitor dependencies such as databases, queues, caches, DNS, and third-party APIs

## Performance and Capacity Planning

- Capacity planning helps make sure systems have enough resources for current and future demand
- Important areas include CPU, memory, disk, network, database connections, queue depth, and request throughput
- Performance testing helps identify limits before production traffic exposes them
- Load testing, stress testing, and soak testing are used for different goals
- Capacity planning should influence autoscaling rules, instance sizing, database sizing, and cost estimates

## Common Interview Questions

### Question 1

Your team builds a Java application in CI and deploys the same build to dev, staging, and production. Explain how you would use an artifact repository to make the release process repeatable and traceable.

An artifact repository stores build outputs such as packages, binaries, libraries, and container images. Examples include Artifactory, Nexus, GitHub Packages, and AWS CodeArtifact.

It is important because deployments should use tested and versioned artifacts instead of rebuilding randomly on each server. This makes releases repeatable, traceable, and easier to roll back.

In a real pipeline, I would tag artifacts with the Git commit SHA, build number, semantic version, and environment promotion status. I would also restrict who can publish or delete production artifacts.

### Question 2

Your pipeline currently deploys code as soon as tests pass, but security issues are being found late. Tell me how you would introduce static code analysis and security scanning into the CI/CD process.

I would add static code analysis as a pipeline step after checkout and before deployment. The tool would scan the code for bugs, security issues, bad patterns, and quality problems.

If the scan finds serious issues, the pipeline should fail and stop the deployment. This helps catch problems early before they reach production.

### Question 3

You are deploying a web application with a public load balancer, private application servers, and a private database. Explain how you would design network access control for this setup in the cloud.

Network access control means deciding which traffic is allowed between users, systems, and services. In the cloud, I would use security groups, NACLs, private subnets, route tables, and firewalls.

For example, a database should not be open to the internet. It should only accept traffic from the application servers that need it.

In this design, the load balancer can accept `80` and `443` from the internet, the application servers can accept traffic only from the load balancer, and the database can accept traffic only from the application server security group.

### Question 4

Your application stores customer data and needs encryption for databases, disks, and secrets. Explain how you would use a Key Management System to protect encryption keys and control access.

A Key Management System protects encryption keys used for disks, databases, applications, and secrets. Examples include AWS KMS, Azure Key Vault, Google Cloud KMS, and HashiCorp Vault.

Teams should use a KMS because encryption keys must be controlled, rotated, audited, and protected from unauthorized access.

### Question 5

Your production database must survive accidental deletion, disk failure, and regional outage. Discuss how backup, snapshot, and replication would help in this real-life recovery plan.

A backup is a copy of data kept for recovery. A snapshot is a point-in-time copy of a disk, volume, or database. Replication copies data continuously or near continuously to another location.

Backups are useful for recovery from data loss. Snapshots are useful before changes or patching. Replication helps with availability and disaster recovery.

### Question 6

Your developers need secure access to private cloud resources, and the company office also needs private connectivity to the cloud network. Explain when you would use client VPN and when you would use site-to-site VPN.

A client VPN allows individual users to connect securely to a private network. It is commonly used by engineers working remotely.

A site-to-site VPN connects two networks together, such as an office network and a cloud VPC. It is used when systems in both networks need private communication.

### Question 7

You have just provisioned a fresh Linux server that will run a public-facing API. Walk me through the security hardening steps you would complete before production traffic is allowed.

I would disable root login, use SSH keys, limit SSH access, configure a firewall, remove unused packages, and apply security updates. I would also create named users, control sudo access, enable logging, and install monitoring.

For production, I would also check file permissions, rotate logs, configure backups, and document the server setup.

### Question 8

Your Kubernetes cluster uses containerd, but developers build images locally with Docker. Explain the difference between Docker, containerd, and CRI-O in this workflow.

Docker is a container platform used to build and run containers. containerd is a lower-level container runtime that manages container lifecycle. CRI-O is a container runtime designed for Kubernetes.

Kubernetes uses the Container Runtime Interface to talk to runtimes like containerd and CRI-O.

### Question 9

You need to configure Nginx, users, packages, SSH settings, and monitoring agents across 30 servers. Tell me why you would use Ansible instead of manually configuring each server.

Ansible makes server configuration repeatable and automated. Instead of logging into many servers manually, I can define tasks in playbooks and run them consistently across servers.

This reduces human error, saves time, and makes it easier to rebuild or update infrastructure.

### Question 10

A developer pushes a new container image and you update a Kubernetes Deployment from version `v1` to `v2`. Explain what Kubernetes does behind the scenes during that rollout.

When you create a Deployment, Kubernetes creates a ReplicaSet, and the ReplicaSet creates the required Pods. The Deployment keeps the desired number of replicas running.

If a Pod fails, Kubernetes creates a replacement. If the image or configuration changes, the Deployment can perform a rolling update.

### Question 11

Your app has multiple Pods that change IP addresses, and users need to reach it through `api.example.com`. Explain how a Kubernetes Service and Ingress work together in this setup.

A Service exposes Pods inside or outside the cluster using a stable name and IP. It helps route traffic to the correct Pods even when Pods are replaced.

An Ingress manages HTTP and HTTPS routing from outside the cluster to Services. It is commonly used with an ingress controller like Nginx Ingress, Traefik, or AWS Load Balancer Controller.

### Question 12

You are deploying both an HTTPS web app and a TCP-based internal service. Discuss when you would choose an Application Load Balancer and when you would choose a Network Load Balancer.

An Application Load Balancer works at layer 7 and understands HTTP and HTTPS. It can route traffic based on hostnames, paths, headers, and other application-level rules.

A Network Load Balancer works at layer 4 and handles TCP or UDP traffic. It is useful for high performance, static IP needs, and non-HTTP workloads.

### Question 13

Your company has several microservices exposing APIs to mobile apps, partners, and internal teams. Explain how an API Gateway would help manage this traffic.

An API Gateway sits in front of backend APIs and controls how clients access them. It can handle authentication, authorization, routing, rate limiting, logging, and request transformation.

It is useful when many services expose APIs and the team needs one controlled entry point.

### Question 14

Your deployment pipeline needs database passwords, cloud credentials, and API tokens. Tell me how you would manage these secrets without exposing them in Git, logs, or Docker images.

Secrets should be stored in a secure secrets manager or the CI/CD platform's protected secret storage. They should not be committed to Git or printed in pipeline logs.

Access should be limited to the jobs and environments that need them. Secrets should also be rotated and audited regularly.

### Question 15

Your team wants every merge to be tested and ready for production, but management still wants approval before release. Explain the difference between continuous delivery and continuous deployment in this situation.

Continuous delivery means code is automatically built, tested, and prepared for release, but production deployment may still require manual approval.

Continuous deployment means every successful change can be deployed to production automatically without manual approval.

### Question 16

You are asked to design a production pipeline for a customer-facing application where downtime is not acceptable. Walk me through the stages, checks, approvals, and rollback strategy you would include.

I would include build, test, security scan, artifact creation, approval, deployment, health check, and rollback steps. I would deploy the same tested artifact across environments.

For production, I would use strategies like rolling deployment, blue-green deployment, or canary deployment depending on the application risk.

I would also include database migration checks, smoke tests, deployment notifications, release notes, and post-deployment monitoring for error rate, latency, CPU, memory, and business-critical endpoints.

### Question 17

Users report that checkout is slow, but there is no clear error. Explain how logs, metrics, and traces would help you investigate the issue across the application stack.

Logs are event records that explain what happened. Metrics are numeric measurements over time, such as CPU usage or request count. Traces follow a request across multiple services.

Together, they help engineers understand system behavior, debug issues, and monitor production health.

### Question 18

Your monthly cloud bill increased sharply after several new environments were created. Explain how you would investigate and reduce cost without breaking production reliability.

Cost optimization means reducing unnecessary spending while keeping performance and reliability. Examples include right-sizing servers, deleting unused resources, using autoscaling, and applying storage lifecycle policies.

It also includes tagging resources, setting budgets, and reviewing usage reports regularly.

### Question 19

An engineer accidentally used an admin cloud access key in a script. Discuss how IAM should be designed to reduce the risk from this kind of mistake.

IAM controls who can access cloud resources and what actions they can perform. It uses users, groups, roles, policies, and service accounts.

Good IAM practice means using least privilege, enabling MFA, avoiding long-lived credentials, and reviewing access regularly.

### Question 20

Three engineers are using Terraform to manage the same cloud environment. Explain why remote state and state locking are important in this team workflow.

Terraform remote state stores the state file in a shared backend such as S3, Azure Storage, Google Cloud Storage, or Terraform Cloud.

It is useful for teams because everyone works with the same state file. With locking enabled, it also prevents two people from applying changes at the same time.

### Question 21

A security group was manually changed in the cloud console, and Terraform no longer matches the real environment. Explain infrastructure drift and tell me how you would detect and correct it.

Infrastructure drift happens when real infrastructure changes outside the IaC code. For example, someone may manually change a security group in the cloud console.

You can detect drift by running `terraform plan`, using cloud configuration tools, or setting up policy and monitoring checks.

### Question 22

Your public web application is receiving suspicious requests that look like SQL injection and bot traffic. Explain how a Web Application Firewall would help and where you would place it.

A Web Application Firewall protects web applications from common web attacks such as SQL injection, cross-site scripting, and malicious requests.

I would use a WAF for public-facing applications, especially APIs, login pages, payment systems, and applications that need stronger security controls.

### Question 23

Your microservices communicate with each other across many namespaces, and the team wants mTLS, retries, and better traffic visibility. Explain how a service mesh could help.

A service mesh manages service-to-service communication in a microservice environment. It can provide mTLS, retries, traffic splitting, observability, and policy enforcement.

A team might use it when microservice communication becomes complex and they need better security, routing, and visibility.

### Question 24

Your team wants every Kubernetes change to be reviewed through pull requests and automatically applied after merge. Explain GitOps and discuss how Argo CD supports this workflow.

GitOps uses Git as the source of truth for deployment configuration. Changes are made through pull requests, reviewed, merged, and then applied to the environment.

Argo CD supports GitOps by watching Git repositories and syncing Kubernetes clusters to match the desired state in Git.

### Question 25

A user request passes through an API gateway, auth service, payment service, and database before failing. Explain how distributed tracing would help you find where the failure happened.

Distributed tracing tracks a request as it moves through multiple services. It shows where time is spent and where failures happen.

It is useful in microservices because one user request may pass through many APIs, databases, queues, and external services.

### Question 26

Your company is moving from a monolith to many independently deployed services. Discuss the operational challenges you expect with microservices.

Microservices can be harder to operate because they require strong networking, monitoring, logging, tracing, CI/CD, and security. Failures can also be harder to debug because requests move across many services.

To manage these challenges, teams need good observability, clear ownership, stable APIs, automation, and incident response processes.

### Question 27

Your homepage is up, but users complain that login and checkout sometimes fail. Explain how synthetic monitoring can detect this kind of problem before users report it.

Synthetic monitoring runs automated checks that simulate real user actions. It can test login pages, APIs, checkout flows, and page load times.

It helps detect problems before users report them.

### Question 28

Your application needs faster read performance and also needs to process background jobs asynchronously. Explain where Redis and RabbitMQ would fit in this design.

Redis is commonly used for caching, sessions, rate limiting, and fast key-value storage. It can also support queues, but caching is one of its strongest use cases.

RabbitMQ is a message broker used for reliable background processing and communication between services.

### Question 29

At 2:00 AM, alerts show the API error rate has jumped from 1% to 40%. Walk me through how you would respond to this production incident.

I would first confirm the impact and severity. Then I would focus on restoring service, communicate with stakeholders, check dashboards and logs, and involve the right people.

After the incident is resolved, I would document the timeline, root cause, and follow-up actions in a postmortem.

### Question 30

A production container image is found to contain a critical OpenSSL vulnerability. Explain why container image scanning is important and where it should happen in the delivery process.

Container image scanning checks images for vulnerable packages, misconfigurations, and security risks. It helps prevent insecure images from reaching production.

Image scanning should run in CI/CD and also in the registry where images are stored.

### Question 31

Your Kubernetes application has Deployments, Services, ConfigMaps, Ingress, and environment-specific values. Explain how Helm would help package and deploy this application.

Helm is a package manager for Kubernetes. It uses charts to define Kubernetes resources and values files to customize deployments.

It is useful because it simplifies installation, upgrades, rollbacks, and configuration management for Kubernetes applications.

### Question 32

Your organization is preparing a Kubernetes cluster for production workloads. Tell me how you would secure the cluster before teams start deploying applications.

I would use RBAC, namespaces, network policies, image scanning, pod security controls, and secrets encryption. I would also restrict cluster access, enable audit logs, and avoid running containers as root.

I would set resource requests and limits, keep the cluster updated, and monitor cluster activity.

### Question 33

A Kubernetes Service exists, but traffic to the service returns connection errors. Walk me through how you would troubleshoot the Service, Pods, endpoints, DNS, and network policies.

I would check the Pod status, Deployment status, Service selector, endpoints, DNS resolution, network policies, and application logs.

Useful commands include `kubectl get pods`, `kubectl describe pod`, `kubectl get svc`, `kubectl get endpoints`, and `kubectl logs`.

I would confirm that the Service selector matches the Pod labels, the target port matches the container port, and endpoints are being created. If DNS is suspected, I would test from another Pod using tools like `nslookup`, `curl`, or a temporary debug container.

### Question 34

Users say the application is available but slow during peak hours. Walk me through how you would troubleshoot high latency across the load balancer, app, database, cache, and network.

I would check metrics for CPU, memory, database performance, network latency, and error rates. I would also inspect logs and traces to find where requests are slowing down.

Common causes include slow database queries, overloaded servers, external dependency issues, poor caching, and network problems.

I would compare latency at each layer: load balancer, application, database, cache, and external APIs. If tracing is available, I would check the slowest span. If the issue happens only at peak time, I would review autoscaling, connection pools, queue depth, and database locks.

### Question 35

Your security team wants all authentication logs, server logs, cloud audit logs, and firewall events in one place. Explain the role of a SIEM tool in this environment.

A SIEM tool collects security logs and events from different systems, detects suspicious activity, and helps with investigations.

It is useful for threat detection, compliance, audit trails, and security incident response.

### Question 36

After a production outage, the service is back online, but leadership wants to know why it happened and how to prevent it. Explain how you would perform Root Cause Analysis.

Root Cause Analysis is the process of finding the real reason an incident happened. It helps the team understand not only what failed, but why it failed.

For example, if an application went down because the disk was full, the deeper cause may be missing log rotation, poor alerting, or lack of storage monitoring. A good RCA should include the incident timeline, impact, root cause, contributing factors, actions taken, and prevention steps.

RCA is important because it helps teams learn from incidents and reduce the chance of the same issue happening again.

### Question 37

Your team keeps handling server patching differently depending on who is on duty. Explain how a Standard Operating Procedure would improve this process and what it should contain.

A Standard Operating Procedure is a documented step-by-step process for performing a repeated task. It helps make operational work consistent and safer.

As a DevOps Engineer, I would use SOPs for deployments, rollback, server patching, access requests, backups, database maintenance, and incident response. A good SOP should include prerequisites, exact steps, validation checks, rollback steps, and the person or team responsible.

### Question 38

A senior engineer who built the deployment process leaves the company, and the remaining team cannot confidently deploy. Discuss how documentation prevents this kind of operational risk.

Documentation is important because DevOps work involves many systems, tools, environments, and teams. Good documentation helps people understand how things work and reduces dependency on one person.

It supports collaboration by making deployment steps, architecture decisions, troubleshooting guides, SOPs, and incident reports available to everyone who needs them. Good documentation also makes onboarding, handover, audits, and incident response easier.

### Question 39

Your company stores backups, logs, images, and reports in object storage, and the bucket is growing quickly. Discuss advanced object storage techniques you would use to manage cost, security, and retention.

Advanced object storage techniques include lifecycle policies, storage classes, cold storage, intelligent tiering, versioning, object lock, encryption, and access logging.

They are important because object storage can grow very large over time. Without proper management, teams can waste money, expose sensitive data, or lose important files. These techniques help improve cost, security, durability, and automation.

### Question 40

Compliance requires the company to keep audit logs for seven years, but the logs are rarely accessed after 90 days. Explain how cold storage fits this use case.

Cold storage is a cheaper storage class for data that is rarely accessed. It is useful for archives, old backups, compliance records, logs, and historical reports.

The tradeoff is that retrieval may take longer or cost more compared to hot storage. I would use cold storage when the data must be kept but does not need to be accessed frequently.

### Question 41

Your team does not know which uploaded files will be accessed often and which will rarely be used. Explain how intelligent tiering can help control storage cost in this situation.

Intelligent tiering automatically moves objects between storage tiers based on how often they are accessed. For example, frequently accessed objects can stay in a hot tier, while rarely accessed objects can move to a cheaper tier.

This is useful when the team does not know the access pattern of the data. It helps reduce cost without manually moving objects.

### Question 42

The storage bill keeps increasing because old logs, reports, and object versions are never cleaned up. Tell me how you would automate object storage cost optimization.

I would create lifecycle rules to move old objects to cheaper storage classes and delete data that is no longer needed. For example, logs can stay in hot storage for 30 days, move to cold storage after 90 days, and be deleted after one year if the retention policy allows it.

I would also enable storage metrics, review access patterns, clean up old object versions, use compression where possible, and set budget alerts for storage growth.

For production buckets, I would also review versioning cost, multipart upload cleanup, replication cost, access logs, encryption settings, and whether intelligent tiering is better than manually choosing storage classes.

### Question 43

A user accidentally overwrites an important file in object storage, and another user deletes a file by mistake. Explain how object versioning helps recover from these incidents.

Object versioning keeps multiple versions of the same object when it is changed or deleted. It helps recover from accidental deletion, overwrite mistakes, and some ransomware scenarios.

However, versioning can increase storage cost, so it should be combined with lifecycle rules that expire old versions when they are no longer needed.

### Question 44

Your team wants to deploy the same Kubernetes application to dev, staging, and production with small configuration differences. Explain why Helm is useful in this scenario.

Helm is a package manager for Kubernetes. It helps package Kubernetes resources into charts so they can be installed, upgraded, reused, and rolled back more easily.

Helm is useful because Kubernetes applications often need many YAML files. Instead of managing all those files manually, Helm allows teams to use templates and values files to deploy applications consistently across environments.

### Question 45

You are asked to package a Kubernetes app so other teams can install it easily. Explain what a Helm chart is and what files you would expect inside it.

A Helm chart is a package that contains the files needed to deploy an application to Kubernetes. It usually includes templates, a `values.yaml` file, chart metadata, and sometimes dependencies.

The templates define Kubernetes resources like Deployments, Services, ConfigMaps, Ingress, and Secrets. The values file allows the same chart to be customized for different environments.

### Question 46

A Helm release upgrade breaks production after a new image tag is deployed. Explain how `helm install`, `helm upgrade`, and `helm rollback` are used across the release lifecycle.

`helm install` deploys a chart for the first time and creates a release. `helm upgrade` updates an existing release with new chart changes or new values.

`helm rollback` returns a release to a previous revision when an upgrade fails or causes problems. This is useful for safer Kubernetes deployments.

### Question 47

Your dev, staging, and production environments use different replica counts, hostnames, image tags, and resource limits. Tell me how you would manage these differences with Helm.

I would use the same Helm chart with different values files for each environment. For example, I can have `values-dev.yaml`, `values-staging.yaml`, and `values-prod.yaml`.

Each file can define environment-specific settings such as replica count, image tag, resource limits, ingress hostnames, and feature flags. This keeps deployments consistent while still allowing controlled differences between environments.

### Question 48

You need to release a risky payment-service change without affecting all users at once. Discuss rolling, blue-green, and canary deployment strategies and which one you would choose.

A rolling deployment updates application instances gradually. It reduces downtime, but if the new version is bad, some users may still be affected during rollout.

A blue-green deployment keeps two environments. One is live, and the other has the new version. Traffic is switched when the new version is ready. Canary deployment releases the new version to a small percentage of users first, then increases traffic if metrics are healthy.

### Question 49

The business wants to promise customers 99.9% availability, while engineering needs internal reliability targets. Explain the difference between SLI, SLO, and SLA in this context.

An SLI is a measurable signal, such as latency, error rate, or availability. An SLO is the target for that signal, such as 99.9% availability.

An SLA is a formal agreement with customers or stakeholders. If the SLA is not met, there may be business or financial consequences.

### Question 50

The database in one region becomes unavailable, and the business asks how much data may be lost and how long recovery will take. Explain RPO and RTO in this disaster recovery scenario.

RPO means Recovery Point Objective. It defines how much data loss is acceptable.

RTO means Recovery Time Objective. It defines how quickly the system must be restored after failure. For example, if RPO is 15 minutes and RTO is 1 hour, the system should lose no more than 15 minutes of data and should be restored within 1 hour.

### Question 51

Your team wants to stop Terraform from creating public databases, unencrypted buckets, or resources without tags. Explain how Policy as Code can enforce these rules.

Policy as Code means writing rules as code so systems can automatically check infrastructure and deployments. It is useful for enforcing security, compliance, tagging, encryption, and access control.

For example, a policy can block Terraform from creating a public database or opening SSH to the whole internet.

### Question 52

A malicious package is discovered in a dependency used by one of your services. Explain software supply chain security and the controls you would add to reduce this risk.

Software supply chain security protects the path from source code to production. It focuses on dependencies, build systems, artifacts, container images, CI/CD pipelines, and deployment credentials.

Good practices include dependency scanning, image scanning, SBOM generation, signed images, protected branches, secret scanning, and traceable artifacts.

### Question 53

Traffic increases during business hours, and some Pods are using more CPU while the cluster also runs out of node capacity. Explain how Horizontal Pod Autoscaler and Cluster Autoscaler work together.

Horizontal Pod Autoscaler increases or decreases the number of Pods based on metrics like CPU, memory, or custom metrics.

Cluster Autoscaler increases or decreases the number of worker nodes when the cluster does not have enough capacity for Pods or when nodes are underused.

### Question 54

You are upgrading Kubernetes nodes, but the application must keep at least two replicas available at all times. Explain how a PodDisruptionBudget helps during this maintenance.

A PodDisruptionBudget defines how many Pods must remain available during voluntary disruptions, such as node maintenance or cluster upgrades.

It helps protect application availability by preventing too many replicas from being taken down at the same time.

### Question 55

An application starts slowly, sometimes becomes unhealthy, and should not receive traffic until it connects to the database. Explain how readiness, liveness, and startup probes solve these problems.

A readiness probe tells Kubernetes when a container is ready to receive traffic. A liveness probe tells Kubernetes when a container should be restarted.

A startup probe is used for applications that take longer to start. It prevents Kubernetes from killing the container too early while it is still starting.

### Question 56

Your staging deployment passed testing, but production rebuilt a different artifact and introduced a bug. Explain how "build once, deploy many" prevents this problem.

It means the same tested artifact should be promoted across environments instead of rebuilding separately for dev, staging, and production.

This improves reliability because the artifact deployed to production is the same one that passed tests and checks in earlier environments.

### Question 57

The on-call team receives hundreds of alerts every week, and many do not require action. Tell me how you would reduce alert fatigue while still catching real incidents.

I would make alerts actionable, remove duplicate alerts, tune thresholds, group related alerts, and alert on user impact instead of every small internal event.

I would also link alerts to runbooks and review noisy alerts after incidents or on a regular schedule.

### Question 58

Before a major product launch, the business expects traffic to triple for several hours. Discuss how load testing, stress testing, and soak testing would help prepare the system.

Load testing checks how the system performs under expected traffic. Stress testing pushes the system beyond expected limits to find the breaking point.

Soak testing runs the system under load for a long period to find memory leaks, resource exhaustion, or performance degradation over time.

### Question 59

A new Kubernetes deployment is stuck because Pods remain in `Pending` state. Walk me through how you would troubleshoot scheduling, resource, storage, and node capacity issues.

I would run `kubectl describe pod` to check events. Common causes include insufficient CPU or memory, missing node selectors, taints without tolerations, unavailable persistent volumes, or scheduling constraints.

I would also check node capacity, resource requests, quotas, and whether the Cluster Autoscaler is working if the cluster should scale automatically.

Useful checks include `kubectl get nodes`, `kubectl describe node`, `kubectl get events`, `kubectl describe quota`, and checking PVC status if the Pod needs storage.

### Question 60

You are releasing a major backend change on Friday, and rollback must be possible if errors increase. Tell me how you would make this production deployment safer.

I would use automated tests, security scans, artifact versioning, approvals, health checks, monitoring, and rollback steps. I would also use a safer deployment strategy such as rolling, blue-green, or canary deployment.

Before production, I would confirm the change was tested in staging, the rollback plan is clear, and the team knows what metrics to watch after release.

For a risky Friday release, I would prefer a canary or blue-green deployment, define success metrics, keep the previous version ready, avoid unrelated changes, and make sure the right people are available during and after deployment.

## Useful Resources

- https://www.udemy.com/course/devopsprojects/learn/lecture/23902712#overview
- https://www.udemy.com/course/learn-kubernetes
- https://andreybyhalenko.medium.com/
  7-github-repositories-that-help-you-become-a-better-devops-engineer-afae85ed9865
- https://github.com/kelseyhightower/kubernetes-the-hard-way
- https://www.techworld-with-nana.com/devops-bootcamp 
- https://www.udemy.com/course/learn-openshift