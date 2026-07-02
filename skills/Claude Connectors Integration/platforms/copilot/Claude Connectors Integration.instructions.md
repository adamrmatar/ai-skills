# Copilot Instructions: Claude Connectors Integration
Description: Skill for connecting Claude AI to external services like Gmail, Google Calendar, and Notion through Claude Connectors and Zapier MCP to automate workflows and enhance productivity.

# Claude Connectors Integration Skill

## Overview
This skill enables you to connect Claude to external services for enhanced automation capabilities. See [Core Concepts](references/core_concepts.md) for foundational knowledge.

## Step-by-Step Workflow
1. **Access Connectors Menu**
   - Click profile icon → Customize → Connectors

2. **Select Service to Connect**
   - Choose from available options (Gmail, Calendar, etc.)
   - For extended options, select Zapier MCP

3. **Authenticate Service**
   - Follow OAuth flow for each service
   - Example Gmail auth prompt:
     ```
     [Gmail Authentication]
     Please log in to your Google account to continue
     Allow Claude to:
     [✓] Read your emails
     [✓] Send emails on your behalf
     ```

4. **Verify Connection**
   - Test with simple query: "Are there any unread emails?"

5. **Begin Automation**
   - Use natural language prompts to interact with connected services
   - Sample prompt template:
     ```
     "Draft a professional response to [email subject] that includes:
     - Acknowledgement of their message
     - Answer to their question about [topic]
     - Availability for follow-up next week"
     ```

## Best Practices
- Start with read-only permissions before granting write access
- Use specific date ranges in calendar queries ("this week" vs "recently")
- For Zapier, pre-configure common workflows in your Zapier account

## Common Pitfalls
1. **Over-permissioning**: Granting full access when only read is needed
   - Fix: Adjust permissions in service settings
2. **Vague Queries**: "Check my emails" is less effective than "Show unread emails from boss"
3. **Zapier Timeouts**: Complex automations may exceed execution windows
   - Solution: Break into smaller Zaps

## Validation Steps
1. Test basic retrieval ("Show my next meeting")
2. Verify action commands ("Schedule a meeting")
3. Check error handling for:
   - Invalid queries
   - Service outages
   - Permission errors

For detailed implementation examples, see [Practical Guide](references/practical_guide.md).

## Reference Guides

### Core Concepts

# Core Concepts of Claude Connectors

Claude Connectors are integration tools that allow Claude AI to interact with external services like email clients, calendars, and productivity apps. This enables Claude to perform actions like reading emails, scheduling events, or managing tasks directly within your conversations.

Key capabilities include:
- **Service Integration**: Connect to popular services like Gmail, Google Calendar, Notion
- **Data Access**: Read and summarize information from connected accounts
- **Action Automation**: Perform actions like drafting emails or creating calendar events
- **Extended Reach**: Through Zapier MCP, access 9,000+ additional apps

Architecture:
1. Authentication layer handles OAuth with services
2. Permission system controls data access levels
3. API translation layer converts between Claude's interface and service APIs

Security features include:
- Token-based authentication
- Session-limited access
- Explicit user permissions for each action

Common use cases:
- Email triage and response drafting
- Calendar management
- Task synchronization across platforms
- Data retrieval from connected apps

### Practical Guide

# Practical Guide to Using Claude Connectors

## Initial Setup
1. Ensure you have a Claude Pro account (required for connectors)
2. Navigate to Claude's web interface
3. Click your profile icon → 'Customize' → 'Connectors'

## Connecting Services
For Gmail:
1. Select 'Gmail' from available connectors
2. Authenticate with your Google account
3. Set permission levels (read-only, compose, etc.)
4. Confirm connection

For Zapier MCP:
1. Select 'Zapier' connector
2. Authenticate with Zapier account
3. Configure desired app connections
4. Set up trigger-action pairs as needed

## Usage Patterns
**Email Management:**
- "Show me unread emails from [sender]"
- "Draft a response to email [subject] saying [message]"

**Calendar Operations:**
- "Do I have meetings scheduled with [person] this week?"
- "Schedule a 30-minute meeting with [person] on [date]"

**Notion Integration:**
- "Create a new page in [workspace] with title [title]"
- "Summarize the key points from [Notion page]"

## Maintenance
- Regularly review connected services
- Audit permissions quarterly
- Disconnect unused integrations
- Monitor API usage limits

### Sources

# Video Sources

The following curated videos were synthesized to create this skill:

1. **[How to Use Claude Connectors](https://www.youtube.com/watch?v=1-Rr3iadlOs)** by Kevin Stratvert