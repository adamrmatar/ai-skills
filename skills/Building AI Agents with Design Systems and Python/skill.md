## Overview
This skill teaches you how to build AI agents that integrate design systems and context engineering using Python and the Agentspan framework. You'll learn to define agents, create tools, and ensure resilience against crashes. For a deeper dive into core concepts, see [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow
1. **Install Prerequisites**: Ensure Python 3.10+, JDK, and uv are installed.
2. **Set Up Agentspan**: Initialize a project and add Agentspan dependencies.
3. **Define Tools**: Create Python functions with decorators to expose them to the agent.
4. **Configure the Agent**: Define the agent's name, model, and tool list.
5. **Run the Agent**: Use the Agentspan server to execute the agent.
6. **Ensure Resilience**: Implement idempotent tool calls and handle crashes gracefully.

## Code Snippets
```python
from agentspan import tool

@tool
def get_weather(city: str) -> str:
    """Returns the weather for a given city."""
    return f"Sunny in {city}"
```
For more examples, see [Code Examples](references/code_examples.md).

## Best Practices
- Always include docstrings and type hints in tool functions.
- Use idempotent tool calls to avoid duplicate results.
- Validate your setup with `uv run agentspan doctor`.

## Common Pitfalls
- Missing docstrings can confuse the agent.
- Non-idempotent tool calls can lead to duplicate data.
- Improper setup of AI providers can cause failures.

## Validation Steps
1. Run `uv run agentspan doctor` to check setup.
2. Execute the agent and verify tool calls in the Agentspan dashboard.
3. Test crash resilience by interrupting the agent mid-execution.

For a practical guide, see [Practical Guide](references/practical_guide.md).