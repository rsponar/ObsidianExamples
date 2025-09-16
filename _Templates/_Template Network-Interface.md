---
tags:
  - Networkdocumentation
  - Interface
Date: <%tp.file.creation_date("YYYY-MM-DD") %>
Description: <%* const description = await tp.system.prompt("Enter Description or leave empty"); %><% description %>
net_subnet:
net_ip: <%* const ip = await tp.system.prompt("Enter IP (e.g. 10.10.10.1)"); %><% ip %>
net_fqdn: <%* const fqdn = await tp.system.prompt("Enter fqdn or leave empty (e.g. lin-01.lab.sponar.de)"); %><% fqdn %>
net_parent:
net_interface_type: <%* const types = ["virtual", "physical", "vip", "dhcp-scope", "Reservation", "Gateway"]; const choice = await tp.system.suggester(types, types); const output = choice; %><% output %>
---

<%*
  // Get Parent entity
  const parent_entity = await tp.system.prompt("Enter parent entity");
  
  // Compose new title
  const newTitle = `${parent_entity}_nic01`; 
  
  // Rename the note await tp.file.rename(newTitle); 
  await tp.file.rename(newTitle);

  // Move this note to the desired folder (change 'Static' to your folder name)
  await tp.file.move("Documentation/Network/Interfaces/" + newTitle);
%>