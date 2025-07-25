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

### 3. Uploading Example Files

Several example files were uploaded to the newly created GCS bucket to demonstrate content storage.

**Screenshot 2: Uploaded Files in Bucket**
https://github.com/ankitdatta07/CODTECH-Cloud-Computing-Internship/blob/main/Task%201%20(2).png?raw=true


### 4. Configuring Access Permissions

A key part of this task was to configure access permissions. Specifically, one of the uploaded files was made publicly accessible for demonstration purposes.

* **File Made Public:** (e.g., `your-example-document.pdf` or `sample-image.jpg`)
* **Permission Granted:** `allUsers` (Public) with `Storage Object Viewer` role.

**Note on Public Access Prevention:**
During the configuration, I encountered a "Public access prevention enforced" error at the bucket level. To proceed with making an individual object public (as required by the task), I temporarily disabled Public Access Prevention for the bucket. This allowed for fine-grained control over object-level access.

**Screenshot 3: File Permissions (allUsers with Reader Role)**
https://github.com/ankitdatta07/CODTECH-Cloud-Computing-Internship/blob/main/Task%201%20(3).png?raw=true


### 5. Verifying Public Access

The public accessibility of the configured file was verified by attempting to open its public URL in an incognito browser window.

* **Public URL of the Example File:** `https://storage.googleapis.com/codtech-internship-mybucket-2025/ilide.info-lux-algo-signals-amp-overlays-61-pr_4fd52ecacecd2db180613801d34f95c0.pdf'

## Conclusion

Task 1, "Cloud Storage Setup," has been successfully completed on Google Cloud Platform. I have demonstrated the creation of a storage bucket, the upload of example files, and the configuration of access permissions, including making a file publicly accessible. All work-related files and documentation are stored in this GitHub repository.# CODTECH-Cloud-Computing-Internship

---

## Task 2: Cloud Monitoring and Alerts

This section details the setup of monitoring and alerting for a cloud-based service, fulfilling Task 2 of the internship. I used **Google Cloud Monitoring (Operations Suite)** to achieve this.

### 1. Alert Policy Configuration

An alert policy was created to notify me of activity on my Google Cloud Storage bucket, demonstrating the ability to set up automated alerts based on specific metrics.

* **Monitored Metric:** Google Cloud Storage - Request count
* **Threshold:** Triggered when "Request count" rate exceeds 2 per second within a 5-minute rolling window.
* **Notification Channel:** Email (configured to send alerts to my specified email address).
* **Policy Name:** `My Email Alerts`

**Screenshot 4: Configured Alert Policy Overview**
 https://github.com/ankitdatta07/CODTECH-Cloud-Computing-Internship/blob/main/Task%202.png?raw=true

**Screenshot 5:**
https://github.com/ankitdatta07/CODTECH-Cloud-Computing-Internship/blob/main/Task%202%20(2).png?raw=true

### 2. Monitoring Dashboard Creation

A custom dashboard was created to visualize key metrics related to my cloud storage, providing a comprehensive overview of its performance and usage.

* **Dashboard Name:** `CODTECH Internship Cloud Storage Dashboard`
* **Included Charts:**
    * Cloud Storage: Request count (filtered by bucket name)
    * Cloud Storage: Bytes sent (filtered by bucket name) - (If you couldn't find "Bytes sent", use another relevant GCS metric you found)

**Screenshot 6: Monitoring Dashboard Overview**
https://github.com/ankitdatta07/CODTECH-Cloud-Computing-Internship/blob/main/Task%202%20(3).png?raw=true


## Conclusion for Task 2

Task 2, "Cloud Monitoring and Alerts," has been successfully completed using Google Cloud Monitoring. I have configured an alert policy for Cloud Storage request count and created a custom dashboard to visualize relevant metrics. This demonstrates proficiency in setting up proactive monitoring and insightful data visualization for cloud services. All work-related files and documentation for Task 2 are stored in this GitHub repository.
