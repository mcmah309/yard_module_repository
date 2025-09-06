```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "jujustu version control (jj)"
```
```Dockerfile
RUN curl -L -o jj.tar.gz https://github.com/jj-vcs/jj/releases/download/v0.33.0/jj-v0.33.0-x86_64-unknown-linux-musl.tar.gz \
    && tar -xvzf jj.tar.gz \
    && mv jj /usr/local/bin/ \
    && rm jj.tar.gz \
    && jj --version
```