```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Ruby module"
```
```Dockerfile
RUN apt-get update -y && apt-get upgrade -y && apt-get install -y ruby-full build-essential zlib1g-dev
ENV GEM_HOME ${HOME}/gems
ENV PATH ${PATH}:${HOME}/gems/bin
```