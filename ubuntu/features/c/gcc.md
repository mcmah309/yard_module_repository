```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "clang development module"
args:
    optional:
        - version
```
```Dockerfile
{% if version %}
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    build-essential \
    gdb \
    # Add the Ubuntu Toolchain PPA for latest GCC versions
    && add-apt-repository ppa:ubuntu-toolchain-r/test -y \
    && apt-get update -y \
    # Install the latest specific GCC/G++ version
    && apt-get install -y --no-install-recommends --no-install-suggests \
    gcc-{{ version }} \
    g++-{{ version }} \
    # Install the debug package for better GDB experience
    gcc-{{ version }}-plugin-dev \
    && rm -rf /var/lib/apt/lists/* \
    # Set the latest GCC/G++ as the default 'gcc' and 'g++' commands
    # Priority '100' should be high enough to override the 'build-essential' default
    && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-{{ version }} 100 \
    --slave /usr/bin/g++ g++ /usr/bin/g++-{{ version }} \
    && update-alternatives --config gcc \
{% else %}
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    build-essential \
    gdb \
{% endif %}
    && rm -rf /var/lib/apt/lists/*
```