# VSCode Server Swift MOD

![Swift](https://i.imgur.com/1fpf5HJ.png)

This MOD installs Swift binaries to be used in VSCode at startup. [linuxserver](https://www.linuxserver.io/)'s [code-server image](https://hub.docker.com/r/linuxserver/code-server) is used as core

> **Note** 
>
> You also need the [code-server-extension-arguments](https://github.com/linuxserver/docker-mods/tree/code-server-extension-arguments) MOD to supply the official VS marketplace where [sswg.swift-lang](https://marketplace.visualstudio.com/items?itemName=sswg.swift-lang) exists. 
> 
> This MOD will try to install it if you provide the correct envs.

## TODO
- [Merge request](https://github.com/linuxserver/docker-mods/tree/template) for this MOD to be included in linuxserver [MOD list](https://mods.linuxserver.io/?mod=code-server) ([example](https://github.com/linuxserver/docker-mods/pull/538))

### Full example
```sh
docker run -d \
  --name=vscodeserver \
  --restart unless-stopped \
  -p 8443:8443 \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Europe/Bucharest \
  -e DOCKER_MODS="linuxserver/mods:code-server-extension-arguments|rursache/vscode-swift-linuxserver-mod" \
  -e VSCODE_EXTENSION_IDS="sswg.swift-lang"\
  -e EXTENSIONS_GALLERY='{"serviceUrl": "https://marketplace.visualstudio.com/_apis/public/gallery", "cacheUrl": "https://vscode.blob.core.windows.net/gallery/index", "itemUrl": "https://marketplace.visualstudio.com/items"}' \
  -v /home/USER/.vscodeserver/config:/config \
  -v /home/USER/.vscodeserver/projects:/projects \
  -v /opt/swift:/swift \
  lscr.io/linuxserver/code-server:latest
```
