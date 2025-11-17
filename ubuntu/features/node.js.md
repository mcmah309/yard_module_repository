```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Node.js"
args:
    optional:
        - version
```
```Dockerfile
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    curl \
    # set to 4, 5, 6, ... as needed
    && v={{ version | default (value="23") }} \
    && curl -sL https://deb.nodesource.com/setup_$v.x | bash - \
    && apt-get install -y nodejs \
    && node -v \
    && npm -v \
    && npx -v
    && rm -rf /var/lib/apt/lists/*
```