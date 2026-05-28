---
title: "AWS Vietnam Community Day in May 2026: perspectives on AI, data, and system architecture"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---
### Event objective

I attended this event to strengthen my understanding of backend architecture, data structure, and the operational side of cloud systems. Because my role in CloudDoc is mainly backend and AWS integration, I wanted to learn how real systems balance AI ideas, metadata quality, scalability, and cost awareness.

### Speaker

The speakers were AWS community practitioners and technical presenters with hands-on experience. I appreciated that they explained architecture as a set of operating decisions instead of presenting services as isolated tools.

### Detailed content

One of the most useful themes for me was the discussion around data quality and context. The speakers made it clear that intelligent systems become weak very quickly when the underlying metadata is inconsistent or poorly structured. This connected directly to CloudDoc because backend fields such as school, subject, uploader, status, and S3 key are not just storage details; they determine whether later search and workflow logic remains reliable.

Another important topic was the separation of system layers. The event showed that stable systems depend on clean boundaries between delivery, application logic, storage, and observability. That idea matched the backend design direction of CloudDoc, especially the decision to keep large-file transfer out of the API server through presigned URLs.

### Experience and reflection

The event helped me stop thinking of backend work as only endpoint development. I started to look more seriously at metadata design, logging needs, operational visibility, and how future features depend on data discipline from the beginning. This gave me a more system-level view of CloudDoc.

### Conclusion

For my backend role, this event was valuable because it connected architecture, data quality, and cloud operations into one clear mindset. It strengthened the way I approached the API and metadata structure in CloudDoc.
