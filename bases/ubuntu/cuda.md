```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Ubuntu module with cuda."
```
```Dockerfile
FROM nvidia/cuda:12.6.3-cudnn-devel-ubuntu24.04

RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests ca-certificates \
    && update-ca-certificates
```