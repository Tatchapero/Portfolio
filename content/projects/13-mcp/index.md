---
title: "MCP"
summary: "MCP (Model Context Protocol) is an open standard protocol for connecting AI applications to external systems, data sources, tools and workflows. It acts as a universal bridge between AI applications and data sources and tools."
date: 2026-05-22
categories: ["Project"]
tags: ["mcp", "model", "context", "protocol"]
---

## What is MCP?

**MCP** (Model Context Protocol) is an open standard protocol for connecting AI applications to external systems, data sources, tools and workflows.

It acts as a universal bridge between AI applications and data sources and tools. 

For example, you could hook up a code agent to Figma with MCP, so that your agent can have direct access to your designs, and have the code agent build a frontend that looks exactly like the Figma design.

MCP architecture consists of:

- **MCP Host**: The AI application that manages one or multiple MCP clients
- **MCP Client**: A component that maintains a connection to an MCP server
- **MCP Server**: A program that provides context to MCP clients

Using the same example with a code agent and Figma:

| MCP Component | Example |
| --- | --- |
| MCP Host | Code Agent (OpenAI Codex, Claude Code) |
| MCP Client | Open AI/Claude Code's built-in MCP connector |
| MCP Server | Figma

### Transport layer

MCP supports two transport mechanisms:

- `STDIO` transport
  - Uses standard input/output streams
  - Used for direct process communication between local processes
  - Provides optimal performance with no network overhead
  - Typically serves a single MCP client
- Streamable `HTTP` transport
  - Uses `HTTP POST` for client-to-server messages
  - Enables remote server communication
  - Supports standard HTTP authentication methods (Bearer tokens, API keys, custom headers)
  - Typically serves many MCP clients

### Benefits

- MCP makes it easy to build and integrate an AI to an external system
- MCP is an open standard, so it is broadly supported
- MCP has real-time context access

## What we've learned

- MCP is an open standard for connecting AI applications to external systems
- MCP architechture consists of a host, client and a server
- MCP supports `STDIO` transport and streamable `HTTP` transport