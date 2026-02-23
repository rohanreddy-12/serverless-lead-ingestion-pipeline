
# Serverless Lead Ingestion Pipeline

A lightweight, serverless backend solution designed for a static HTML portfolio to seamlessly capture, process, and store contact form submissions without requiring a dedicated backend server.

## 🚀 Overview

This project replaces a traditional backend server (like Node.js or Python) with a visual automation workflow using **n8n**. When a user submits the contact form on the frontend, the data is asynchronously transmitted to an n8n webhook and securely logged into a Google Sheet in real-time.

### **Features**
* **Asynchronous Submission:** Uses JavaScript's `fetch()` API to send data to the webhook without triggering a page reload.
* **Serverless Architecture:** Eliminates the need for hosting a custom backend by leveraging n8n webhooks.
* **Automated Data Storage:** Automatically parses incoming JSON payloads and maps them to a Google Sheets database.
* **Real-time UI Feedback:** Disables the submit button during processing and provides instant success/error messages to the user.
* **CORS Configured:** Secure communication established between the static frontend and the automation workflow.

## 🛠️ Tech Stack

* **Frontend:** HTML5, CSS3, Vanilla JavaScript (ES6+ Promises/Fetch API)
* **Backend/Automation:** n8n (Node-based workflow automation)
* **Database:** Google Sheets API

## 🏗️ Architecture & Data Flow

1. **Client-Side:** The user fills out the contact form (Name, Email, Message).
2. **Data Transformation:** JavaScript intercepts the form submission, prevents the default refresh, appends an ISO timestamp, and packages the data into a JSON object.
3. **Transmission:** A POST request is sent to the n8n Webhook URL.
4. **n8n Workflow:** * **Webhook Node:** Receives the POST request and resolves CORS.
   * **Google Sheets Node:** Appends a new row mapping the JSON keys to the respective columns.
   * **Webhook Response Node:** Sends a `200 OK` status back to the frontend.
5. **UI Update:** The frontend receives the success response, clears the form, and displays a confirmation message.

## 📸 Project Screenshots

*(Note: Add your screenshots to a `/images` folder in your repo and uncomment the lines below)*

* **Frontend UI:** Clean, responsive form with gradient styling.
* **n8n Workflow:** The 3-node serverless pipeline (Webhook -> Append Row -> Respond).
* **Google Sheets Database:** The final destination for structured lead data.
