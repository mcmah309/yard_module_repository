```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "chrome install (useful for headless testing)"
```
```Dockerfile
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    wget \
    && rm -rf /var/lib/apt/lists/*
RUN wget -q --show-progress -O /tmp/chrome.deb 'https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb' \
&& dpkg -i /tmp/chrome.deb \
&& apt-get install -f -y \
&& google-chrome --version \
rm /tmp/chrome.deb
```