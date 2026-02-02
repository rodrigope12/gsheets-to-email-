# Setup Instructions for n8n Workflow

## 1. Import Workflow
1. Open your n8n dashboard.
2. Click on **Workflows** > **Import from File**.
3. Select the `workflow.json` file located in this folder.

## 2. Configure Credentials
This workflow requires you to connect your Google Sheets and Email credentials.

### Google Sheets Trigger Node
1. Double-click the **Google Sheets Trigger** node.
2. Under **Authentication**, select your Google Sheets account credential.
   - If you don't have one, select **Create New** and follow the n8n guide to set up OAuth2 with Google Console.
3. Select the **Document** (Spreadsheet) you want to monitor.
4. Select the **Sheet** (Tab) within that document.
5. Ensure **Event** is set to "Row Added".

### Email Node (Send Email)
1. Double-click the **Send Email** node.
2. Under **Credentials**, select your SMTP account.
   - For Gmail, you often need an "App Password" if you have 2FA enabled.
3. Update the **From Email** and **To Email** fields.
4. **Note:** The email body is now pre-configured with a professional HTML template that automatically lists all fields from the new row. You do not need to manually map fields unless you want to customize the design.

## 3. Reliability Features (What we improved)
- **Data Validation**: A new filter node ensures that empty or "ghost" rows do not trigger false emails.
- **Robust Polling**: The trigger checks for new rows every minute.
- **Retry Logic**: The Email node is configured to **retry 3 times** if it fails (e.g., network glitch).
- **Error Handling**: An independent "Error Trigger" workflow runs if the main workflow fails, sending a detailed alert to the admin.
- **HTML Formatting**: Emails now look professional and work on mobile devices.

## 4. Testing
1. Click **Execute Workflow** (simulating or waiting).
2. Go to your Google Sheet and add a new row of data.
3. Wait up to 1 minute.
4. Verify you receive the formatted HTML email.
5. **Negative Test**: Add a row with no data (if possible) or ensure that transient network issues (simulated) trigger the Error Email.
