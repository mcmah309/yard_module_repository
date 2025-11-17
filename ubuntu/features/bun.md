```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Deno"
args:
    optional:
        - version # e.g. `bun-v1.2.19`
```
```Dockerfile
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    curl \
    unzip \
    && rm -rf /var/lib/apt/lists/*
RUN curl -fsSL https://bun.com/install | bash {% if version %} -s "{{ version }}" {% endif %}
```