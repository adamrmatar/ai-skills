# Building RBAC Applications with AI

## Overview
This skill teaches you to efficiently build Role-Based Access Control (RBAC) applications using a hybrid AI/visual development approach. Key concepts are covered in [Core Concepts](references/core_concepts.md).

## Step-by-Step Workflow

1. **Define Requirements**
   - Identify all user roles (e.g., organizers, regular users)
   - List permissions for each role (create/edit vs. view)
   - Outline key data entities and relationships

2. **Initial Prompt**
   ```
   Build an event management app. Organizers can create and edit events with name, date, and description. Regular users can view events and sign up.
   ```

3. **Permission Modeling** (before generation)
   - Use visual tools to define access rules
   - Create permission groups with checkboxes
   - See [Practical Guide](references/practical_guide.md) for details

4. **Database Inspection**
   - Verify proper table relationships exist
   - Check for:
     - Events table (name, date, description)
     - Users table (with role differentiation)
     - Sign-ups table (linking users to events)

5. **Workflow Automation**
   - Set triggers (e.g., new sign-up)
   - Define actions (send emails, update status)
   - Add conditions (check capacity)

6. **Custom UI Logic**
   - Use AI only for specific components like:
   ```
   Create a live capacity counter that shows 'Only X spots left' and turns red when below 5.
   ```

## Best Practices
- Always model permissions first
- Use visual tools for workflows and permissions
- Reserve AI for small, custom UI components
- Inspect database relationships carefully

## Common Pitfalls
Avoid these mistakes documented in [Common Pitfalls](references/common_pitfalls.md):
- Generating before defining permissions
- Using flattened data structures
- Overusing AI for simple configuration

## Validation Steps
1. Test each role's permissions thoroughly
2. Verify database relationships handle real-world usage
3. Check workflows execute correctly
4. Confirm UI components respect permissions
5. Stress test edge cases (concurrent sign-ups, etc.)

## Implementation Notes
- This approach works best for business applications (internal tools, CRMs)
- For consumer UI-focused apps, consider different tools
- Always use the right tool for the job scope