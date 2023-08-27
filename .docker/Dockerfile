# Ubuntu 22.04 LTS
FROM mcr.microsoft.com/dotnet/sdk:6.0-jammy

LABEL Author="Josh Byrnes"
LABEL Email="j.byrnes.github@gmail.com"
LABEL GitHub="https://github.com/j-byrnes/ado-dockeragent"
LABEL BaseImage="mcr.microsoft.com/dotnet/sdk:6.0-jammy"

RUN DEBIAN_FRONTEND=noninteractive apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get upgrade -y && useradd -m agentuser
 
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y -qq --no-install-recommends \
    apt-transport-https \
    apt-utils \
    ca-certificates \
    curl \
    git \
    iputils-ping \
    jq \
    lsb-release \
    software-properties-common \
    nano
 
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash
 
# Can be 'linux-x64', 'linux-arm64', 'linux-arm', 'rhel.6-x64'.
ENV TARGETARCH=linux-x64

WORKDIR /azp
RUN chown -R agentuser:agentuser /azp
RUN chmod 755 /azp
 
COPY ./extras/start.sh .
RUN chmod +x start.sh
# All subsequent commands run under this user
USER agentuser
 
#ENTRYPOINT [ "./start.sh", "--once" ]
ENTRYPOINT [ "pwsh"]
