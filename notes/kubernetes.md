Kubernetes is a portable, extensible, open-source platform for managing containerised workloads and services, that facilitates both declarative configuration and automation.

Traditional Deployment
- Ran applications on physical servers
- No way to define resource boundaries -> resource allocation issues
- One application could take up most resources -> other applications underperform.
- Solution could be to run each application on a different physical server, but this does not scale well and resources were underutilised, and it was expensive to maintain many physical servers.

Virtualised Deployment Era
- Allows you to run multiple VMs on a single physical server's CPU. 
- Allows applications to be isolated between VMs and provides a level of security as the information cannot be freely accessed by each other.
- Allows better utilisation of resources in a physical server and allows better scalability because an application can be added or updated easily, reduces hardware cost, and much more. 
- Each VM is a full machine running all the components, including its own operating system, on top of the virtualised hardware.

Container Deployment Era
- Similar to VMs, a container has its own filesystem, share of CPU, memory, process space, and more; But have relaxed isolation properties to share the Operating System among the applicatinos.
- Lightweight compared to VM 
- Decoupled from underlying infrastructure, they are portable across clouds and OS distributions.

Containers have become popular because they provide extra benefits, such as: - Agile application creating and deployment: increased ease and efficiency of container image creation compared to VM image use.
- Continuous development, integration, and deployment: provides for reliable and frequent container image build and deployment with quick and efficient rollbacks (due to image immutability)
- Dev and Ops separation of concerns : create application container images at build/release time rather than deployment time, thereby decoupling applications from infrastructure.
- Observability not only surfaces OS-level information and metrics, but also application health and other signals.
- Environmental consistency across development, testing, and production: Runs the same on a laptop as it does in the cloud.
- Cloud and OS distribution portability: Runs on Ubuntu, RHEL, CoreOS, on-premises, on major public clouds, and anywhere else.
- Application-centric management: Raises the level of abstraction from running an OS on virtual hardware to running an application on an OS using logical resources.
- Loosely coupled, distributed, elastic, liberated micro-services: applications are broken into smaller, independent pieces and can be deployed and managed dynamically – not a monolithic stack running on one big single-purpose machine.
- Resource isolation: predictable application performance.
- Resource utilization: high efficiency and density.

# Why you need kubernetes and what it can do
Containers are a good way to bundle and run your applications. 
In a production environment, you need to manage the containers that run the applications and ensure that there is no downtime.
If a container goes down, another container needs to start.

Kubernetes provides a framework to run distributed systems resiliently. It takes care of scaling and failover for your application, provides deployment patterns, and more. For example Kubernetes can easily manage a canary deployment for your system.

Kubernetes provides:
* Service discovery and load balancing 
* Storage orchestration
* Automated rollouts and rollbacks
* Automatic bin packing
* Self-healing
* Secret and configuration management
