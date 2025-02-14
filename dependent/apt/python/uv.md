```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "uv for python and project management"
args:
    optional:
        - version # e.g. 0.5.18
```
```Dockerfile
RUN apt-get update -y && apt-get upgrade -y && apt install -y build-essential libssl-dev pkg-config curl \
    {% if version %}
    && curl -LsSf https://astral.sh/uv/{{ version }}/install.sh | sh \
    {% else %}
    && curl -LsSf https://astral.sh/uv/install.sh | sh \
    {% endif %}
    && . $HOME/.local/bin/env \
    && uv tool install mypy
```