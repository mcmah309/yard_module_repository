```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Deno"
args:
    optional:
        - version # e.g. `1.0.1`
```
```Dockerfile
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    curl \
    && curl -fsSL https://deno.land/install.sh | sh -s -- --yes \
    {% if version %}
    && deno upgrade --version {{ version }} \
    {% endif %}
    && rm -rf /var/lib/apt/lists/*
```