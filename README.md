# Azure DevOps Self-Hosted Agent

This project builds a self-hosted agent that can be use by Azure DevOps for CI/CD within Azure Pipelines.

This approach is based on [documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops#linux) within the Microsoft Azure docs.

## Testing Locally

```bash
docker build -t dockeragent:latest .

docker run -e AZP_URL=https://dev.azure.com/cdwms \
-e AZP_TOKEN=<<PAT_TOKEN_GOES_HERE>> \
-e AZP_POOL=test-agent-pool \
-e AZP_AGENT_NAME=mydockeragent \
dockeragent:latest
```

## GitHub Actions

To setup the GitHub Actions for building this image, set these Secret values:

* `DOCKER_IMAGE` => cwiederspan/azdo-agent-container-image

* `DOCKER_USERNAME` => cwiederspan

* `DOCKER_PASSWORD` => YOUR_DOCKER_PAT
