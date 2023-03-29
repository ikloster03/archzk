---
{{ $subName := substr .Name 13 }}
title: "{{ replace $subName "-" " " | title}}"
date: {{ .Date }}
description: ""
tags: []
ShowToc: true
ShowBreadCrumbs: true
draft: false
---