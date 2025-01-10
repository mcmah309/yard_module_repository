```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "python module with just the interpreter"
```
```Dockerfile
RUN apt install -y python3 \
    && ln -s /usr/bin/python3 /usr/bin/python
```