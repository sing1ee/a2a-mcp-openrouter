# Example: Using a2a-python SDK Without an LLM Framework

This repository demonstrates how to set up and use the [a2a-python SDK](https://github.com/google/a2a-python) to create a simple server and client, without relying on any large language model (LLM) framework.

## Overview

- **A2A (Agent-to-Agent):** A protocol and SDK for building interoperable AI agents.
- **This Example:** Shows how to run a basic A2A server and client, exchange messages, and view the response.

## Prerequisites

- Python 3.13+
- [uv](https://github.com/astral-sh/uv) (for fast dependency management and running)
- An API key for OpenRouter (set as `OPENROUTER_API_KEY`)

## Installation

1. **Clone the repository:**
   ```bash
   git clone <this-repo-url>
   cd <repo-directory>
   ```

2. **Install dependencies:**
   ```bash
   uv pip install -e .
   ```

3. **Set environment variables:**
   ```bash
   export OPENROUTER_API_KEY=your-openrouter-api-key
   ```

   Or create a `.env` file with:
   ```
   OPENROUTER_API_KEY=your-openrouter-api-key
   ```

   **Note:** You can get your OpenRouter API key from [https://openrouter.ai/](https://openrouter.ai/)

## Running the Example

### 1. Start the Server

```bash
uv run --env-file .env a2a-server
```
- The server will start on port 9999.

### 2. Run the Client

In a new terminal:

```bash
uv run --env-file .env a2a-client --question "What is A2A protocol?"
```

- The client will connect to the server and send a request.

### 3. View the Response

- The response from the client will be saved to [response.xml](./response.xml).

## Configuration

The system uses the following configuration:
- **Model:** `google/gemini-flash-1.5` via OpenRouter
- **Base URL:** `https://openrouter.ai/api/v1`

## File Structure

- `src/a2a_mcp_openrouter/server/`: Server implementation.
- `src/a2a_mcp_openrouter/client/`: Client implementation.
- `response.xml`: Example response from the client.

## Troubleshooting

- **Missing dependencies:** Make sure you have `uv` installed.
- **API key errors:** Ensure `OPENROUTER_API_KEY` is set correctly.
- **Port conflicts:** Make sure port 9999 is free.
