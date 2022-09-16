---
title: "npm global installed path config"
date: 2021-10-18
categories:
  - note
tags:
  - javascript
toc: true
toc_label: "Outline"
toc_sticky: true
toc_icon: "box-open"
header:
  teaser: ./assets/teasers/code-bg.png

---

In order to fix `Error: EACCES: permission denied, access '/usr/lib/node_modules'`,
a solution will be set installed path non-root. Here's how to set it.

```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
```

This can see if config set properly

```bash
npm config list
```

Output will be like this

```bash
; cli configs
metrics-registry = "https://registry.npmjs.org/"
scope = ""
user-agent = "npm/6.14.15 node/v14.18.1 linux x64"

; userconfig /home/wesley/.npmrc
prefix = "/home/wesley/.npm-global"

; node bin location = /usr/local/bin/node
; cwd = /mnt/c/Users/Wesley/GitHub/wesleych3n.github.io/_posts
; HOME = /home/wesley
; "npm config ls -l" to show all defaults.
```

Add bin path to `$PATH` variable

```bash
if [ -d $HOME/.npm-global ]; then
  export PATH=$HOME/.npm-global/bin:$PATH
fi
```
