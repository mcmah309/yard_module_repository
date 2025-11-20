```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: |
  Configure git

  Volumes:
  - ${HOME:-/root}:/.ssh
args:
  required:
    - user-name
    - email
```
```Dockerfile
RUN git config --global user.name {{ user-name }} \
    && git config --global user.email {{ email }}
```
