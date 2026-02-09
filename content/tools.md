---
title: Tools
date: 2026-02-04
draft: true
tags:
---
Sync changes with the actual content folder of quartz:
```bash
rsync -avh --progress --delete /home/jesus/Google\ Drive/Zettelkasten/carloyjesus/ /home/jesus/carloyjesus/content
```

Build and publish: 
```bash
npx quartz sync
```


Build 

```bash
npx quartz build --serve
```



