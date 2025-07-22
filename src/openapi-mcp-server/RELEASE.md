Note: This is a fork from v1 of https://github.com/snaggle-ai/openapi-mcp-server. The library took a different direction with v2 which is not compatible with our development approach.

Forked to upgrade vulnerable dependencies and easier setup.


## Publish:

### Smithery
Check that deployment was successful at https://smithery.ai/server/@GravitonINC/xeenon-mcp-server

# NPM

```bash
npm version patch
npm run build
npm publish
```


# Docker
```bash
VERSION=[INSERT VERSION]
docker build -t gravitonxyz/xeenon-mcp-server:latest -t gravitonxyz/xeenon-mcp-server:$VERSION .
docker push gravitonxyz/xeenon-mcp-server:latest
docker push gravitonxyz/xeenon-mcp-server:$VERSION
```