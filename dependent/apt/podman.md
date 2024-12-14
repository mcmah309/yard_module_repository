```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Podman in Podman"
args:
  optional:
    - include_volumes
```
```Dockerfile
# Podman in Podman
# Tips:
# - Run outer with with `--privileged`
# Known issues: 
# - some containers may need args like `--net=host` on the inside and outside container


RUN apt install -y podman \
    && tee /etc/containers/registries.conf > /dev/null <<EOF
[registries]
[registries.block]
registries = []

[registries.insecure]
registries = []

[registries.search]
registries = ["docker.io", "quay.io"]
EOF

# Root podman containers location. (For users ~/.local/share/containers)
{% if include_volumes %}
VOLUME /var/lib/containers
{% endif %}
```
