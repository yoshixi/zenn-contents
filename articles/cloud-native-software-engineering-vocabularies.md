---
title: ""
emoji: "🕌"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: []
published: false
---

Cloud Architectures
Redundancy
Redundancy refers to the duplication of critical components or functions of a system to increase its reliability. In the cloud architecture context, redundancy often means having backup resources or solutions to ensure continuous functionality even when primary resources fail.

Idempotence
Idempotence refers to the property of certain operations where performing them multiple times has the same effect as performing them once. In cloud environments, idempotent operations help in preventing unintended side effects, especially in distributed systems where the same command might be retried multiple times due to network failures.

Availability
Availability pertains to the uptime of a system or service. In cloud architectures, high availability is often a goal, ensuring that services are accessible and operational most of the time, if not all the time.

Database Replication/Shadowing
This is a technique where a database's content is duplicated onto one or more systems. Replication ensures that a backup of the data exists and can enhance availability. Shadowing, on the other hand, usually involves maintaining a nearly real-time copy of the data for redundancy or load-balancing purposes.

Transparent
In the cloud context, transparency often refers to the seamless operation of a service or process without the end-user needing to be aware of the complexities underlying it.

Consistency
Consistency ensures that all copies of the data reflect the same version across distributed systems. It's a vital attribute in distributed databases, ensuring that all nodes provide the same data view.

Observability
Observability in cloud systems refers to the ability to understand and diagnose the internal state of a system or service just by observing its outputs. Tools and practices for observability include logging, monitoring, and tracing.

Trace
In cloud environments, tracing allows tracking of requests as they navigate through various microservices or components. This aids in debugging and performance optimization.

APM
APM stands for Application Performance Monitoring/Management. It's a toolset used to monitor and manage the performance and availability of software applications, providing insights into how applications are performing in real-time.

Microservices
Microservices is an architectural style that structures an application as a collection of loosely coupled, independently deployable services. Each service runs a specific process and communicates via a well-defined API.

Serverless
Serverless is a cloud-computing model that allows developers to build and run applications without managing server infrastructures. Providers automatically manage server provisioning and scaling, charging only for the compute time consumed.

Containers
Containers are lightweight, standalone executable software packages that include everything needed to run a piece of software, including code, runtime, system tools, and libraries. They ensure consistency across multiple environments.

Immutable Infrastructure
This concept involves provisioning and replacing components instead of updating them. In a cloud environment, new instances replace outdated or faulty ones, ensuring stability and reducing inconsistencies.

Scalability
Scalability refers to the capability of a cloud system, process, or network to handle growth or decrease in workload. It can be either vertical (adding resources) or horizontal (adding more instances).

Infrastructure as Code (IaC)
IaC is the practice of managing and provisioning computing resources using machine-readable definition files, rather than hardware configurations or interactive configuration tools.

CI/CD
Continuous Integration and Continuous Deployment (CI/CD) is a practice that integrates code changes continuously, automatically tests them, and deploys them into production.

Elasticity
Elasticity is the ability of cloud systems to scale resources both up and down as needed. It's about the efficient allocation and deallocation of resources dynamically based on demand.

Software programming
Redundant
In software programming, redundancy refers to unnecessary code or functionality that doesn't add value to the application. It's considered a bad practice as it can introduce bugs and makes the code harder to maintain.

Overhead
Overhead in software refers to the additional computational work or resource allocation that's necessary to implement a specific operation or function. It's often a trade-off between performance and functionality.

Latency
Latency is the time taken to process a request or the delay between the request and response. In software systems, minimizing latency is essential for ensuring fast and responsive applications.

ACID
Stands for Atomicity, Consistency, Isolation, and Durability. It's a set of properties that ensure reliable processing of database transactions. In essence, ACID ensures that all database transactions are processed reliably.

Concurrency
Concurrency in software programming refers to the simultaneous execution of sequences or units of code. Managing concurrency is crucial in multi-threaded or distributed systems to prevent conflicts or resource contention.

RESTful APIs
Representational State Transfer (REST) is an architectural style for designing networked applications. A RESTful API uses HTTP requests to perform CRUD operations on data.

Garbage Collection
It's a form of automatic memory management. The garbage collector attempts to reclaim memory that's no longer in use by the program, ensuring efficient memory utilization.

JIT Compilation
Just-In-Time (JIT) Compilation is a technique where bytecode is compiled into native machine code just before execution, aiming to improve performance.

Refactoring
Refactoring is the process of restructuring existing computer code without changing its external behavior. The goal is to improve the code's structure, making it cleaner and more maintainable.

Dependency Injection
Dependency Injection (DI) is a design pattern where an object's dependencies are "injected" or passed to it, rather than the object creating them. It aids in decoupling software components, making the system more modular.

SDK
Software Development Kit (SDK) is a set of tools, libraries, documentation, and sample code that developers use to create applications for a specific platform or framework.

Agile
Agile is a set of principles for software development where requirements and solutions evolve through collaborative efforts. It promotes adaptive planning, evolutionary development, and early delivery.