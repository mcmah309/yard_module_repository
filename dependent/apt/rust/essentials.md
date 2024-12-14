```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Essential rust packages adjacent like openssl"
```
```Dockerfile
# libssl-dev: Needed for openssl certificates (may need to add the pkg files to PKG_CONFIG_PATH)
# libasound2-dev: Needed for alsa (may need to add the pkg files to PKG_CONFIG_PATH)
# pkg-config: Quering local libraries for compilation. Needed by rustc.
RUN apt-get update && apt install -y libssl-dev libasound2-dev pkg-config
```
