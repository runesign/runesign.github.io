---
# date: '{{ .Date }}'
lastmod: { { .Date } } #更新时间
draft: true
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
---
