```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Dioxus. Also depends on cargo being installed."
args:
    optional:
    - version # e.g. `0.6.0-alpha.4` do not include the `v`
```
```Dockerfile
# From: https://dioxuslabs.com/learn/0.6/getting_started
RUN cargo install cargo-binstall && cargo binstall dioxus-cli {% if version %} --version {{version}} --force {% endif %}
RUN apt-get update -y && apt-get upgrade -y && apt install -y \
libwebkit2gtk-4.1-dev \
build-essential \
curl \
wget \
file \
libxdo-dev \
libssl-dev \
libayatana-appindicator3-dev \
librsvg2-dev
```