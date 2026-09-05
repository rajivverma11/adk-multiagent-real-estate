# Real Estate ADK Multi-Agent

A learning project that demonstrates how to build AI agents with
**Google Agent Development Kit (ADK)** and connect them to **Model
Context Protocol (MCP)** servers.

The project uses a real-estate scenario to demonstrate agents that can
access pricing, inventory, and seller-related information through MCP
tools.

## Tech Stack

-   Python 3.11
-   Google ADK
-   Model Context Protocol (MCP)
-   LiteLLM
-   OpenAI GPT-4o
-   uv

## Project Structure

``` text
real-estate-adk-multiagent/
├── m1_mcp/
│   ├── pricing_server.py
│   └── inventory_server.py
├── m2_adk_multiagents/
│   └── ...
├── .env.example
├── .gitignore
├── requirements.txt
└── README.md
```

The `m1_mcp` directory contains the MCP servers required by the ADK
agents. The `m2_adk_multiagents` directory contains the ADK and
multi-agent examples.

## Setup

### 1. Clone the repository

``` bash
git clone <your-repository-url>
cd real-estate-adk-multiagent
```

### 2. Create a Python 3.11 virtual environment

``` bash
uv venv --python 3.11
```

Activate it on macOS/Linux:

``` bash
source .venv/bin/activate
```

### 3. Install dependencies

``` bash
uv pip install -r requirements.txt
```

This project currently uses the MCP 1.x API. If needed, install a
compatible MCP version:

``` bash
uv pip install "mcp<2"
```

## Environment Variables

Create a `.env` file from the example:

``` bash
cp .env.example .env
```

Add your OpenAI API key to `.env`:

``` text
OPENAI_API_KEY=your_openai_api_key_here
```

Do not commit your real `.env` file or API key to Git.

## Test the MCP Servers

Test the pricing server:

``` bash
uv run python m1_mcp/pricing_server.py --check
```

Test the inventory server:

``` bash
uv run python m1_mcp/inventory_server.py --check
```

## Run the ADK Application

For an ADK demo directory, run:

``` bash
uv run adk web m2_adk_multiagents/adk_demos/
```

Then open the local ADK web interface shown in the terminal, typically:

``` text
http://127.0.0.1:8000
```

Select an available agent and interact with it through the ADK
interface.

## Example

A property advisor can use information exposed by multiple MCP servers
to answer questions such as:

``` text
What's 742 Evergreen Terrace worth?
```

or:

``` text
Walk me through whether to make an offer on 742 Evergreen Terrace.
I have a $460K budget.
```

The agent can discover and call relevant MCP tools and combine their
results into a response.

## Notes

-   Use Python 3.11 for this project.
-   The current MCP server code uses the MCP 1.x `FastMCP` API.
-   Keep `.env` out of source control.
-   `.env.example` should contain placeholders only, never real API
    keys.

## Purpose

This repository is intended as a learning project for experimenting
with:

-   Google ADK agents
-   MCP tool integration
-   Multi-agent architectures
-   Tool discovery and invocation
-   Agent callbacks and guardrails
-   AI-assisted real-estate workflows
