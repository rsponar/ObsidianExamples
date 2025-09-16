---
tags:
  - Networkdocumentation
  - Entity
Date: <%tp.file.creation_date("YYYY-MM-DD") %>
Description: <%* const description = await tp.system.prompt("Enter Description or leave empty"); %><% description %>
net_parent:
net_entity_type: <%* const types = ["Virtual Machine", "Hardware", "Firewall"]; const choice = await tp.system.suggester(types, types); const output = choice; %><% output %>
---

<%*
  // Get Entity Name
  const newTitle = await tp.system.prompt("Enter entity name");
  
  // Rename the note await tp.file.rename(newTitle); 
  await tp.file.rename(newTitle);

  // Move this note to the desired folder (change 'Static' to your folder name)
  await tp.file.move("Documentation/" + newTitle);
%>

## Interfaces/IPs

```base
filter:
formulas:
  Untitled: ""
properties:
  file.name:
    displayName: Name
  note.net_ip:
    displayName: IP Address
  note.net_fqdn:
    displayName: FQDN
  note.net_subnet:
    displayName: Subnet
views:
  - type: table
    name: Table
    filters:
      and:
        - file.tags.contains("Interface")
        - net_parent == this
    order:
      - file.name
      - net_ip
      - net_fqdn
      - net_subnet
      - Description
    sort:
      - property: net_ip
        direction: DESC
    columnSize:
      note.net_ip: 142
      file.name: 140
      note.net_fqdn: 217
      note.Description: 225

```

## Services

```base
filter:
formulas:
  Untitled: ""
properties:
  file.name:
    displayName: Name
  note.net_port:
    displayName: Port
  note.net_protocol:
    displayName: Protocol
  note.net_parent_interface:
    displayName: Parent Interface
views:
  - type: table
    name: Table
    filters:
      and:
        - file.tags.contains("Service")
        - net_parent == this
    order:
      - file.name
      - net_port
      - net_protocol
      - Description
      - net_parent_interface
    sort:
      - property: net_ip
        direction: DESC
    columnSize:
      note.net_ip: 142
      file.name: 140
      note.net_fqdn: 217
      note.Description: 225

```