```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "firebase cli module"
```
```Dockerfile
RUN \
    # set to 4, 5, 6, ... as needed
    v=20 \
    && curl -sL https://deb.nodesource.com/setup_$v.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g firebase-tools \
    && firebase login \
    && export PATH="$PATH":"$HOME/.pub-cache/bin" \
```
