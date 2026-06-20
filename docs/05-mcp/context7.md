# Context7 MCP

A Context7 MCP integration provides current library and framework documentation to AI tools. It helps reduce outdated API usage by letting agents retrieve relevant documentation during implementation, debugging, and migration work.

## Common Use Cases

- Check current API syntax for libraries and frameworks.
- Look up configuration examples during setup.
- Compare migration guidance across versions.
- Ground implementation advice in official documentation.
- Reduce reliance on stale model memory for fast-moving ecosystems.

## Setup Considerations

Configure the integration through the approved MCP configuration path for the AI client. Ensure developers know when to invoke documentation lookup, especially for frontend frameworks, backend frameworks, SDKs, cloud tools, and libraries with frequent releases.

## Usage Guidance

Use Context7 before making claims about current library behavior or version-specific APIs. Ask for documentation that matches the exact package, framework, or tool in use. When the project pins a specific version, include that version in the request if supported.

## Review Notes

Documentation lookup improves accuracy, but it does not remove the need to inspect local code. The repository may use wrappers, older versions, custom abstractions, or conventions that differ from upstream examples.

## Example Configuration

A typical Claude Code MCP configuration for Context7:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

## Example Prompts

**Checking current API syntax:**

```
Look up the current React Query v5 API for data fetching. I need to know
the correct syntax for useQuery with TypeScript, including the new
placeholderData and retry options. Our project uses React Query 5.12.
```

**Migration guidance:**

```
We're migrating from Express 4 to Express 5. Look up the Context7 docs
for Express 5 breaking changes and list the specific changes needed in
our src/routes/ directory.
```

## Validation

Confirm that the integration can retrieve documentation for a common package used by the project. Then verify that generated guidance references the same library family and version range as the codebase.

## External References

- [Context7](https://context7.com/)
- [Context7 GitHub Repository](https://github.com/upstash/context7)
- [npm Documentation](https://docs.npmjs.com/)
- [MDN Web Docs](https://developer.mozilla.org/)
- [DevDocs API Documentation Browser](https://devdocs.io/)

## Third-Party Repositories

- [upstash/context7](https://github.com/upstash/context7)
- [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
- [microsoft/typespec](https://github.com/microsoft/typespec)
- [mdn/content](https://github.com/mdn/content)
- [freeCodeCamp/devdocs](https://github.com/freeCodeCamp/devdocs)

---
*Last updated: 2026-06-21 | Version: 1.1*
