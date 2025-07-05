# Zoom AI Meeting Assistant with ClickUp and Google Calendar

This workflow acts as a powerful AI assistant for your Zoom meetings. Once a meeting recording is available, this automation fetches the transcript, uses an AI model to analyze the conversation, and then automatically performs key follow-up actions: it sends a summary email, creates tasks in ClickUp, and schedules a follow-up call in Google Calendar if needed.

## Overview

Forgetting to follow up on action items discussed in a meeting is a common problem. This workflow eliminates that risk by creating a fully automated post-meeting process. It ensures that all key decisions and tasks are captured, assigned, and communicated, improving productivity and accountability for your team.

## Features

* **Automated Trigger:** Uses a webhook to start automatically as soon as a Zoom meeting recording has been processed.
* **AI-Powered Analysis:** Leverages a Large Language Model (LLM) like GPT-4o to process the meeting transcript, generate a concise summary, and identify actionable tasks.
* **Task Management Integration:** Automatically creates tasks in a specified ClickUp list, assigning them based on the meeting discussion.
* **Email Summaries:** Sends a professionally formatted email summary of the meeting to all participants.
* **Automated Scheduling:** If the transcript mentions a need for a follow-up meeting, it automatically creates a new event in Google Calendar and invites the attendees.

## How It Works

1.  **Webhook Trigger:** Zoom sends a notification to the n8n webhook when a cloud recording is complete.
2.  **Fetch Transcript:** The workflow makes an API call to Zoom to retrieve the full meeting transcript and participant list.
3.  **Analyze with AI:** The transcript is passed to an `OpenAI` node. The prompt instructs the AI to:
    * Generate a summary of the meeting.
    * Extract a list of action items or tasks.
    * Determine if a follow-up meeting is required.
4.  **Execute Actions based on AI Output:**
    * **Create ClickUp Tasks:** The workflow loops through the list of action items provided by the AI and uses the `ClickUp` node to create a new task for each one.
    * **Send Summary Email:** An `Email` node sends the AI-generated summary to the meeting participants.
    * **Schedule Follow-up:** If the AI indicates a follow-up is needed, a `Google Calendar` node creates a new event for the suggested date and time.

## Technologies Used

* n8n
* Zoom
* ClickUp
* OpenAI (or another LLM provider)
* An email provider (e.g., Gmail, SMTP)
* Google Calendar

## Setup & Configuration

1.  **Zoom Webhook:** In your Zoom account settings, create a webhook subscription for the `recording.completed` event and point it to the n8n webhook URL.
2.  **Zoom Credentials:** Add your Zoom API credentials (JWT or OAuth) to n8n.
3.  **ClickUp Credentials:** Add your ClickUp API token and configure the `ClickUp` node with your desired Workspace, Space, and List for new tasks.
4.  **AI Provider Credentials:** Add your API key for an AI provider like OpenAI.
5.  **Email & Calendar Credentials:** Add your credentials for your email provider and Google Calendar.

## How to Use

1.  Complete the setup and activate the workflow.
2.  Host a meeting on Zoom and ensure it is being recorded to the cloud.
3.  After the meeting ends and the recording is processed, the workflow will trigger automatically.
4.  Check your email for the summary, your ClickUp list for new tasks, and your Google Calendar for any follow-up events.

This automation acts as a virtual assistant, ensuring every meeting is productive and actionable. [book a chat here😁](https://cal.com/closegem/coffee-chat)
