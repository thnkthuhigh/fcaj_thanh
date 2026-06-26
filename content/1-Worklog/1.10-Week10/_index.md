---
title: "Integrating S3 uploads with presigned URLs and completing document business logic"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.10. </b> "
---
### Week 10 Objectives:

* Integrate direct document upload to Amazon S3 through presigned URLs.
* Complete backend business logic for metadata, moderation status, and document download.
* Standardize how frontend and backend cooperate in the real upload/download flow.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Build the `presign-upload` API so the backend can generate temporary S3 upload URLs for the frontend. | 22/06/2026 | 22/06/2026 |  |
| 3 | Implement `s3_key` generation, file-name normalization, and expiration settings for presigned URLs. | 23/06/2026 | 23/06/2026 |  |
| 4 | Complete the API that stores document metadata after the file has been uploaded to S3. | 24/06/2026 | 24/06/2026 |  |
| 5 | Add business logic for moderation status updates and download-count increments. | 25/06/2026 | 25/06/2026 |  |
| 6 | Build the presigned download API and align the end-to-end upload/download flow with the frontend side. | 26/06/2026 | 26/06/2026 |  |

### Week 10 Achievements:

* Completed a direct-to-S3 upload flow that reduces unnecessary load on the backend.
* Expanded the backend business logic for metadata storage, moderation, and document download.
* Improved API consistency between the frontend and backend integration flow.
