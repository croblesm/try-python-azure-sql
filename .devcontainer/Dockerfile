# [Choice] Python version: 3.11-bookworm, 3.12-bullseye
ARG VARIANT="3.12-bullseye"
FROM mcr.microsoft.com/devcontainers/python:1-${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends software-properties-common

# Install SQL Tools: SQLPackage and sqlcmd
COPY sql/installSQLtools.sh installSQLtools.sh
RUN bash ./installSQLtools.sh \
     && apt-get clean -y && rm -rf /var/lib/apt/lists/* /tmp/library-scripts

# Install .NET SDK 8 (for SQL Database projects)
COPY dotnet/install-dotnet.sh install-dotnet.sh
RUN bash ./install-dotnet.sh \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/* /tmp/library-scripts