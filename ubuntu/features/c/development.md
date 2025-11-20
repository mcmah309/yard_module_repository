```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "c development module"
args:
    optional:
        - clang-version
```
```Dockerfile 
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    clang \
    clangd \
    clang-format \
    clang-tidy \
    && rm -rf /var/lib/apt/lists/*
```
