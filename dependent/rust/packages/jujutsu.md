```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "jujustu version control (jj)"
```
```Dockerfile
RUN cargo binstall --strategies crate-meta-data jj-cli
```