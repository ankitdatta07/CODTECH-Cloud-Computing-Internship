# CODTECH Cloud Computing Internship - Task 1: Cloud Storage Setup

## Overview

This repository documents the completion of Task 1 for the CODTECH Cloud Computing Internship, focusing on setting up and configuring cloud storage.

**Task Goal:** Create and configure cloud storage on AWS S3 or Google Cloud Storage, delivering a bucket setup with example files uploaded and access permissions configured.

For this task, I chose **Google Cloud Storage (GCS)** due to its robust features and ease of use for beginners.

---

## Task 1: Cloud Storage Setup - Detailed Steps & Deliverables

### 1. Google Cloud Platform (GCP) Account Setup

* Successfully signed up for a Google Cloud Platform account and activated the Free Tier.
* Created a new GCP project to host all resources for this internship.

    * **My GCP Project Name:** `<CODTECH-CloudStorage>` 
### 2. Cloud Storage Bucket Creation

A dedicated bucket was created in Google Cloud Storage to store the example files.

* **Bucket Name:** `< codtech-internship-mybucket-2025>`
* **Location Type:** Region
* **Location:** 'asia-south1 (Mumbai)'
* **Default Storage Class:** Standard
* **Access Control:** Fine-grained (to allow individual object permissions)

**Screenshot 1: Bucket Contents**
https://github.com/ankitdatta07/CODTECH-Cloud-Computing-Internship/blob/main/Task%201.png?raw=true
---

### 3. Uploading Example Files

Several example files were uploaded to the newly created GCS bucket to demonstrate content storage.

**Screenshot 2: Uploaded Files in Bucket**
https://github.com/ankitdatta07/CODTECH-Cloud-Computing-Internship/blob/main/Task%201%20(2).png?raw=true
---

### 4. Configuring Access Permissions

A key part of this task was to configure access permissions. Specifically, one of the uploaded files was made publicly accessible for demonstration purposes.

* **File Made Public:** (e.g., `your-example-document.pdf` or `sample-image.jpg`)
* **Permission Granted:** `allUsers` (Public) with `Storage Object Viewer` role.

**Note on Public Access Prevention:**
During the configuration, I encountered a "Public access prevention enforced" error at the bucket level. To proceed with making an individual object public (as required by the task), I temporarily disabled Public Access Prevention for the bucket. This allowed for fine-grained control over object-level access.

**Screenshot 3: File Permissions (allUsers with Reader Role)**
https://github.com/ankitdatta07/CODTECH-Cloud-Computing-Internship/blob/main/Task%201%20(3).png?raw=true
---

### 5. Verifying Public Access

The public accessibility of the configured file was verified by attempting to open its public URL in an incognito browser window.

* **Public URL of the Example File:** `https://storage.googleapis.com/codtech-internship-mybucket-2025/ilide.info-lux-algo-signals-amp-overlays-61-pr_4fd52ecacecd2db180613801d34f95c0.pdf'

## Conclusion

Task 1, "Cloud Storage Setup," has been successfully completed on Google Cloud Platform. I have demonstrated the creation of a storage bucket, the upload of example files, and the configuration of access permissions, including making a file publicly accessible. All work-related files and documentation are stored in this GitHub repository.# CODTECH-Cloud-Computing-Internship
