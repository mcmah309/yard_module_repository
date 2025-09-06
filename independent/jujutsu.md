```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "jujustu version control (jj). https://github.com/jj-vcs/jj/releases"
args:
    required:
        - version # e.g `v0.33.0`
```
```Dockerfile
RUN apt-get install curl -y \
    && curl -L -o jj.tar.gz https://github.com/jj-vcs/jj/releases/download/{{ version }}/jj-{{ version }}-x86_64-unknown-linux-musl.tar.gz \
    && tar -xvzf jj.tar.gz \
    && mv jj /usr/local/bin/ \
    && rm jj.tar.gz \
    && jj --version
```