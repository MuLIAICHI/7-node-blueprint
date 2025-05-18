# Setting Up the 7 Node Blueprint Example

This guide will walk you through setting up the example workflow for the 7 Node Blueprint. The workflow demonstrates a food critic AI agent that showcases all seven essential node types working together.

## Prerequisites

Before you begin, make sure you have:

1. n8n installed (either via Docker, npm, or n8n cloud)
2. OpenAI API key
3. Optional: Supabase account (for PostgreSQL memory)
4. Optional: Google account (for document storage)
5. Optional: Slack workspace (for approvals)

## Step 1: Install n8n

### Option A: Using Docker

```bash
docker volume create n8n_data
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

### Option B: Using npm

```bash
npm install n8n -g
n8n start
```

### Option C: n8n Cloud

Sign up at [n8n.cloud](https://www.n8n.cloud/) for a hosted solution.

## Step 2: Import the Workflow

1. Open your n8n instance in a browser (typically at http://localhost:5678)
2. Go to Workflows in the left sidebar
3. Click the "Import from File" button
4. Select the `7-node-blueprint-workflow.json` file from this repository

## Step 3: Configure Credentials

### OpenAI API Key

1. Go to Settings > Credentials
2. Click "New" and select "OpenAI API"
3. Enter your API key from [platform.openai.com](https://platform.openai.com/)
4. Save the credential

### Supabase (Optional)

1. Create a Supabase account and set up a new project
2. Create a PostgreSQL credential in n8n with your Supabase connection details
3. Update the PostgreSQL memory nodes in the workflow to use your credential

### Google Drive (Optional)

1. Set up Google Cloud credentials for Google Drive API
2. Create a Google Drive credential in n8n
3. Update the Google Drive nodes to use your credential

### Slack (Optional)

1. Create a Slack app in your workspace with appropriate permissions
2. Create a Slack credential in n8n
3. Update the Slack nodes to use your credential

## Step 4: Adjust the Workflow

1. Open the imported workflow
2. Review each node and update any references to specific credentials or resources
3. For the memory nodes, ensure the database connection is properly configured
4. For Slack approval nodes, update the channel and user references

## Step 5: Test the Workflow

1. Activate the workflow by toggling the switch in the upper right
2. Open the Chat interface in n8n (if using the Chat Trigger node)
3. Start interacting with your agent by asking it to recommend dishes

## Troubleshooting

### Common Issues

1. **API Key Issues**: Ensure your OpenAI API key is valid and has sufficient credits
2. **Database Connection**: Check that PostgreSQL connection details are correct
3. **Node Execution**: Use the "Execute Workflow" button to test individual nodes

### Getting Help

If you encounter issues with the workflow, you can:

1. Check the n8n logs for detailed error messages
2. Visit the [n8n forum](https://community.n8n.io/) for community support
3. Reach out via GitHub issues on this repository

## Advanced Configuration

### Customizing the Agent's Behavior

The primary behavior of the agent is controlled by system messages in the LLM nodes. To modify how the agent responds:

1. Open the AI Agent nodes
2. Locate the "System Message" field
3. Update the text to reflect your desired agent behavior

### Adding New Tools

To extend the agent's capabilities:

1. Add new tool nodes to the workflow (HTTP Request, Database, etc.)
2. Connect them to the appropriate agent node
3. Update prompts to instruct the agent on how to use the new tools

### Modifying Memory Storage

The example uses PostgreSQL and Google Docs for memory, but you can change to:

1. Simple variables for basic memory
2. Vector databases for semantic memory
3. Other document storage systems

## Next Steps

After getting the basic workflow running, consider:

1. Adding specialized tools for your domain
2. Implementing more sophisticated memory systems
3. Creating custom guardrails for your specific use case
4. Building a proper front-end interface for your agent

Happy building!
