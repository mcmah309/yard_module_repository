```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "protoc module"
```
```Dockerfile
RUN apt install -y protobuf-compiler
```