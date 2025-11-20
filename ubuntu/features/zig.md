```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Installs zigup and zig"
args:
    optional:
        - version
```
```Dockerfile
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    curl \
    xz-utils \
    && rm -rf /var/lib/apt/lists/* \
    && curl -L https://github.com/marler8997/zigup/releases/latest/download/zigup-x86_64-linux.tar.gz | tar xz -C /usr/local/bin \
    && /usr/local/bin/zigup {{ version | default (value="0.15.2") }} --install-dir /usr/local/bin
```