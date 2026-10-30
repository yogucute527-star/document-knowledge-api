# Agentic AI

## Agent Overview

### Purpose

The **Document Knowledge API** can be extended with an AI agent to help applications search, retrieve, and work with technical documentation.

The agent builds on the existing Document Knowledge API and RAG capabilities. It combines an AI model with tools, planning, workflows, and guardrails so that it can determine the actions required to accomplish a documentation-related task.

### Agent Role in the Document Knowledge API

The agent acts as an intelligent layer on top of the Document Knowledge API.

For example, when a user asks:

> "Find the API authentication documentation and explain how API keys are used."

The agent can:

1. Understand the user's request.
2. Determine what action is required.
3. Use a document-search or retrieval tool.
4. Retrieve relevant documentation.
5. Use the retrieved information to generate an answer.
6. Apply defined guardrails before returning the response.

### Agent Components

The Agentic AI extension of the Document Knowledge API consists of the following components:

- **AI Model** — understands the user's request and generates the response.
- **Tools** — provide capabilities such as searching or retrieving documents.
- **Function Calling** — allows the AI model to request execution of a specific tool with structured arguments.
- **Planning** — determines which actions should be taken to accomplish the user's goal.
- **Workflow** — defines the sequence of actions, tool calls, and results involved in completing the task.
- **Guardrails** — define the rules and restrictions that control what the agent is allowed to do.

### Relationship with RAG

The agent works together with the RAG layer of the Document Knowledge API.

RAG provides the agent with relevant documentation, while the agent determines how and when to use available tools to accomplish the user's request.

For example:

**User request → Agent → Document search → Relevant documentation → Agent → Generated answer**

### Intended Use

The Agentic AI extension is intended to demonstrate how the Document Knowledge API can evolve from a standard documentation API into an intelligent documentation workflow.

It provides a foundation for applications that need to retrieve technical information, use tools, make decisions based on results, and generate documentation-focused responses within defined boundaries.

## Agent Workflow

### Overview

The Agentic AI extension of the **Document Knowledge API** uses a workflow to define how the agent processes a user request, selects tools, retrieves information, and generates a response.

The workflow connects the agent's planning, tool usage, retrieved information, and final response into a sequence of actions.

### Workflow

A typical documentation request follows this flow:

**User Request → Understand Goal → Plan → Select Tool → Execute Tool → Observe Result → Generate Response**

### 1. User Request

The user submits a documentation-related question or task.

Example:

> "How do I authenticate with the Document Knowledge API?"

### 2. Understand the Goal

The agent interprets the request and identifies what information the user needs.

In this example, the goal is to find information about API authentication.

### 3. Plan

The agent determines which action should be taken to accomplish the goal.

For example, it may determine that it needs to search the available technical documentation.

### 4. Select Tool

The agent selects an appropriate tool, such as a document-search tool.

### 5. Execute Tool

The application executes the selected tool using the arguments provided by the agent.

**Example:**

`search_documents("API authentication")`

### 6. Observe Result

The agent receives the result returned by the tool.

If relevant documentation is found, the agent can use that information to continue.

If the result is not useful, the agent may refine the search and try again.

### 7. Generate Response

After obtaining relevant information, the agent uses the retrieved documentation to generate a response for the user.

### Example Workflow

User Request  
↓  
Agent receives request  
↓  
Understand goal  
↓  
Plan action  
↓  
Select document-search tool  
↓  
Execute search  
↓  
Relevant documentation found?

**If No:** Refine search → Search again

**If Yes:** Use retrieved information  
↓  
Generate response  
↓  
Return response to user

### Guardrails in the Workflow

Guardrails can be applied throughout the workflow to control the agent's behavior.

For example:

- Restrict the agent to approved documentation sources.
- Prevent unsupported actions.
- Require confirmation before destructive actions.
- Prevent the agent from returning information that is not supported by the available documentation.

### Workflow Outcome

The workflow allows the Document Knowledge API agent to move from a user's request to a relevant, documentation-supported response while providing controlled steps for tool usage and decision-making.

## Tools and Function Calling

The Agentic AI extension of the **Document Knowledge API** uses tools to give the agent capabilities beyond generating text.

### Tool

A **tool** is an external capability that an agent can use to accomplish a task.

For example:

**Tool:** `search_documents`  
**Purpose:** Search the available technical documentation.

### Function Calling

**Function calling** allows the AI model to request execution of a specific tool using structured arguments.

Example:

**Function:** `search_documents`  
**Argument:** `API authentication`

The application executes the tool and returns the search results to the agent.

### Workflow

**User Request → Agent → Function Call → Tool Execution → Tool Result → Response**

### Key Difference

- **Tool:** The capability available to the agent.
- **Function calling:** The mechanism used to request that the tool be executed.

In the Document Knowledge API, tools and function calling allow the agent to retrieve relevant documentation and use it to generate a supported response.

## Tool API Reference

### Overview

The Document Knowledge API agent uses tools to access capabilities that are not available through the AI model alone.

### search_documents

Searches the available technical documentation for information relevant to the user's request.

| Field | Description |
|---|---|
| Tool Name | `search_documents` |
| **Purpose** | Search technical documentation |
| **Input** | Search query |
| **Output** | Relevant document content or search results |

### Example

**Input:**  
`API authentication`

**Expected result:**  
Relevant documentation about API authentication and API keys.

### Usage in the Agent Workflow

The agent can call `search_documents` when it needs information from the Document Knowledge API's documentation.

**Agent → search_documents → Search Results → Agent → Response**

If the search does not return useful information, the agent can refine the query and perform another search.

### Notes

The tool should be used only for its defined purpose and within the guardrails configured for the agent.

## Planning and Decision Flow

### Overview

Planning allows the **Document Knowledge API agent** to determine which actions are needed to accomplish a user's request.

The agent can choose an appropriate tool, evaluate the result, and adjust its next action when necessary.

### Decision Flow

**User Request → Understand Goal → Plan Action → Select Tool → Execute Tool → Evaluate Result → Respond or Retry**

### Example

User asks:

> "Find the API authentication documentation."

The agent can:

1. Understand that documentation needs to be retrieved.
2. Plan to search the documentation.
3. Select the **search_documents** tool.
4. Execute the search.
5. Evaluate the search result.
6. Generate a response if relevant information is found.
7. Refine the search and try again if the result is not useful.

### Key Point

**Planning determines what the agent should do next based on the user's goal and the results of previous actions.**

## Guardrails

### Overview

Guardrails define the rules and restrictions that control what the **Document Knowledge API agent** is allowed to do.

They help keep the agent's behavior controlled, predictable, and aligned with the intended workflow.

### Guardrails in the Project

The agent should:

- Use approved technical documentation as its information source.
- Avoid generating unsupported information.
- Use tools only for their defined purposes.
- Follow permission requirements before performing restricted actions.
- Ask for confirmation before destructive actions, such as deleting a document.

### Example

If the agent has access to a document deletion tool, it should **ask for confirmation before deleting a document**.

This prevents unintended destructive actions.

### Key Point

**Planning determines what the agent should do, while guardrails define what the agent is allowed to do.**

## Agent Implementation Guide

### Overview

The Agentic AI extension of the **Document Knowledge API** combines the AI model, document-search tools, planning, workflow, and guardrails to process documentation-related requests.

### Implementation Flow

1. **Receive the user request**  
   The agent receives a documentation-related question or task.

2. **Determine the goal**  
   The agent identifies what information or action is required.

3. **Select a tool**  
   The agent selects an appropriate tool, such as **search_documents**.

4. **Execute the tool**  
   The application executes the requested function and returns the result.

5. **Evaluate the result**  
   The agent checks whether the returned information is relevant.

6. **Generate the response**  
   The agent uses the relevant documentation to provide the user with a response.

7. **Apply guardrails**  
   The agent follows the defined rules and restrictions throughout the process.

### Example

**User Request → Agent → search_documents → Relevant Documentation → Agent → Response**

If the search does not provide useful information, the agent can refine the search and try again.

### Implementation Requirements

The implementation should provide:

- An AI model
- Access to approved documentation
- Defined tools and functions
- A workflow for tool usage and responses
- Guardrails for controlled behavior

## Agent Testing

### Overview

Testing the **Document Knowledge API agent** verifies whether it correctly understands requests, selects appropriate tools, uses retrieved information, and follows defined guardrails.

### Test Scenarios

| Test Scenario | Expected Result |
|---|---|
| Valid documentation request | Agent retrieves relevant information and provides a response |
| Irrelevant request | Agent does not provide unsupported information |
| Search returns no useful result | Agent refines the search or handles the result appropriately |
| Tool selection | Agent selects the appropriate tool for the task |
| Restricted action | Agent follows the defined guardrail |
| Destructive action | Agent requests confirmation before performing the action |

### Testing Focus

Agent testing should verify:

- **Accuracy** — the response is correct and supported by documentation.
- **Tool usage** — the appropriate tool is selected and used correctly.
- **Workflow behavior** — the agent follows the expected sequence of actions.
- **Guardrails** — restricted actions are handled according to defined rules.
- **Consistency** — similar requests produce appropriate and reliable behavior.

### Expected Outcome

The agent should retrieve relevant documentation, use tools appropriately, follow its defined workflow and guardrails, and avoid generating unsupported information.

## Agent Troubleshooting

### Overview

Troubleshooting the **Document Knowledge API agent** helps identify and resolve problems with tool usage, retrieval, workflow, and guardrails.

### Common Issues

| Issue | Possible Cause | Resolution |
|---|---|---|
| Agent returns unsupported information | Relevant documentation was not retrieved | Check retrieval results and restrict responses to approved documentation |
| Search returns no useful result | Search query is too broad or unclear | Refine the search query and try again |
| Wrong tool selected | Agent misunderstood the user's goal | Review the tool descriptions and agent workflow |
| Tool execution fails | Invalid input or tool error | Check the function arguments and tool response |
| Agent performs a restricted action | Guardrail is missing or not applied | Review and strengthen the relevant guardrail |
| Agent gives inconsistent responses | Workflow or retrieval behavior is inconsistent | Test similar requests and review the workflow |

### Troubleshooting Approach

When an issue occurs:

1. Identify the user's request.
2. Check the agent's selected action and tool.
3. Review the tool input and returned result.
4. Check whether the workflow was followed correctly.
5. Verify that the required guardrails were applied.
6. Test the agent again after making the necessary change.

### Expected Outcome

Troubleshooting should help ensure that the Document Knowledge API agent retrieves relevant information, uses the correct tools, follows its workflow, and operates within defined guardrails.
