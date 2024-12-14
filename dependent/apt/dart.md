```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Dart module"
args:
  optional:
    - dart_version
```
```Dockerfile
# https://dart.dev/get-dart#install-a-debian-package

ARG dart_ver={{ dart_version | default (value="3.5.2") }}

RUN apt install wget -y \
    && wget https://storage.googleapis.com/dart-archive/channels/stable/release/${dart_ver}/linux_packages/dart_${dart_ver}-1_amd64.deb \
    && dpkg -i dart_${dart_ver}-1_amd64.deb \
    && apt install -f -y \
    && rm dart_${dart_ver}-1_amd64.deb
```
