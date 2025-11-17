```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/mcmah309/containeryard/master/src/schemas/yard-module-schema.json

description: "Firebase cli module. Needs Node.js."
```
```Dockerfile
RUN npm install -g firebase-tools
```

Users can then run `firebase login` to setup for their project
