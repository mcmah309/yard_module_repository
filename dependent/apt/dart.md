```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Dart module"
args:
  optional:
    - dart_version
    - channel
```
```Dockerfile
# https://dart.dev/get-dart#install-a-debian-package

ARG dart_ver={{ dart_version | default (value="3.6.2") }}

RUN apt install wget -y \
    && wget https://storage.googleapis.com/dart-archive/channels/{{ channel | default (value="stable") }}/release/${dart_ver}/linux_packages/dart_${dart_ver}-1_amd64.deb \
    && dpkg -i dart_${dart_ver}-1_amd64.deb \
    && apt install -f -y \
    && rm dart_${dart_ver}-1_amd64.deb

ENV PATH ${PATH}:/root/.pub-cache/bin
```
