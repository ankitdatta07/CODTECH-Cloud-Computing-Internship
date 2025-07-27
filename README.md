# CODTECH Cloud Computing Internship 
Task 1: Cloud Storage Setup

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


## Task 3: Multi-Cloud Architecture (AWS + GCP)

This section details the implementation of a multi-cloud architecture, demonstrating seamless serverless communication and data flow between Amazon Web Services (AWS) and Google Cloud Platform (GCP).

### Objective

The primary objective of this task was to create a workflow where:
* A file uploaded to **AWS S3** triggers an event.
* An **AWS Lambda** function is invoked by this S3 event.
* The Lambda function sends a request to a **GCP Cloud Run** service.
* The **Cloud Run** service processes the request and logs the event, which is then viewable in **GCP Logs Explorer**.

This setup showcases real-time, event-driven interoperability between two distinct cloud environments.

### Tools Used

The following cloud services were utilized in this multi-cloud pipeline:
* **AWS S3:** For object storage and event triggering.
* **AWS Lambda:** For serverless compute to process S3 events and initiate cross-cloud communication.
* **GCP Cloud Run:** For serverless compute to receive requests from AWS Lambda and log events.
* **GCP Logs Explorer:** For monitoring and verifying the successful execution and logging of events on the GCP side.

### Step-by-Step Implementation Guide

The following steps were performed to set up the multi-cloud architecture:

1.  **Create AWS S3 Bucket:**
    * A new S3 bucket named `codtech-task3-bucket` was created in the AWS Console. This bucket serves as the entry point for the multi-cloud workflow.

2.  **Create AWS Lambda Function:**
    * An AWS Lambda function named `triggerGCPFunction` was created with Python 3.9 runtime. This function will be triggered by S3 events.

3.  **Add Lambda Code to Call GCP:**
    * The Lambda function's code was configured to make an HTTP POST request to a GCP Cloud Run service. This code includes error handling for the HTTP request.
    ```python
    import json
    import urllib3

    http = urllib3.PoolManager()

    def lambda_handler(event, context):
        gcp_url = "<your-cloud-run-url>" # This will be replaced with actual URL later
        data = {"message": "File uploaded to S3"}
        encoded_data = json.dumps(data).encode('utf-8')

        try:
            response = http.request("POST", gcp_url, body=encoded_data, headers={'Content-Type': 'application/json'})
            return {
                'statusCode': response.status,
                'body': response.data.decode('utf-8')
            }
        except Exception as e:
            return {
                'statusCode': 500,
                'body': f"Error calling GCP: {str(e)}"
            }
    ```

4.  **Add S3 Trigger to Lambda:**
    * An S3 trigger was added to the `triggerGCPFunction` Lambda function. This trigger is configured to fire on `PUT` events in the `codtech-task3-bucket`, meaning the Lambda function will execute whenever a new file is uploaded to this S3 bucket.

5.  **Deploy Cloud Run in GCP:**
    * A new service named `gcpfunction` was deployed on GCP Cloud Run.
    * The service was configured to use Python 3.9 runtime and allow unauthenticated access, enabling it to receive requests from the AWS Lambda function.
    * The Flask application code for Cloud Run was implemented to receive POST requests, print the received data (which gets logged to GCP Logs Explorer), and return an 'OK' status.
    ```python
    import flask
    from flask import request

    app = flask.Flask(__name__)

    @app.route('/', methods=['POST'])
    def receive():
        data = request.get_json()
        print(f"Received from AWS: {data}") # This will appear in GCP Logs Explorer
        return 'OK', 200
    ```

6.  **Update Lambda with Cloud Run URL:**
    * After deploying the Cloud Run service, its unique URL was obtained.
    * The `gcp_url` variable in the AWS Lambda function's code was updated with this actual Cloud Run URL.
    * The Lambda function was then re-deployed with the updated code.

7.  **Test Upload to S3:**
    * To test the entire multi-cloud pipeline, an example file (e.g., `test.txt`) was uploaded to the `codtech-task3-bucket` in AWS S3. This action initiated the workflow.

8.  **Check Logs in GCP:**
    * The GCP Logs Explorer was accessed.
    * Logs were filtered by `Resource type: Cloud Run Revision` and searched for the message "Received from AWS:".
    * The presence of this log message confirmed the successful end-to-end communication from AWS S3, through AWS Lambda, to GCP Cloud Run, and finally to GCP Logs Explorer.

### Architecture Diagram

The following diagram visually represents the multi-cloud architecture implemented for this task, illustrating the event flow from AWS S3 to GCP Cloud Logging.

**Screenshot 7: Multi-Cloud Architecture Diagram**
![Multi-Cloud Architecture Diagram](YOUR_LINK_TO_ARCHITECTURE_DIAGRAM_PNG_HERE)

---

## Conclusion for Task 3

Task 3, "Multi-Cloud Architecture," has been successfully completed by designing and conceptually implementing a serverless pipeline between AWS and GCP. This setup demonstrates robust multi-cloud communication, where an event in AWS (file upload to S3) seamlessly triggers a service in GCP (Cloud Run), with the event details logged and verifiable in GCP Logs Explorer. This showcases practical interoperability and the power of leveraging services across different cloud providers.
