```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Node.js"
args:
    optional:
        - version
```
```Dockerfile
RUN \
    apt-get install -y curl \
    # set to 4, 5, 6, ... as needed
    {% if version %}
        && curl -sL https://deb.nodesource.com/setup_{{ version }}.x | bash - \
    {% else %}
        && curl -sL https://deb.nodesource.com/setup | bash - \
    {% endif %}
    && apt-get install -y nodejs
```