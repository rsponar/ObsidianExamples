---
tags:
  - Task
Date: <%tp.file.creation_date("YYYY-MM-DD") %>
project:
task_order:
status: in Progress
---
<% 
// Get Title of Task
const newTitle = await tp.system.prompt("Enter Task title");

// Rename the note 
await tp.file.rename(newTitle);

// Move this note to the desired folder (change according to your folder name)
await tp.file.move("/Documentation/Tasks" + newTitle);
%>
## 📖Steps

## 🔗Resources