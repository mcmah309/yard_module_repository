```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "clang development module"
args:
    optional:
        - version
```
```Dockerfile
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
{% if version %}
    lsb-release \
    wget \
    software-properties-common \
    gnupg \
    && wget https://apt.llvm.org/llvm.sh \
    && chmod +x llvm.sh \
    && ./llvm.sh {{ version }} \
    && rm ./llvm.sh \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    clang-{{ version }} \
    clangd-{{ version }} \
    clang-tools-{{ version }} \
    clang-format-{{ version }} \
    clang-tidy-{{ version }} \
    lldb-{{ version }} \
    lld-{{ version }} \
{% else %}
    clang \
    clangd \
    clang-tools \
    clang-format \
    clang-tidy \
    lldb \
    lld \
{% endif %}
    && rm -rf /var/lib/apt/lists/*
```