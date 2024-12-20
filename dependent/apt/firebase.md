```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "firebase cli module"
args:
    optional:
        - version
```
```Dockerfile
RUN \
    # set to 4, 5, 6, ... as needed
    v={{ version | default (value="20") }} \
    && curl -sL https://deb.nodesource.com/setup_$v.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g firebase-tools \
    && export PATH="$PATH":"$HOME/.pub-cache/bin"
    # && firebase login # Needs to be done by user
```
