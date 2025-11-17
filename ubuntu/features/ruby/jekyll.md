```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Jekyll package for Ruby. Requires Ruby."
```
```Dockerfile
RUN gem install jekyll bundler
```