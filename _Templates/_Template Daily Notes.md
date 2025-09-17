---
tags:
  - daily
---
## ✏Scratchpad

## ✅open Tasks

```base
views:
  - type: table
    name: Table
    filters:
      and:
        - file.tags.contains("Task")
        - file.name != "_Template Task"
        - status != "done"
    order:
      - file.name
      - status
      - file.ctime
    columnSize:
      file.name: 500
      note.status: 110
      file.ctime: 150

```
## 🏆open Projects

```base
properties:
  file.name:
    displayName: Project
views:
  - type: table
    name: Table
    filters:
      and:
        - file.tags.contains("Project")
        - status != "done"
        - file.name != "_Template Project"
    order:
      - file.name
      - status
      - file.ctime
    columnSize:
      file.name: 500
      note.status: 110
      file.ctime: 150

```