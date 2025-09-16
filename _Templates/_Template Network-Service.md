---
tags:
  - Networkdocumentation
  - Service
Date: <%tp.file.creation_date("YYYY-MM-DD") %>
Description: <%* const description = await tp.system.prompt("Enter Description or leave empty"); %><% description %>
net_parent: 
net_parent_interface:
net_protocol: <%* const types = ["TCP", "UDP", "ICMP"]; const choice = await tp.system.suggester(types, types); const output = choice; %><% output %>
net_port: <%* const port = await tp.system.prompt("Enter Port number"); %><% port %>
Application:
---

<%*
  // Get Parent entity
  const parent_entity = await tp.system.prompt("Enter parent entity");

  // Compose new title
  const newTitle = `${parent_entity}_`; 
  
  // Rename the note await tp.file.rename(newTitle); 
  await tp.file.rename(newTitle);

  // Move this note to the desired folder (change 'Static' to your folder name)
  await tp.file.move("Documentation/Network/Services/" + newTitle);
%>