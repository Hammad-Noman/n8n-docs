---
title: AI Workflow Builder
description: Create, refine, and debug workflows using natural language descriptions of your goals.
status: beta
---

# AI Workflow Builder

AI Workflow Builder enables you to create, refine, and debug workflows using natural language descriptions of your goals.

It handles the entire workflow construction process, including node selection, placement, and configuration, thereby reducing the time required to build functional workflows.

For details of pricing and availability of AI Workflow Builder, see [n8n Plans and Pricing](https://n8n.io/pricing/).

!!! note
    The AI Workflow Builder generates workflows automatically, but you should always review the generated nodes and configurations before activating the workflow.

## Availability

- **Availability**: Available on n8n Cloud Starter, Pro, and Enterprise plans. Self-hosted availability depends on licensing and environment configuration (see self-host section).
- **Credits**: Each time you ask the builder to create or modify a workflow (for example, "Build" or "Execute and refine"), that counts as one interaction and consumes one credit. Example plan allocations: Starter = 50 credits/month, Pro = 150 credits/month, Enterprise = 1000 credits/month (cloud only). If credits are exhausted you must upgrade or wait for a monthly reset.
- **Does NOT count**: UI-only preview or aborted attempts that fail with model errors (see Troubleshooting).

## Accessing the AI Workflow Builder

To open the AI Workflow Builder:

1. Open the **n8n editor UI**.
2. Click **+ Add workflow** or open an existing workflow.
3. Click **Build with AI** in the editor toolbar.
4. The AI builder panel opens where you can describe the workflow you want to create.

The builder generates a complete workflow including:
- Nodes
- Connections
- Basic configuration

You can then review and refine the workflow before running it.

## Working with the builder

1. **Describe your workflow:** Either select an example prompt or describe your requirements in natural language.
2. **Monitor the build:** The builder provides real-time feedback through several phases.
3. **Review and refine the generated workflow:** Review required credentials and other parameters. Refine the workflow using prompts.
    
    ![ai-workflow-builder.png](/_images/advanced-ai/ai-workflow-builder.png)
    

### Commands you can run in the builder

## Example prompts

You can describe workflows in natural language. For best results, include:

- The trigger
- The services involved
- The expected action

### Example 1: Send Slack message from new GitHub issue
```
Create a workflow that triggers when a new GitHub issue is opened and sends a message to Slack with the issue title and URL.
```

### Example 2: Summarize emails using AI
```
Create a workflow that checks Gmail every hour, summarizes new emails using OpenAI, and sends the summary to Telegram.
```

### Example 3: Scrape website and store results
```
Build a workflow that fetches a webpage, extracts article titles, and saves them to a Google Sheet.
```

### Example 4: Webhook to Discord notification
```
Create a workflow that receives data from a webhook and sends the message content to a Discord channel.
```

This helps people building integrations.

Tip: Be explicit about triggers, services, and outputs.

- `/clear`: Clears the context for the LLM and lets you start from scratch

## Refining workflows

After the builder generates a workflow, you can ask it to refine or modify the workflow.

Examples:

- Change the trigger from webhook to schedule
- Add error handling
- Transform data before sending it

Example prompt:
Add a filter so that Slack notifications are only sent for high priority issues.

The builder will update the workflow and explain the changes it made.

## Limitations

The AI Workflow Builder is currently in **beta** and may have limitations:

- Generated workflows may require manual adjustments.
- Some node configurations may not be fully completed.
- Complex workflows may require multiple refinement prompts.
- The builder may not support all community nodes.

Always review the generated workflow before running it.

## Understanding credits

### How credits work

Each time you send a message to the builder asking it to create or modify a workflow, that counts as one **interaction**, which is worth one **credit**.

✅ **Counts as an interaction**

- Sending a message to create a new workflow
- Asking the builder to modify an existing workflow
- Clicking the **Execute and refine** button in the builder window after a workflow is built

❌ **Does NOT count as an interaction**

- Messages that fail or produce generation errors
- Requests you manually stop by clicking the stop button

### Getting more credits

If you've used your monthly limit, you can upgrade to a higher plan.

For details on plans and pricing, see [n8n Plans and Pricing](https://n8n.io/pricing/).

## Best practices

To get the best results from the AI builder:

- Be specific about triggers and services.
- Describe the expected output clearly.
- Break complex workflows into smaller steps.
- Use follow-up prompts to refine the workflow.

Example strategy:

1. Generate the initial workflow.
2. Review the generated nodes.
3. Ask the builder to refine or extend the workflow.

## AI model and data handling

The following data are sent to the LLM:

- Text prompts that you provide to create, refine, or debug the workflow
- Node definitions, parameters, and connections and the current workflow definition.
- Any mock execution data that is loaded when using the builder

The following data are not sent:

- Details of any credentials you use
- Past executions of the workflow

## Troubleshooting

### The builder generated an incomplete workflow

Ask the builder to complete missing steps. For example:
Finish configuring the Slack node and map the required fields.

### The workflow doesn't run

Check:

- Credentials
- Required parameters
- Node connections

### The builder misunderstood my request

Rephrase your prompt with more detail.

## Tutorials

- [Build a Slack alert workflow using AI](tutorial-build-slack-alert-workflow.md)