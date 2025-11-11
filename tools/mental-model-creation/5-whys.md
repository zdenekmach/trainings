# 5 Whys Method

## Overview
The 5 Whys is a root cause analysis technique that involves asking "why" five times (or as many times as needed) to drill down from a symptom to the fundamental cause of a problem.

## When to Use

### Ideal Situations
- **Problem diagnosis**: When you need to identify the root cause of a specific problem
- **Simple to moderate complexity**: Works best for problems with clear cause-effect relationships
- **Quick analysis needed**: When you need rapid insights without extensive data collection
- **Team alignment**: When getting everyone on the same page about what's really causing an issue
- **Process improvement**: Identifying systemic issues in workflows or procedures

### Not Recommended For
- Highly complex problems with multiple interacting causes
- When immediate action is needed without time for analysis
- Problems requiring statistical analysis or large data sets
- Situations where the "why" questions lead to blame rather than understanding

## How to Use

### Step-by-Step Process

1. **Define the Problem Clearly**
   - State the problem in specific, observable terms
   - Example: "The website crashed during peak hours"

2. **Ask the First Why**
   - Why did this problem occur?
   - Focus on facts, not opinions
   - Example: "Why did the website crash? Because the server ran out of memory."

3. **Ask Why Again (2nd Level)**
   - Take the answer from step 2 and ask why that happened
   - Example: "Why did the server run out of memory? Because too many concurrent users were logged in."

4. **Continue Asking Why (3rd-5th Levels)**
   - Keep drilling down with each answer
   - Stop when you reach a root cause that's actionable
   - Example progression:
     - 3rd Why: "Why were too many concurrent users logged in? Because the session timeout was set too long."
     - 4th Why: "Why was the session timeout set too long? Because no one reviewed the default configuration."
     - 5th Why: "Why was the configuration never reviewed? Because there's no formal review process for infrastructure settings."

5. **Identify the Root Cause**
   - The final answer should point to a systemic issue or actionable root cause
   - In this example: Lack of formal review process for infrastructure

6. **Develop Counter-Measures**
   - Create action items to address the root cause
   - Example: Implement infrastructure configuration review process

## Conversation Guide for AI/Application

### Initial Engagement
```
AI: "I'll help you get to the root cause of this problem using the 5 Whys method.

First, can you clearly describe the problem you're experiencing? Be as specific as possible about what happened, when, and what the visible symptom was."

[Wait for user response]
```

### Iterative Questioning (Repeat 5 times or until root cause found)
```
AI: "Why do you think [previous answer] happened?

Try to focus on facts and observable causes rather than assumptions. If you're not sure, that's okay - we can explore different possibilities."

[Wait for user response]

[After each response, assess if this is the root cause or if you need to go deeper]
```

### Assessment Questions (Internal Logic for AI)
- Is this answer actionable?
- Does this point to a systemic issue rather than a symptom?
- Have we reached a point where fixing this would prevent recurrence?
- Are we at risk of going into blame rather than system analysis?

### Closure and Action Planning
```
AI: "Based on our analysis, it seems the root cause is: [summarize root cause].

This differs from the original symptom because [explain difference].

What actions could address this root cause? Let's brainstorm 2-3 potential solutions."

[Help user develop action items]
```

### Warning Signs to Watch For
- **Circular reasoning**: If answers start repeating, try a different angle
- **Human error as endpoint**: If you hit "because someone made a mistake," ask why the system allowed that mistake
- **Blame focus**: Redirect to systemic issues, not individual fault
- **Too shallow**: If reaching "root cause" in 2-3 whys, might need to go deeper

## Expected Outcomes

### What This Method Produces
- Clear understanding of root cause vs. symptoms
- Actionable insights for preventing recurrence
- Shared understanding among team members
- Documentation of causal chain from symptom to root

### Success Metrics
- Solution addresses the root cause, not just symptoms
- Problem doesn't recur after implementing countermeasures
- Team alignment on what caused the issue
- Clear action items identified

## Example Use Cases

### Software Bug
- **Problem**: Users can't log in
- **5 Whys**: Login fails → Database timeout → Too many connections → Connection pooling not configured → No infrastructure standards
- **Root Cause**: Missing infrastructure standards documentation

### Project Delay
- **Problem**: Project delivered 2 weeks late
- **5 Whys**: Late delivery → Testing took too long → Many bugs found → Code review skipped → Team under deadline pressure → Unrealistic timeline set
- **Root Cause**: Estimation process doesn't account for quality gates

### Customer Complaint
- **Problem**: Customer received wrong product
- **5 Whys**: Wrong product shipped → Warehouse picked wrong item → Similar SKUs confused → Labels unclear → Labeling system outdated
- **Root Cause**: Need for warehouse labeling system update

## Tips for Success
- Write down each question and answer
- Focus on processes and systems, not people
- Be persistent but know when to stop (diminishing returns)
- Validate assumptions with data when possible
- Use with other tools (fishbone diagram, Pareto analysis) for complex problems
