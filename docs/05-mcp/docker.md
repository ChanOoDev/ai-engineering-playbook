# Docker MCP

A Docker MCP integration helps AI tools inspect containers, images, Dockerfiles, Compose files, local development environments, and build output. It is useful for debugging application runtime behavior and improving container quality.

## Common Use Cases

- Explain Dockerfiles and Compose configurations.
- Diagnose build failures and container startup errors.
- Review image size, base images, exposed ports, and environment variables.
- Generate local development instructions.
- Suggest health checks and runtime hardening improvements.

## Setup Considerations

Local Docker access can be powerful. Limit the integration to the intended developer environment and avoid exposing unrelated containers or host paths. Document whether the tool can only inspect Docker state or can also build, start, stop, and remove containers.

## Security Guidance

Be careful with mounted volumes, environment variables, private registries, and images containing credentials. Do not grant broad host-level access unless the workflow requires it and the risk is understood.

## Validation

A safe validation sequence is:

1. Read a Dockerfile or Compose file.
2. List non-sensitive local images or containers if allowed.
3. Build a sample image in a sandbox project.
4. Confirm that destructive actions such as removing containers or volumes require explicit approval.

## Example Configuration

A typical Claude Code MCP configuration for Docker:

```json
{
  "mcpServers": {
    "docker": {
      "command": "npx",
      "args": ["-y", "@anthropic/docker-mcp-server"]
    }
  }
}
```

## Example Prompts

**Reviewing a Dockerfile:**

```
Review the Dockerfile in src/api/. Check for:
- Base image pinning and size optimization
- Multi-stage build opportunities
- Exposed ports and environment variables
- Security hardening (non-root user, minimal packages)
- Health check configuration

Suggest specific improvements with the updated Dockerfile.
```

**Diagnosing a build failure:**

```
The Docker build for our Node.js API is failing with "npm ERR! peer dep
conflict." Inspect the Dockerfile and package-lock.json to identify the
conflict and suggest a fix that doesn't require broad --legacy-peer-deps.
```

## Operating Model

Docker MCP should improve development repeatability and runtime visibility. It should not hide the actual build and run commands from engineers; generated guidance should remain easy to reproduce manually.

## External References

- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)
- [Docker Build Documentation](https://docs.docker.com/build/)
- [Open Container Initiative Image Specification](https://github.com/opencontainers/image-spec)
- [Kubernetes Documentation](https://kubernetes.io/docs/)

## Third-Party Repositories

- [docker/cli](https://github.com/docker/cli)
- [docker/compose](https://github.com/docker/compose)
- [moby/moby](https://github.com/moby/moby)
- [docker/buildx](https://github.com/docker/buildx)
- [opencontainers/image-spec](https://github.com/opencontainers/image-spec)

---
*Last updated: 2026-06-21 | Version: 1.1*
