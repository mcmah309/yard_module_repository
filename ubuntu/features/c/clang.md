```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "clang development module"
args:
    optional:
        - clang_version
```
```Dockerfile
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends --no-install-suggests \
{% if clang_version %}
    lsb-release \
    wget \
    software-properties-common \
    gnupg \
    && wget https://apt.llvm.org/llvm.sh \
    && chmod +x llvm.sh \
    && ./llvm.sh {{ clang_version }} \
    && rm ./llvm.sh \
    && apt-get install -y --no-install-recommends --no-install-suggests \
    clang-{{ clang_version }} \
    clangd-{{ clang_version }} \
    clang-tools-{{ clang_version }} \
    clang-format-{{ clang_version }} \
    clang-tidy-{{ clang_version }} \
    lldb-{{ clang_version }} \
    lld-{{ clang_version }} \
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