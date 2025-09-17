---
Date: <%tp.file.creation_date("YYYY-MM-DD") %>
tags:
  - Project
status: open
---

<% 
// Get Title of project
const newTitle = await tp.system.prompt("Enter Project title");

// Rename the note 
await tp.file.rename(newTitle);

// Move this note to the desired folder (change 'Static' to your folder name)
await tp.file.move("/Projects/" + newTitle);
%>

## Related Tasks

```base
filter:
formulas:
  Untitled: ""
properties:
  file.name:
    displayName: Task
  note.task_order:
    displayName: Order
  note.status:
    displayName: Status
views:
  - type: table
    name: Table
    filters:
      and:
        - project == this
        - file.tags.contains("Task")
    order:
      - task_order
      - file.name
      - status
    sort:
      - property: task_order
        direction: ASC
      - property: Date
        direction: ASC
    columnSize:
      note.task_order: 78
      file.name: 238

```



## 📖Documentation


## 🔗Resources

