```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "hurl module"
args:
    optional:
        - version
```
```Dockerfile
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    curl \
    && rm -rf /var/lib/apt/lists/*
RUN VERSION={{ version | default (value="6.0.0") }} \
    && curl --location --remote-name https://github.com/Orange-OpenSource/hurl/releases/download/$VERSION/hurl_${VERSION}_amd64.deb \
    && apt install ./hurl_${VERSION}_amd64.deb \
    && rm ./hurl_${VERSION}_amd64.deb
```
