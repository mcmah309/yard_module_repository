```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "git module"
```
```Dockerfile
RUN apt-get update -y && apt-get upgrade -y && apt install -y git
```
