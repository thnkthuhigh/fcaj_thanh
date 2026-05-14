---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
## CloudDoc Platform for HUTECH Students
## A backend-oriented direction for a cloud-based academic document platform

### 1. Executive summary
CloudDoc was shaped from a very practical problem: students have many study materials, but they still lack a single place where documents can be stored, found, and trusted in a structured way. When files are scattered across personal drives, chat groups, or temporary folders, users waste time searching, while the system itself has no clean data foundation for future growth.

As the backend contributor in this project, I do not see CloudDoc as a simple file upload website. The more important challenge is how the backend can handle document flows in a clean, secure, and scalable way. Files should be stored in the right layer, metadata must remain structured, and APIs should be consistent enough for the frontend to integrate without turning the application server into a bottleneck.

### 2. Problem statement
From a technical perspective, the key issue is not just whether users can upload files. The real issue is how the system manages the full lifecycle of a document after upload. Once a learning platform starts serving many subjects, many users, and many similar files, poor metadata quickly leads to weak search quality, difficult moderation, and a messy repository.

Another important concern is the upload architecture itself. If the backend receives entire files and then forwards them to storage, the application server takes unnecessary I/O load. That pattern may work for a small demo, but it becomes inefficient when document volume grows, especially for larger PDFs, DOCX files, or slide decks. Because of that, CloudDoc needs a structure where the backend focuses on business logic and data, while object storage handles file persistence.

**Proposed solution**

The core idea is to clearly separate four responsibilities: user interface, business API, metadata storage, and file storage. This gives each layer a precise role:

- The frontend handles user interaction, document forms, and API calls.
- The Node.js/Express backend validates input, creates `s3_key` values, generates presigned URLs, stores metadata, and returns results to the UI.
- PostgreSQL acts as the structured source of truth for fields such as title, subject, department, file type, uploader, moderation status, and download count.
- Amazon S3 stores the original files so the backend does not need to act as a raw file transfer layer.

The most important part of this design is that the backend does not carry the entire upload path in the traditional way. Instead, it coordinates the process while the actual file upload is delegated to S3 through presigned URLs. That decision is a better fit for CloudDoc because it reduces EC2 load while keeping the data layer consistent.

### 3. Solution architecture
The diagram below presents CloudDoc as a multi-layer AWS architecture in which content delivery, application logic, data storage, and observability are clearly separated:

![CloudDoc AWS Architecture](/fcaj_thanh/images/2-Proposal/aws-drawio-cloudoc.png)

In this model, CloudFront and static S3 serve the frontend; ALB receives external traffic; EC2 runs the Express backend; RDS PostgreSQL stores document metadata; S3 upload keeps original files; and SQS, CloudWatch, SNS, and Glacier support asynchronous processing, monitoring, alerting, and long-term storage optimization.

I chose this architecture because it matches how a backend should support a real document platform: not by forcing everything through one server, not by mixing files with business data, and not by ignoring future needs such as moderation, observability, or background jobs.

### 4. Technical implementation
The internship scope is not to deliver a fully production-ready platform from day one. The realistic goal is to complete a working core flow that matches the existing CloudDoc codebase. Because of that, the practical priorities are:

- Building backend APIs for health checks, document listing, document details, creation, status updates, and presigned upload/download flows.
- Designing PostgreSQL structures that keep metadata queryable and extensible.
- Enabling direct upload to S3 so the application server does not process binary file streams.
- Validating input carefully and keeping the flow between frontend, backend, and storage clean.

Services such as SQS, CloudWatch, SNS, and Glacier are therefore presented as justified architectural directions rather than falsely claimed as fully completed production features. I intentionally keep that boundary clear so the report stays honest about what was truly implemented.

### 5. Roadmap and milestones
**Phase 1: Complete the backend core**

- Stabilize document APIs, health checks, and metadata flow.
- Finalize PostgreSQL structures and moderation state management.
- Support clean frontend integration for the main endpoints.

**Phase 2: Real cloud integration**

- Complete direct-to-S3 upload through presigned URLs.
- Standardize environment setup and IAM Role usage for the backend.
- Validate the upload, moderation, and access flow end-to-end.

**Phase 3: Expansion and operations**

- Add background processing for heavier or asynchronous tasks.
- Improve logging, monitoring, and alerting with CloudWatch and SNS.
- Optimize storage cost through lifecycle rules and data tiering.

### 6. Budget estimate
The image below shows the estimated monthly AWS cost for the near-production CloudDoc architecture, exported from AWS Pricing Calculator on **June 17, 2026**:

![CloudDoc AWS Monthly Cost](/fcaj_thanh/images/2-Proposal/aws-monthly-cost-cloudoc.jpg)

| Item | Estimated monthly cost (USD) | Note |
| --- | ---: | --- |
| RDS PostgreSQL Multi-AZ | 85.50 | Largest cost due to high availability and stronger data protection |
| EC2 Server (t4g.micro x2) | 19.51 | Two backend application instances across two AZs |
| Application Load Balancer | 18.98 | Shared entry point and traffic distribution |
| NAT Instance (t4g.nano) | 4.64 | Supports outbound traffic for private subnets |
| CloudWatch | 4.01 | Basic logs, metrics, and alarms |
| Others (SNS, CloudFront) | 0.89 | Small but necessary operational services |
| **Total** | **133.53** | Reference cost for the proposed architecture |

From a backend perspective, this is not only a pricing table. It also supports technical decisions. In a dev or demo environment, the team can reduce instance size, use single-AZ where appropriate, stop idle resources, and apply S3 Lifecycle policies to avoid waste. FinOps thinking therefore needs to appear at design time, not only after deployment.

### 7. Risk assessment
I see three main groups of risk. The first is integration mismatch between frontend and backend, especially in the presigned upload flow. A small contract mismatch can break the entire upload experience. The second is poorly structured metadata, where files may exist but remain difficult to search, review, or manage. The third is operational risk related to AWS permissions and unnecessary infrastructure cost.

To reduce those risks, the backend direction should follow several clear rules:

- Validate request payloads before creating document records.
- Use IAM Roles with the Principle of Least Privilege instead of hard-coded access keys in source code or `.env` files.
- Keep files and metadata separated so that moderation, search, and analytics remain manageable.
- Add CloudWatch logs, metrics, and SNS alerts around important system paths.
- Clearly distinguish between implemented features and architectural extensions to avoid overclaiming in the report.

### 8. Expected outcomes
What I want this proposal to show is not just an AWS diagram or a long list of services. More importantly, CloudDoc shows that backend engineering is what keeps the system organized: it keeps data structured, keeps upload flows efficient, keeps security in the conversation, and leaves room for future growth.

For the project, this direction gives CloudDoc a better foundation for future features such as deeper moderation, background processing, content analysis, or smarter search. For me personally, it marks a clear shift from writing APIs screen by screen to thinking about backend design as the stable core of a product that must handle data, operations, and long-term evolution.
