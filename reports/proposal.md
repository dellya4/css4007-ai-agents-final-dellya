# Project Proposal — Semester Week 10

## AI-Powered GNS3 Network Cloning and Validation Agent

## Problem Description

Creating an experimental copy of a computer network may require manual configuration and verification. 
This process can take time and lead to errors.

The goal of this project is to develop an AI agent that can automatically clone an existing network in GNS3, 
validate the copied topology, and help identify problems. In the future, 
this system can be used to prepare digital twin environments for cybersecurity experiments.

## Target Users

* Computer networking and cybersecurity students
* Network administrators
* Cybersecurity specialists
* Researchers working with GNS3

## Selected Difficulty

A - Advanced.

The project will use an LLM, multiple tools, multi-step execution, error handling, state management, and safety controls

## Expected Functionality

1. Connect to GNS3 using its REST API.

2. Retrieve information about a reference network.

3. Automatically create a separate copy of the network.

4. Compare nodes and links between the original and copied networks.

5. Check virtual device status.

6. Detect problems and suggest next actions.

7. Save agent execution results.

8. Protect the original network from accidental changes.

## Proposed Functions

| Function | Purpose | Inputs | Outputs | Dependencies |
|---|---|---|---|---|
| `get_projects()` | Retrieve available GNS3 projects | None | Project names and IDs | GNS3 REST API |
| `get_topology()` | Retrieve network topology | `project_id` | Nodes and links | GNS3 REST API |
| `duplicate_project()` | Clone an existing project | `project_id`, `new_name` | New project ID | GNS3 REST API |
| `compare_topologies()` | Compare original and cloned networks | `source_id`, `copy_id` | List of differences | Python, GNS3 API |
| `check_node_status()` | Check virtual device status | `project_id` | Node statuses | GNS3 REST API |
| `generate_report()` | Generate a validation report | Validation results | Report | Python |

## Proposed Agent Tools

The AI agent will use the following model-callable tools:

1. **`get_projects`** — Find available GNS3 projects.
2. **`get_topology`** — Inspect the structure of a selected network.
3. **`duplicate_project`** — Create an experimental copy of a reference network.
4. **`compare_topologies`** — Compare the original and copied networks.
5. **`check_node_status`** — Check the status of virtual devices.

The agent will select tools based on the user's request and the results of previous actions.

## Model Selection

**OpenAI API** with a cost-efficient model that supports function calling.

Python and OpenAI API will be used for development. The final model will be selected after evaluating API costs and tool-calling performance.

## Architecture

The planned system architecture is:

`User → Web Interface → Python Backend → AI Agent → GNS3 REST API → GNS3 Server`

The AI agent will process user requests and call Python tools to interact with GNS3.

The application will store validation results, execution logs, and agent state for further analysis.

## Example Requests

1. "Show all available GNS3 projects."
2. "Create a copy of Office-Reference named Office-Test-01."
3. "Compare the reference network with its copy."
4. "Check whether all devices were copied successfully."
5. "Find problems in the copied network and suggest next actions."

## Evaluation Plan

At least **12 tests** will be performed, including at least **4 safety tests**.

The tests will cover:

1. Correct tool selection.
2. Successful project cloning.
3. Accurate topology comparison.
4. Detection of missing nodes.
5. Detection of missing links.
6. Device status verification.
7. Handling invalid project IDs.
8. GNS3 API error handling.
9. Protection of the reference project (safety).
10. Prevention of unauthorized project operations (safety).
11. Agent execution limits (safety).
12. Handling unsafe or unexpected requests (safety).

Execution logs will be reviewed to verify that the agent selects appropriate tools and adapts its actions when errors occur.

## Weekly Milestones

| Week | Planned Work |
|---|---|
| Week 10 | Select the project topic, review requirements, and design the architecture. |
| Week 11 | Install GNS3 and create a small reference network. |
| Week 12 | Develop Python integration with GNS3 REST API. |
| Week 13 | Implement network cloning and topology comparison. |
| Week 14 | Integrate OpenAI API and agent tools. |
| Week 15 | Add adaptive error handling, state management, and safety controls. |
| Week 16 | Test the application, improve the interface, and fix issues. |
| Week 17 | Complete the final report, documentation, and demonstration. |