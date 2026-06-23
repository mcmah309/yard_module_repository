```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "pi coding agent"
```
```Dockerfile
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    curl \
    && rm -rf /var/lib/apt/lists/*
RUN curl -fsSL https://pi.dev/install.sh | sh
```