```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Configure git"
args:
  required:
    - user_name
    - email
  optional:
    - include_volumes
```
```Dockerfile
RUN git config --global user.name {{ user_name }} && \
    git config --global user.email {{ email }}

{% if include_volumes %}
VOLUME /root/.ssh
{% endif %}
```
