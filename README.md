# ADO-DOCKERAGENT

This is a docker image for running an Azure DevOps agent in a docker container. It is based off of [Moim Hossain's](https://moimhossain.com/2022/11/08/self-hosted-azure-devops-pool-on-azure-container-apps/) post on setting up ADO agents in docker containers for use on Azure Container App Services.

## Building The Image

```powershell
& docker build -t ado-buildagent .\.docker
```

## Manual running of image

```powershell
$azpURL = "<URL to Azure Org>"
$azpToken = "<PAT (https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows)>"
$azpAgentName = "<ADO Agent Name"
$azpPool = "<ADO Agent Pool Name>"
& docker run -e AZP_URL=$azpURL -e AZP_TOKEN=$azpToken -e AZP_AGENT_NAME=$azpAgentName -e AZP_POOL=$azpPool ado-buildagent:latest

```

## Reference Information

- Original Source Post: [https://moimhossain.com/2022/11/08/self-hosted-azure-devops-pool-on-azure-container-apps/](https://moimhossain.com/2022/11/08/self-hosted-azure-devops-pool-on-azure-container-apps/)
- Create ADO PAT: [https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows)
- MS Documentation on running ADO agent as a container: [https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops#create-and-build-the-dockerfile-1](https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops#create-and-build-the-dockerfile-1)
- KEDA: [https://keda.sh/](https://keda.sh/)
- MS Artifact Registry: [https://mcr.microsoft.com/](https://mcr.microsoft.com/)
  - GitHub reference: [https://github.com/microsoft/containerregistry](https://github.com/microsoft/containerregistry)
- Dockerfile Best Practices: [https://docs.docker.com/develop/develop-images/dockerfile_best-practices/](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- Sysdig Dockerfile best practices (some good basic info): [https://sysdig.com/blog/dockerfile-best-practices/](https://sysdig.com/blog/dockerfile-best-practices/)
