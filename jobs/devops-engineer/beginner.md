# DevOps interview preparation roadmap

## Role

DevOps Engineer

## Experience Level

Beginner

## Key Concepts


## Linux Foundations

- Command line and filesystem navigation
- Users, groups, sudo, and permissions
- Processes, services, and system logs
- Storage, partitions, mounts, and volumes
- Troubleshooting tools: `top`, `df`, `du`, `journalctl`, `dmesg`, `lsof`

## Networking

- IP addresses, subnets, CIDR, gateways, public/private IPs
- DNS, DHCP, NAT, ports, firewalls
- Routers, switches, hubs, and load balancers
- TCP, UDP, HTTP, HTTPS, SSH
- Tools: `ping`, `curl`, `ss`, `ip`, `dig`, `nslookup`, `traceroute`

## Git and GitHub

- Clone, add, commit, pull, push, fetch
- Branches, merges, conflicts, and pull requests
- Forks, code reviews, issues, releases
- Rebase, cherry-pick, stash, revert, reset
- GitHub Actions, secrets, and branch protection

## Servers

- SSH access and server hardening basics
- Package management and systemd services
- Nginx/Apache, reverse proxy, and static hosting
- Domains, DNS records, and SSL/TLS
- Backups, patching, cron, and log rotation

## Security Basics

- SSH keys and secure SSH configuration
- Least privilege, sudo control, and disabled root login
- Firewalls and cloud security rules
- Public/private subnets and basic network isolation
- Secrets, patching, and vulnerability awareness


## Cloud Basics (please pick one among AWS, Azure, GCP)

### AWS

- EC2, S3, IAM
- VPC, subnets, route tables
- Internet Gateway, NAT Gateway
- Security Groups, EBS, EFS
- ELB/ALB, Auto Scaling, CloudWatch

### Azure

- Virtual Machines, Blob Storage
- Microsoft Entra ID
- Virtual Network, subnets, routes
- Network Security Groups, Managed Disks
- Load Balancer, VM Scale Sets, Azure Monitor

### GCP

- Compute Engine, Cloud Storage, IAM
- VPC Network, subnets, routes
- Firewall Rules, Persistent Disk
- Cloud Load Balancing
- Managed Instance Groups, Cloud Monitoring

## CI/CD

- Continuous integration, delivery, and deployment
- Build, test, scan, deploy, rollback
- Pick One: GitHub Actions, Jenkins, GitLab CI
- YAML workflows, secrets, artifacts, approvals
- Deploying to Linux servers

## Infrastructure as Code

- Terraform providers, resources, variables, outputs
- State files and remote state basics
- `init`, `validate`, `plan`, `apply`, `destroy`
- Provision VMs, networks, disks, and firewalls
- Modules and reusable infrastructure patterns

## Monitoring and Logging

- Metrics, logs, traces, alerts, dashboards
- CPU, memory, disk, network, uptime
- Prometheus, Grafana, and cloud monitoring tools
- System logs, application logs, access/error logs
- Troubleshooting service, resource, and network issues


## Interview Projects

- Admin a Linux server with users, groups, sudo, and storage
- Host a site with Nginx/Apache, DNS, SSL, and logs
- Use GitHub workflow: fork, PR, rebase, cherry-pick
- Deploy a cloud VM with firewall, disk, and monitoring
- Provision infrastructure with Terraform
- Build a CI/CD pipeline that deploys to a server




## Common Interview Questions

### Question 1

What is the difference between continuous integration and continuous deployment?

Continuous integration means developers regularly merge code into a shared repository, and automated checks such as builds and tests run to catch problems early. Continuous deployment goes further by automatically releasing every successful change to production or another target environment.

In simple terms, CI checks that the code is good. CD delivers or deploys the code.

### Question 2

Explain how Terraform tracks the state of infrastructure?

Terraform uses a state file to record the resources it manages and their current configuration. When you run `terraform plan`, Terraform compares the desired configuration in your `.tf` files with the state file and the real infrastructure provider.

This helps Terraform know what to create, update, or delete. For teams, the state file should usually be stored remotely, for example in S3 with locking, so people do not overwrite each other's changes.

### Question 3

Using Bash or Python scripting, how can you deploy a static website to three Linux machines at the same time?

I would package the static website files, then use a script to copy them to each server with `scp` or `rsync`. After copying the files, the script can restart or reload Nginx on each server using SSH.

For example, a Bash script can loop through a list of server IPs and run the same deployment command on each one. I would also check that each deployment completed successfully before marking the task as done.

### Question 4

A developer comes to you with an application they want you to deploy. What questions would you ask before proceeding?

I would ask what language or framework the application uses, how it is built, how it is started, and which port it listens on. I would also ask about required environment variables, secrets, databases, external services, and expected traffic.

I would confirm whether the application needs a domain, SSL, background workers, file storage, monitoring, logging, and a rollback plan. These details help avoid deployment mistakes.

### Question 5

Explain the concept of NAT in servers using real-world scenarios?

NAT means Network Address Translation. It allows devices with private IP addresses to communicate with the internet using a public IP address.

For example, servers in a private subnet may not have public IP addresses. They can still download updates from the internet through a NAT Gateway. NAT is useful because it allows outbound internet access while keeping the servers hidden from direct public access.

### Question 6

In Git, what do you understand by cherry-pick, and when is it useful?

`git cherry-pick` is used to apply a specific commit from one branch into another branch. It is useful when you need one fix or feature from another branch without merging the whole branch.

For example, if a bug fix was committed to a development branch and production needs only that fix, you can cherry-pick the commit into the production branch.

### Question 7

As a Junior DevOps Engineer, you try to connect to a website or app on the internet, but the request times out. What steps would you take to trace the issue?

I would first check if my own internet connection works. Then I would test DNS with `dig` or `nslookup`, test reachability with `ping`, and trace the network path with `traceroute`.

Next, I would use `curl` to check the HTTP response and confirm whether the correct port is open. On the server side, I would check firewall rules, cloud security groups, load balancer health checks, and application logs.

### Question 8

What command can you use to check the size of a folder, for example `/var/log/`?

The command is:

```bash
du -sh /var/log/
```

`du` checks disk usage, `-s` summarizes the total, and `-h` shows the size in a human-readable format.

### Question 9

What command can you use to check running processes and how much resources they are using in Linux?

You can use:

```bash
top
```

For a more interactive view, you can use `htop` if it is installed. You can also use `ps aux` to list running processes with CPU and memory usage.

### Question 10

In networking, what is IP subnetting? If an IP range has a CIDR of `/16`, how many IP addresses are available?

IP subnetting is the process of dividing a network into smaller networks. It helps organize IP addresses, improve security, and control traffic.

A `/16` network has 65,536 total IP addresses because it leaves 16 bits for host addresses. In many cloud providers, some addresses are reserved, so the usable number may be slightly lower.

### Question 11

What is the purpose of netstat?

`netstat` is used to view network connections, listening ports, and routing information. It helps you check which services are listening and which remote systems are connected.

On newer Linux systems, `ss` is often used instead of `netstat`.

### Question 12

What are the four golden signals of monitoring?

The four golden signals are latency, traffic, errors, and saturation.

Latency shows how long requests take. Traffic shows how much demand the system is receiving. Errors show failed requests. Saturation shows how close the system is to reaching its resource limits.

### Question 13

A developer says their application is failing to start on a server you provisioned. What steps would you take to resolve the issue?

I would first check the service status using `systemctl status` if it is managed by systemd. Then I would check logs using `journalctl` or the application's log files.

I would confirm that the correct runtime, dependencies, environment variables, permissions, and ports are configured. I would also check disk space, memory, and whether another process is already using the required port.

### Question 14

What is the difference between TCP and UDP, and what are their common use cases?

TCP is connection-oriented and reliable. It confirms delivery, orders packets correctly, and retransmits lost data. It is used for HTTP, HTTPS, SSH, and databases.

UDP is faster but does not guarantee delivery or ordering. It is used for DNS, video streaming, gaming, and VoIP. TCP and UDP are not secure by themselves; security usually comes from encryption protocols like TLS, SSH, or VPNs.

### Question 15

As a Junior DevOps Engineer, what is SSH, and how can it be used securely?

SSH is a secure protocol used to connect to remote servers. It allows administrators to run commands, manage files, and troubleshoot systems remotely.

To use SSH securely, I would use SSH keys instead of passwords, disable root login, restrict access to trusted users, use least privilege, and limit SSH access with firewall or security group rules.


### Question 16

A user on a server you provisioned has done a lot of work. You want to know what commands they have been using. What command would you use?

I would check the user's shell history file or use the `history` command when logged in as that user.

Common files include:

```bash
~/.bash_history
~/.zsh_history
```

For stronger auditing, command history alone is not enough. It is better to use proper logging and auditing tools such as `auditd`.

### Question 17

What is the difference between Docker and virtual machines?

Docker containers share the host operating system kernel and package applications with their dependencies. They are lightweight and start quickly.

Virtual machines include a full guest operating system and run on a hypervisor. They provide stronger isolation but use more resources than containers.

### Question 18

As a Junior DevOps Engineer, how would you secure Docker containers?

I would avoid running containers as root, use trusted and minimal images, scan images for vulnerabilities, and keep images updated. I would also avoid putting secrets directly inside images or Dockerfiles.

I would limit container permissions, expose only required ports, use read-only filesystems where possible, and remove unused images and containers.

### Question 19

If you want to spin up multiple Docker containers, how would you do it?

For a small setup, I would use Docker Compose. I would define all services, networks, volumes, ports, and environment variables in a `docker-compose.yml` file.

Then I would start the containers with:

```bash
docker compose up -d
```

For production at scale, I would consider orchestration tools like Kubernetes.

### Question 20

What is a Docker volume, why is it important, and when would you use it?

A Docker volume is used to persist data outside the container's lifecycle. This is important because container data can be lost when a container is removed.

Volumes are useful for databases, uploaded files, logs, and any data that must survive container restarts or replacements.

### Question 21

What is reverse proxy?

A reverse proxy sits in front of application servers and forwards client requests to the correct backend service. It can also handle SSL termination, routing, caching, compression, and load balancing.

### Question 22

As a Junior DevOps Engineer, you provisioned a server and created separate users for three developers working on different applications. How can you track who is accessing what, when, and why?

I would make sure each developer has a separate user account and does not share credentials. I would check SSH logs, command history, sudo logs, and application logs.

Since they cannot access root, any installation request should go through an approved process. For better tracking, I would use audit logs, `sudo` logging, and clear documentation for changes made on the server.

### Question 23

What do you understand by DHCP, and what are its key uses in networking?

DHCP means Dynamic Host Configuration Protocol. It automatically assigns IP addresses and network settings to devices.

DHCP helps devices get an IP address, subnet mask, gateway, and DNS server without manual configuration. It is useful in networks where many devices connect and disconnect regularly.

### Question 24

You are tasked with cleaning up an application log file that takes up a lot of space every five days. What is the best way to clean up these logs?

The best approach is log rotation. In Linux, I would use `logrotate` to rotate, compress, and delete old logs based on size or age.

If a custom cleanup is needed, I could create a script and schedule it with cron. However, I would avoid simply deleting active log files because the application may still be writing to them.


### Question 25

Explain the concept of blobs and trees in Git, and how they are used?

A blob stores the content of a file in Git. A tree stores directory structure and references to blobs or other trees.

Together, blobs and trees help Git represent the exact state of a project at a point in time. Commits then point to trees and include metadata like author, message, and parent commit.

### Question 26

What is Infrastructure as Code?

Infrastructure as Code means managing infrastructure using code instead of manual setup. Tools like Terraform allow you to define servers, networks, storage, and firewalls in configuration files.

This makes infrastructure easier to repeat, review, version, and automate.

### Question 27

What is the difference between a public IP address and a private IP address?

A public IP address is reachable over the internet. A private IP address is used inside a private network and is not directly reachable from the internet.

For example, a load balancer may have a public IP, while backend application servers may only have private IPs inside a VPC or virtual network.

### Question 28

A developer has asked for their simple web application to be highly available in the cloud. What approach would you take?

I would deploy the application across multiple instances in different availability zones. Then I would place a load balancer in front of the instances to distribute traffic.

I would also configure health checks, auto scaling, monitoring, alerts, backups, and a proper deployment process. This reduces downtime if one instance or zone has a problem.

### Question 29

You deployed an application that listens on port `8000`, but you cannot access it from the browser. How would you troubleshoot this?

I would first confirm that the application is running and listening on port `8000` using `ss -tuln` or `curl localhost:8000` on the server.

Then I would check the firewall and cloud security group to make sure port `8000` is open if it should be publicly accessible. I would also confirm the app is binding to `0.0.0.0` and not only `127.0.0.1`.

If the app is behind Nginx, I would check the reverse proxy configuration and Nginx logs.

### Question 30

As a Junior DevOps Engineer, you want to know when your server CPU is above 80%. What steps would you take to receive an alert?

I would install or enable monitoring for the server using a tool like CloudWatch, Azure Monitor, Google Cloud Monitoring, Prometheus, or Grafana Alerting.

Then I would create an alert rule that checks CPU usage and triggers when it stays above 80% for a defined period. I would configure notifications through email, Slack, Teams, or another alert channel.

### Question 31

What is the difference between a managed database and a bare-metal database?

A managed database is operated by a cloud provider or platform. The provider handles tasks like backups, patching, replication, monitoring, and scaling.

A bare-metal or self-managed database is installed and managed directly on a server. You are responsible for setup, security, backups, patching, performance, and recovery.

### Question 32

In the cloud, what is object storage, and what benefits does it provide?

Object storage stores data as objects inside buckets or containers. Examples include Amazon S3, Azure Blob Storage, and Google Cloud Storage.

It is useful for backups, static files, logs, images, videos, and application assets. Benefits include durability, scalability, high availability, and lower cost for large amounts of unstructured data.

### Question 33

What is a load balancer?

A load balancer distributes traffic across multiple servers or application instances. It improves availability and performance by making sure one server does not handle all traffic.

It can also perform health checks and stop sending traffic to unhealthy instances.

### Question 34

A developer asks you to increase the CPU and memory of their server. What type of scaling is this?

This is vertical scaling. Vertical scaling means increasing the resources of an existing server, such as CPU, memory, or disk.

Horizontal scaling means adding more servers or instances instead.

### Question 35

Using Terraform, how would you spin up a VM in the cloud? Use AWS, Azure, or GCP as an example.

Using AWS as an example, I would first configure the AWS provider, then define resources such as a VPC or subnet, security group, key pair, and EC2 instance.

After writing the Terraform files, I would run:

```bash
terraform init
terraform validate
terraform plan
terraform apply
```

After deployment, I would confirm the VM was created and that access rules are correct.

### Question 36

What is a web server? Give examples and explain how web servers help in deployment.

A web server receives HTTP or HTTPS requests and serves web content or forwards requests to an application. Examples include Nginx, Apache, and Caddy.

In deployment, a web server can serve static files, act as a reverse proxy, handle SSL, route traffic, and improve security.

### Question 37

If Git is a version control tool, what are GitHub, GitLab, and Bitbucket, and how do they differ?

Git is the tool used to track code changes. GitHub, GitLab, and Bitbucket are platforms that host Git repositories and provide collaboration features.

They provide features like pull requests, code review, issues, CI/CD, permissions, and project management. GitLab has strong built-in CI/CD, GitHub is widely used with GitHub Actions, and Bitbucket is often used with Atlassian tools like Jira.

### Question 38

A developer mistakenly deleted their commits. As a Junior DevOps Engineer, how can you help them find and restore the commits?

I would first check `git reflog` because it records where HEAD and branches recently pointed. If the commit is still available, I can create a new branch from it or reset the branch back to it.

For example:

```bash
git reflog
git checkout -b recovered-branch <commit-hash>
```

If the commit was pushed before, I would also check the remote repository.

### Question 39

What is a multi-stage build in Docker, and what are its benefits?

A multi-stage build uses more than one `FROM` statement in a Dockerfile. One stage can build the application, and another smaller stage can run it.

The benefit is that the final image is smaller, cleaner, and more secure because build tools and temporary files are not included in the runtime image.

### Question 40

What are snapshots in the cloud, and what are they used for?

Snapshots are point-in-time copies of disks, volumes, or instances. They are used for backups, recovery, migrations, and creating new servers from an existing state.

Before patching or making risky changes, snapshots can help restore a system if something goes wrong.

### Question 41

What command can you use to delete Docker images?

To delete one Docker image, use:

```bash
docker rmi <image-id>
```

To remove unused images, use:

```bash
docker image prune
```

To remove all unused images, not just dangling ones, use:

```bash
docker image prune -a
```

### Question 42

You have been tasked with patching servers that run critical applications. What steps would you take to reduce the risk of downtime?

I would first check the patch notes and understand what services may be affected. Then I would take backups or snapshots and confirm that rollback steps are available.

I would test the patches in a staging environment before production. For production, I would patch during a maintenance window or use a rolling update approach so not all servers are patched at once. After patching, I would verify the application, logs, metrics, and alerts.

### Question 43

Why is documentation important, and how does it support collaboration?

Documentation helps teams understand systems, processes, decisions, and troubleshooting steps. It reduces confusion and makes work easier to repeat.

Good documentation helps new team members onboard faster, supports handovers, and makes it easier for developers, operations, and security teams to work together.

### Question 44

In your own words, what is DevOps, and how does it bridge the gap between developers and operations teams?

DevOps is a way of working that improves collaboration between development and operations teams. It focuses on automation, communication, monitoring, and faster delivery of reliable software.

DevOps bridges the gap by helping developers understand deployment and operations concerns, while helping operations teams support faster and safer software releases.

### Question 45

If Grafana is used for visualizing logs and metrics, what is Prometheus known for?

Prometheus is known for collecting, storing, and querying metrics. It scrapes metrics from applications and servers, stores them as time-series data, and supports alerting.

Grafana is commonly used to visualize Prometheus metrics in dashboards.

### Question 46

In Linux, what is `sudo`?

`sudo` allows a permitted user to run commands with elevated privileges, usually as the root user. It is useful because users do not need to log in directly as root to perform administrative tasks.

Access to `sudo` should be controlled carefully using the sudoers configuration.

### Question 47

As a Junior DevOps Engineer, what is the difference between on-premises servers and cloud servers?

On-premises servers are physical servers owned and managed by an organization in its own data center or office. The organization is responsible for hardware, power, networking, maintenance, and scaling.

Cloud servers are virtual servers provided by cloud platforms like AWS, Azure, or GCP. They are easier to provision, scale, and replace, and the cloud provider manages the underlying physical infrastructure.



## Practical Tips

- Pick one cloud provider first, preferably AWS if you are unsure. Learn EC2, S3, IAM, VPC, Security Groups,   
  ALB, Auto Scaling, and CloudWatch well before touching Azure/GCP.

- Build everything around small real projects, not just notes. For example: create a Linux VM, SSH into it, 
  install Nginx, host a static site,point a domain/subdomain to it, add SSL, and check logs.

- For Linux, practice troubleshooting daily with commands like systemctl, journalctl, df -h, du -sh, top,   
  ss-tuln, lsof, and dmesg. Interviewers often care more about how you debug than how much theory you know.

- For networking, make sure you can explain clearly: “What happens when I visit a website?” Include DNS, IP,  
  TCP/TLS, HTTP/HTTPS, ports, firewall rules, and load balancers.

- For Git, do not only learn commands. Practice recovering from mistakes: merge conflict, wrong commit, undo 
  local changes, revert a pushed commit, rebase a branch, and open a pull request.

- For CI/CD, start with GitHub Actions since you already mention GitHub. Build one pipeline that runs tests, 
  builds an artifact, then deploys to a Linux server over SSH.

- For Terraform, avoid jumping into modules too early. First get comfortable with init, validate, plan, apply, 
  variables, outputs, and state. Then create a VM, security group/firewall rule, disk, and basic monitoring.

- For security, be ready to explain practical basics: SSH keys, disabling root login, least privilege, secrets 
  in CI/CD, security groups/firewalls, patching, and why public databases are dangerous.

- For monitoring, learn the difference between metrics, logs, traces, and alerts. Be able to say what you would 
  check if a site is slow, down, or returning 502/503 errors.

- Turn your “Interview Projects” section into your main portfolio. For each project, write a short README with 
  architecture, tools used, screenshots, commands, problems faced, and how you fixed them.
  
- In interviews, answer like an operator: state what you would check first, what command/tool you would use, 
  what result you expect, and what action you would take next.

## Useful Resources

- https://www.udemy.com/course/devopsprereqs/learn/lecture/28359136#overview
- https://www.youtube.com/watch?v=Ou9j73aWgyE&list=PLdpzxOOAlwvIKMhk8WhzN1pYoJ1YU8Csa&pp=0gcJCeECOCosWNin
- https://roadmap.sh/devops
- https://github.com/trimstray/the-book-of-secret-knowledge
- https://www.udemy.com/course/linux-networking
- https://github.com/ivanarandac/Free-DevOps-Books-1
