---
tags:
  - Homelab
  - Subnet
  - Networkdocumentation
Date: <%tp.file.creation_date("YYYY-MM-DD") %>
CIDR: <%* const cidr = await tp.system.prompt("Enter CIDR (e.g. 10.10.0.0/16)"); %><% cidr %>
net_subnet_type: <%* const types = ["VLAN", "NSX", "VPC"]; const choice = await tp.system.suggester(types, types); const output = choice; %><% output %>
net_vlanid: <%* let vlanID = ""; if(choice === "VLAN"){vlanID = await tp.system.prompt("Enter VLAN ID");}%><% vlanID %>
---

<%*
  // Extract subnet ID by splitting on "/" and taking the first part const 
  subnetID = cidr.split("/")[0];

  // Prompt user for Description
  const description = await tp.system.prompt("Enter Description for this Subnet");
  
  // Compose new title
  const newTitle = `${subnetID} - ${description}`; 
  
  // Rename the note await tp.file.rename(newTitle); 
  await tp.file.rename(newTitle);

  // Move this note to the desired folder (change 'Static' to your folder name)
  await tp.file.move("Documentation/Network/Subnets/" + newTitle);
%>

| Network     | <% cidr %>               |
| ----------- | ------------------------ |
| Subnetmask  | 255.255.255.0            |
| Gateway     |                          |
| DNS servers | 192.168.5.90,192.168.5.1 |
| VLAN        | <% vlanID %>             |

## Subnet Address overview

```base
filter:
formulas:
  Untitled: ""
properties:
  file.name:
    displayName: Interface
  note.net_fqdn:
    displayName: FQDN
  note.net_parent:
    displayName: Parent
  note.net_entity_type:
    displayName: Type
  note.net_interface_type:
    displayName: Interface Type
  note.net_ip:
    displayName: IP Address
views:
  - type: table
    name: Table
    filters:
      and:
        - file.tags.contains("Networkdocumentation")
        - net_subnet == this
    order:
      - net_ip
      - net_fqdn
      - net_parent
      - file.name
      - net_interface_type
      - Description
    sort:
      - property: net_ip
        direction: ASC
      - property: net_interface_type
        direction: DESC
    columnSize:
      note.net_ip: 257
      file.name: 238
      note.Description: 230
      note.net_fqdn: 194

```