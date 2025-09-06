```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "A pre-module script to run and make sure the next module is always up to date during rebuilds"
```
```Dockerfile
RUN sudo apt-get update -y \
 && sudo apt-get upgrade -y \
 && sudo apt-get autoremove -y
```
