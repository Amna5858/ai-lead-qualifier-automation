# AI-Powered Lead Qualifier Automation

An automated B2B lead qualification system that processes inbound inquiries, scores them using LLMs, and routes them to appropriate channels with built-in error handling.

## Tech Stack

- **Orchestration:** n8n
- **Intelligence:** OpenAI (GPT-4o-mini)
- **Database:** Airtable
- **Communication:** Slack & Gmail

## How it Works

1. **Trigger:** Captures lead data via a secure Webhook.
2. **Analysis:** Uses LangChain to analyze the lead and assign a qualification score (1-10).
3. **Smart Routing:** The workflow automatically performs one of three actions based on the score:
   - **Hot Leads (Score > 7):** Logged to Airtable and sent as a priority notification to Slack.
   - **Nurture (Score < 4):** Logged to Airtable and triggers an automated nurture sequence via Gmail.
   - **Manual Review (Score 4-7):** Logged to Airtable and flagged in Slack for human oversight.

## Reliability & Error Handling

- **Automated Alerts:** The project includes a dedicated "Error Handler" workflow that monitors the pipeline.
- **Failure Notification:** If any execution step fails, an automated email is triggered immediately to the administrator, including details on the failed node and error message.

## Installation

1. Download [`Lead_Qualification_and_Routing.json`](https://github.com/Amna5858/ai-lead-qualifier-automation/blob/main/Lead_Qualification_and_Routing.json) and [`Workflow_Error_Handler.json`](https://github.com/Amna5858/ai-lead-qualifier-automation/blob/main/Workflow_Error_Handler.json) from this repository.
2. In your n8n instance, use **Import from File** to upload both workflows.
3. Update the credentials for **Airtable**, **Slack**, **Gmail**, and **OpenAI** within the nodes.
4. Set the main workflow to **Active** to begin processing leads.
