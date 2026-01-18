# Based on Microsoft's devcontainer base image with batteries-included agentic development tools
# Optimized for daily autobuilds with proper layer caching
FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Layer 1: Base system dependencies and utilities (most stable)
RUN apt-get update && \
    apt-get install -y \
        curl wget unzip \
        jq yq \
        vim nano \
        make \
        build-essential \
        python3 python3-pip && \
    # Cleanup
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Layer 2: Install uv (modern Python package manager)
# COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/uv

# Layer 3: Install Go
# RUN GO_VERSION="1.21.5" && \
#    curl -fsSL "https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz" | tar -xzC /usr/local && \
#    echo 'export PATH=/usr/local/go/bin:$PATH' >> /etc/profile

# Layer 4: Install Rust
#RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y && \
#    echo 'source ~/.cargo/env' >> /etc/profile
# Layer 5: Install Node.js LTS
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - && \
    apt-get install -y nodejs
# Layer 6: Install cloud CLIs (moderately stable)
RUN ARCH=$(dpkg --print-architecture) && \
    # Install Azure CLI
    curl -sL https://aka.ms/InstallAzureCLIDeb | bash && \
    # Install GitHub CLI
    mkdir -p -m 755 /etc/apt/keyrings && \
    wget -nv -O- https://cli.github.com/packages/githubcli-archive-keyring.gpg | tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null && \
    chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | tee /etc/apt/sources.list.d/github-cli.list > /dev/null && \
    apt-get update && apt-get install -y gh && \
    # Cleanup
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Layer 7: AI CLI tools (most volatile - frequent releases)
# Install in order of stability (most stable first for better caching)
RUN npm install -g \
        @anthropic-ai/claude-code

# Layer 8: Final environment setup
ENV DISABLE_AUTOUPDATER=true

# Set the default user (matches devcontainer convention)
USER vscode
