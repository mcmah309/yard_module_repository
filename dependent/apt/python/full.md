```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "python module with most of the needed tools for development"
```
```Dockerfile
RUN apt-get update -y && apt-get upgrade -y && apt install -y build-essential libssl-dev pkg-config \
    && apt install -y python3-full python3-dev pipx \
    && pipx ensurepath \
    && ln -s /usr/bin/python3 /usr/bin/python
```