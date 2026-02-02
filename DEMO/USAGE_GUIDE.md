# Setup & Usage Guide - Google Sheets Notifications

## Overview
This automated workflow monitors a specific Google Sheet and sends a professionally formatted email notification whenever a new row is added.

## Prerequisites
- An active n8n instance.
- Google Cloud Credentials (for accessing Sheets).
- SMTP Credentials (for sending emails).

## Installation Instructions

1. **Import the Workflow**
   - Open your n8n dashboard.
   - Navigate to **Workflows** > **Import from File**.
   - Select the `workflow.json` file included in this package.

2. **Configure Credentials**
   - **Node: Google Sheets Trigger**
     - Double-click the node.
     - Under **Authentication**, select or create your Google account credentials.
     - Select the **Document** and the specific **Sheet** you want to monitor.
     - Ensure the event is set to **"Row Added"**.

   - **Node: Send Email**
     - Double-click the node.
     - Under **Credentials**, select your SMTP account.
     - Configure the **From Email** and **To Email** addresses.
     - *Note: The email body is pre-configured with a professional HTML template that automatically adapts to your sheet's data.*

## Stability Features
- **Data Validation**: Includes a security filter that ignores empty or incomplete rows to prevent false triggers.
- **Auto-Retry**: In case of network failure, the system will automatically retry sending the email up to 3 times.
- **Error Monitoring**: A backup system is included to notify administrators if a critical error occurs in the workflow.

---
*Final Deliverable - Workflow Automation*
