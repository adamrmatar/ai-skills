# Claude Code Custom Instructions - Agent Workflow Management With Ci/Cd Principles
> A skill for managing AI agent workflows by implementing CI/CD principles to ensure reliability, prevent failures, and maintain operational guarantees.

## Overview
Managing AI agent workflows effectively requires more than just crafting prompts or skills. Over time, you’ll find yourself rebuilding essential operational guarantees like testing, monitoring, and validation. This skill teaches you how to implement CI/CD principles in your agent workflows to prevent failures, ensure reliability, and maintain credibility.

### Core Concepts
To understand this skill, familiarize yourself with the following concepts:
- **Handoffs**: Points in the workflow where data or tasks are passed from one agent or skill to another.
- **Gates**: Validation checkpoints that ensure outputs meet specific criteria before proceeding.
- **Audit Trails**: Logs that record actions and decisions for troubleshooting and accountability.

For a deeper dive, see [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow
1. **Map Your Handoffs**: Identify all handoffs in your workflow. For example, scheduler to command, command to research, etc.
2. **Identify Expensive Handoffs**: Focus on handoffs where failures would be most costly (e.g., publishing incorrect claims).
3. **Implement Gates**: Add validation gates at critical handoffs. Examples include:
   - **Pre-save Output Contract**: Ensure artifacts have the required shape.
   - **Voice/Domain Contract**: Verify outputs match your system’s rules.
   - **Verification Contract**: Trace claims to their sources.
   - **Deduplication Check**: Ensure outputs are genuinely new.
   - **Audit Trail**: Log failures for troubleshooting.
4. **Block Bad Outputs**: Ensure gates block artifacts that fail validation, rather than just logging warnings.
5. **Monitor and Alert**: Set up monitoring and alerts for silent failures.

For detailed instructions, see [Practical Guide](references/practical_guide.md).

## Code Snippets and Prompt Templates
Here’s an example of a voice contract gate:
```python
def voice_contract_check(output):
    # Example: Ensure output doesn’t use generic AI marketing language
    forbidden_phrases = ["unlock the power", "game-changer", "transform how teams operate"]
    for phrase in forbidden_phrases:
        if phrase in output:
            return False
    return True
```

For more examples, see [Code Examples](references/code_examples.md).

## Best Practices and Common Pitfalls
### Best Practices
- **Start Small**: Begin with one gate at the most expensive handoff.
- **Block, Don’t Warn**: Gates should block bad outputs, not just log warnings.
- **Log Everything**: Maintain detailed audit trails for troubleshooting.

### Common Pitfalls
- **Polished but Wrong Outputs**: Outputs that look complete but fail validation (e.g., generic AI marketing language).
- **Unverified Claims**: Claims without traceable sources.
- **Near Duplicates**: Outputs that recycle old content.

For more examples and explanations, see [Common Pitfalls](references/common_pitfalls.md).

## Validation and Testing
1. **Regression Testing**: Test whether changes break downstream skills.
2. **Contract Testing**: Validate output schemas at handoff boundaries.
3. **Audit Trails**: Ensure logs capture failures and their causes.

## References
See the following documents for further reading:
- [Core Concepts](references/core_concepts.md)
- [Practical Guide](references/practical_guide.md)
- [Code Examples](references/code_examples.md)
- [Common Pitfalls](references/common_pitfalls.md)

# Detailed Guidelines

## Code Examples

## Code Examples
### Voice Contract Gate
Here’s an example of a voice contract gate:
```python
def voice_contract_check(output):
    # Example: Ensure output doesn’t use generic AI marketing language
    forbidden_phrases = ["unlock the power", "game-changer", "transform how teams operate"]
    for phrase in forbidden_phrases:
        if phrase in output:
            return False
    return True
```

### Verification Contract Gate
Here’s an example of a verification contract gate:
```python
def verification_contract_check(output, verification_log):
    # Ensure claims are traceable to a source
    if "37%" in output and not verification_log:
        return False
    return True
```

### Deduplication Check
Here’s an example of a deduplication check:
```python
def deduplication_check(output, vault_history):
    # Ensure output is genuinely new
    for historical_output in vault_history:
        if output == historical_output:
            return False
    return True
```

## Common Pitfalls

## Common Pitfalls
### Polished but Wrong Outputs
Outputs that look complete but fail validation are dangerous. For example, generic AI marketing language like "unlock the power" or "game-changer" may look professional but don’t match your voice.

### Unverified Claims
Claims without traceable sources erode credibility. For example, stating "Teams with a clear semantic ownership model reduce AI rollout rework by 37%" without a verification log is problematic.

### Near Duplicates
Outputs that recycle old content make your system look automated but unoriginal. For example, using the same hook or angle repeatedly.

### Silent Failures
Silent failures occur when a scheduled task fails without alerting you. For example, a cron job failing silently for a week.

### Gates That Don’t Block
Gates that log warnings but don’t block bad outputs are ineffective. For example, logging a warning about a missing verification but allowing the output to proceed.

## Core Concepts

## Core Concepts
### Handoffs
Handoffs are critical points in your workflow where data or tasks are passed from one agent or skill to another. Each handoff is a potential failure point, especially if you’re building the system alone. Examples include scheduler to command, command to research, and research to content.

### Gates
Gates are validation checkpoints that ensure outputs meet specific criteria before proceeding. They act as safeguards against bad outputs. Examples include:
- **Pre-save Output Contract**: Ensures artifacts have the required shape.
- **Voice/Domain Contract**: Verifies outputs match your system’s rules.
- **Verification Contract**: Traces claims to their sources.
- **Deduplication Check**: Ensures outputs are genuinely new.

### Audit Trails
Audit trails are logs that record actions and decisions for troubleshooting and accountability. They are essential for reconstructing what happened when something goes wrong.

### Why CI/CD Principles?
Agent systems lack operational guarantees by default. Implementing CI/CD principles ensures reliability, prevents failures, and maintains credibility.

## Practical Guide

## Practical Guide
### Step 1: Map Your Handoffs
Identify all handoffs in your workflow. For example:
1. Scheduler to Command
2. Command to Research
3. Research to Content
4. Content Plan to Production
5. Production Skill to Verifier
6. Verifier to Reviewer
7. Reviewer to Output Folder

### Step 2: Identify Expensive Handoffs
Focus on handoffs where failures would be most costly. Examples include:
- Publishing incorrect claims.
- Breaking schemas that cascade to downstream skills.
- Duplicating content that erodes audience trust.

### Step 3: Implement Gates
Add validation gates at critical handoffs. Examples include:
- **Pre-save Output Contract**: Ensure artifacts have the required shape.
- **Voice/Domain Contract**: Verify outputs match your system’s rules.
- **Verification Contract**: Trace claims to their sources.
- **Deduplication Check**: Ensure outputs are genuinely new.
- **Audit Trail**: Log failures for troubleshooting.

### Step 4: Block Bad Outputs
Ensure gates block artifacts that fail validation, rather than just logging warnings.

### Step 5: Monitor and Alert
Set up monitoring and alerts for silent failures.

## Sources

# Video Sources

The following curated videos were synthesized to create this skill:

1. **[Every Solo Agent Builder Eventually Reinvents a Worse Version of CI/CD - Sumaiya Shrabony](https://www.youtube.com/watch?v=WLXxTaPagA8)** by AI Engineer