# Compute

## Compute Options
Google AppEngine
- Platform as a Service Option
- Serverless
- Ops-free

Google Compute Engine 
- Infra as a Service option
- Fully controllable down to OS

Google Container Engine
- Clusters of machines running K8s and hosting containers
- In between solution


## Google Compute Engine

### Overview
- Google Cloud Launcher helps to deploy a full web serving stack (eg: LAMP stack or WordPress)
- Provides cost estimates
- You can customize architecture eg machine types, disk sizes etc
- You can constumize config, rename instances etc
- You have full control of machine instances
- Loads of storage options such as buckets, persistent disks, ssd, local ssd
- Loads of storage technologies like Cloud SQL
- Load balancing options - L4 lb and L7 LB
- Allows internal load balancing with auto-scaling available
- DevOps options like:
	- Management with ansible etc
	- Automated builds using Jenkins, K8s
	- CI
	- CD

### Additional GCE

#### Image Types
- Public images for Linux and Windows Server that Google provides
- Images for other OSes are also available
- You can import your own custom OS image

#### Creation
- Creator has full root privileges, SSH capability
	- Can share with other users
- While creating instance specify
	- Zone
	- OS
	- Machine type
	
#### Machine Types
- Standard
- High-Memory
- High-CPU
- Shared-core (small, non-resource intensive)
- Can attach GPUs to most machine types

#### Networking in Projects and Instances
- Each instance belongs to a project
- Projects can have any number of instances
- Projects can have upto 5 VPC
- Each instance can only belong to one VPC
- Instances within a VPC communicate on LAN
- Across VPCs, public internet or VPN can be used

#### Preemptible Instances
- Much cheaper than regular compute engine instances
- Might be terminated at any time if CE needs the resources
- Use for fault-tolerant applications
- Definitely terminated after running for 24 hours
- Probability of termination varies by day/zone etc
- Cannot live migrate or auto-restart on maintenance

Pre-emption process:
- Soft off signal
- 30s to clean up
- Mechanical off signal
- Instance sent to terminated state

#### Storage Options
- Each instance comes with a small root persistent disk containing the OS
- Add additional storage options
	- Persistent disks
		- Standard
		- SSD
	- Local SSDs
	- Cloud Storage

## Google Container Engine (GKE)

- Need for DevOps largely mitigated
- Can still use CI/CD tools
- StackDriver for logging and monitoring

### Advantages
- Orchestration because of Kubernetes
- Image registration through container registry
- Flexibility - mix and match with other cloud providers, on-premise
- Autoscaling

### More
- Container disks are ephemeral
- Need to use gcePersistentDisk abstraction for persistent disk
- For HTTP load balancing, need to integrate with Compute Engine load balancing
- Group of compute engine instances running K8s

### Autoscaling
- Automatic resizing of clusters
- Periodically checks whether there are any pods waiting, resizes cluster if needed
- Also monitors usage of nodes and deletes nodes if all its pods can be scheduled elsewhere


## App Engine
- Similar to Heroku or EngineYard
- Can focus on code instead of worrying about DevOps backend stuff
- Serverless

### AppEnging Standard Environment
- Based on container instances running on Google's infra
- Preconfigured with one of several available runtimes (JAVA 7, Python 2.7)
- Each runtime also includes libraries that support App Engine Standard APIs
- Maybe all you need
- Applications run in a secure sandboxed environment
- Your application runs within its own secure reliable environment that is independednt of hardware, OS or physical location of the server

### AppEngine Flexible Environment
- Allows you to customize your runtime and even the OS of your virtual machine using Dockerfiles
- Under the hood, merely instances of Google Compute Engine VMs

### Cloud Functions
- Serverless execution environment for building and connecting cloud services
- Write simple, single-purpose functions
- Attached to events emitted form your cloud infrastructure and services
- Cloud Function is triggered when an event being watched is fired


## Comparison between Compute Options
App Engine | Container Engine | Compute Engine
--- | --- | ---
A flexible zero ops serverless platform for building highly available apps | Logical infra powered by K8s | VMs
If you just want to focus on code and not care about infra | You want to increase velocity and improve operability dramatically by separating the app from the OS | You need complete control over infra and direct access to high-performance hardware such as GPUs and local SSDs
You neither know nor care about the OS running your code | You don't have dependencies on a specific OS | You need to make OS-level changes such as providing tour own network or graphic drivers to squeeze out the last drop of performance
Websires, mobile app and gaming back ends, RESTful APIs, IoT apps | COntainerized workloads, cloud native distributed systems, hybrid applications | Any workload requiring specific OS, currently deployed on-prem software that you want to migrate, can't be containerized easily or needs exiting VM images

- Possible to mix and match the 3 options

## Review 

1) What's the simplest way to host a website on a cloud platform like GCP?

- Just buy some storage (Disk Space)
- Automatic Scaling
- Google Cloud Storage is the best way to host a static site
- Create a cloud storage bucket and upload content
- Can use storage.googleapis.com
- You could write your own HTML CSS or use static generators
- Firebase Hosting + Google Cloud Storage is enough for non-intelligent hosting

2) If you'd like to control load balancing of your web app, would you use SaaS, PaaS or IaaS?

- IaaS

3) What factors would you take into account when you instantiate a compute engine VM?

- Hardware
- CPU
- Hard Disk
- Persistent Memory
- Where is traffic coming from?
- Where can I store my data?

4) What precautions to take if you decide to use a preemptible VM instance?

- A preemptible VM instance is one that Google can take back at any given time
- Fault-tolerant
- Workload cannot be run longer than 24 hrs
- Clean up should be within 30s



5) Which is heavier, a typical VM or a typical container?

- Container

6) Does the AppEngine allow OS config?

- Nope
