```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Deno"
args:
    optional:
        - version # e.g. `1.0.1`
```
```Dockerfile
RUN curl -fsSL https://deno.land/install.sh | sh
{% if version %}
RUN deno upgrade --version {{ version }}
{% endif %}
```