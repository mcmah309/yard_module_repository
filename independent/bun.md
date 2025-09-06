```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Deno"
args:
    optional:
        - version # e.g. `bun-v1.2.19`
```
```Dockerfile
{% if version %}
RUN apt-get install curl -y && curl -fsSL https://bun.com/install | bash -s "{{ version }}"
{% else %}
RUN apt-get install curl -y && curl -fsSL https://bun.sh/install | bash
{% endif %}
```