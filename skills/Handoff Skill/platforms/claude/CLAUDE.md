# Claude Code Custom Instructions - Handoff Skill
> The Handoff Skill enables an AI agent to compact the current conversation into a handoff document for another agent to pick up. This ensures seamless continuation of work across different agent sessions.

### Overview
The Handoff Skill is designed to facilitate the transfer of context and intent from one AI agent to another. This is particularly useful in scenarios where a task needs to be handed off to a different agent for specialized processing or when the context window of the current agent is nearing its limit.

### Step-by-Step Workflow
1. **Initiate Handoff**: Trigger the handoff process by instructing the agent to create a handoff document.
2. **Summarize Conversation**: The agent compacts the current conversation into a concise summary.
3. **Suggest Skills**: The agent suggests relevant skills for the next session based on the context.
4. **Create Temporary File**: The agent writes the handoff document to a temporary file.
5. **Read Before Write**: Ensure the file is read before writing to avoid errors in Claude.
6. **Reference Artifacts**: Avoid duplicating content by referencing existing artifacts by path or URL.
7. **Tailor Document**: If user arguments are provided, tailor the document to focus on the specified aspects.
8. **Handoff to New Agent**: Provide the path of the handoff document to the new agent to continue the work.

### Code/Prompt Snippets
```python
# Example command to initiate handoff
handoff_command = "/handoff"

# Example prompt for summarizing conversation
summary_prompt = "Summarize the current conversation for handoff to another agent."

# Example code snippet for creating a temporary file
import tempfile
with tempfile.NamedTemporaryFile(delete=False, prefix='handoff_', suffix='.txt') as temp_file:
    temp_file.write(summary.encode('utf-8'))
    handoff_path = temp_file.name
```

### Best Practices
- **Clear Summarization**: Ensure the summary captures the essence of the conversation, including context and intent.
- **Skill Suggestion**: Accurately suggest skills that align with the next session's goals.
- **File Handling**: Always read the file before writing to avoid errors in Claude.
- **Artifact Reference**: Reference existing artifacts to avoid redundancy.

### Common Pitfalls
- **Incomplete Summary**: Failing to capture all relevant details can lead to confusion in the next session.
- **Incorrect Skill Suggestion**: Suggesting irrelevant skills can derail the next session.
- **File Handling Errors**: Not reading the file before writing can cause errors in Claude.
- **Redundant Content**: Duplicating content from existing artifacts can lead to inefficiency.

### Validation Steps
1. **Review Summary**: Ensure the summary accurately reflects the conversation.
2. **Check Skill Suggestions**: Verify that the suggested skills are relevant to the next session.
3. **File Integrity**: Confirm that the handoff document is correctly written and readable.
4. **Artifact References**: Ensure all referenced artifacts are correctly linked.

### Supporting Reference Docs
- **Handoff Skill Documentation**: Detailed documentation on the Handoff Skill, including examples and troubleshooting tips.
- **File Handling in Claude**: A guide on best practices for file handling in Claude to avoid common errors.
- **Agent Collaboration Workflow**: An overview of workflows involving multiple agents and how the Handoff Skill fits into these workflows.

# Detailed Guidelines

## Agent Collaboration Workflow

# Agent Collaboration Workflow

## Overview
Agent collaboration workflows involve multiple agents working together on a task. The Handoff Skill plays a crucial role in ensuring seamless transitions between agents.

## Workflow Steps
1. **Initiate Handoff**: Trigger the handoff process.
2. **Summarize Conversation**: Compact the current conversation.
3. **Suggest Skills**: Recommend relevant skills for the next session.
4. **Create Temporary File**: Write the handoff document to a temporary file.
5. **Handoff to New Agent**: Provide the path of the handoff document to the new agent.

## Examples
```python
# Example command to initiate handoff
handoff_command = "/handoff"

# Example prompt for summarizing conversation
summary_prompt = "Summarize the current conversation for handoff to another agent."
```

## Troubleshooting
- **Incomplete Summary**: Ensure the summary captures all relevant details.
- **Incorrect Skill Suggestion**: Verify that the suggested skills are relevant to the next session.
- **File Handling Errors**: Always read the file before writing to avoid errors in Claude.

## File Handling In Claude

# File Handling in Claude

## Overview
File handling in Claude requires careful attention to avoid common errors. This guide covers best practices for reading and writing files in Claude.

## Best Practices
- **Read Before Write**: Always read the file before writing to avoid errors.
- **Temporary Files**: Use temporary files for handoff documents to ensure they are not kept around unnecessarily.

## Examples
```python
import tempfile
with tempfile.NamedTemporaryFile(delete=False, prefix='handoff_', suffix='.txt') as temp_file:
    temp_file.write(summary.encode('utf-8'))
    handoff_path = temp_file.name
```

## Troubleshooting
- **File Errors**: Ensure the file is correctly read before writing.
- **File Integrity**: Confirm that the file is correctly written and readable.

## Handoff Skill Documentation

# Handoff Skill Documentation

## Overview
The Handoff Skill allows an AI agent to compact the current conversation into a handoff document for another agent to pick up. This ensures seamless continuation of work across different agent sessions.

## Usage
To use the Handoff Skill, simply initiate the handoff process by instructing the agent to create a handoff document. The agent will summarize the conversation, suggest relevant skills, and write the document to a temporary file.

## Examples
```python
# Example command to initiate handoff
handoff_command = "/handoff"

# Example prompt for summarizing conversation
summary_prompt = "Summarize the current conversation for handoff to another agent."
```

## Troubleshooting
- **Incomplete Summary**: Ensure the summary captures all relevant details.
- **File Handling Errors**: Always read the file before writing to avoid errors in Claude.
- **Redundant Content**: Reference existing artifacts to avoid duplication.

## Sources

# Video Sources

The following curated videos were synthesized to create this skill:

1. **[New Skills! /handoff, /prototype, /review and /writing-* | Skills Changelog](https://www.youtube.com/watch?v=DNqsMXH6Eog)** by Matt Pocock