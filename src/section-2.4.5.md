# Subnetworks cross zones

Subnets are per region, but because zones fit within a region; subnets can cross zones within that region.

```mermaid
graph TB
    subgraph nw1[Network 1]
        subgraph region1[Region 1]
            subgraph sn1[Subnet 1]
                subgraph zonea[Zone A]
                    vma[VM A 10.0.0.2]
                end
                subgraph zoneb[Zone B]
                    vmb[VM B 10.0.0.3]
                end
            end
        end
    end
```

* VMs can be on the same subnet but in different zones.
* Single firewall rule can apply to both VMs

### Reserved IPs

Note that the graph above has the VMs starting at address `.2` and the next is `.3`, reference [reserved ip ranges](https://cloud.google.com/vpc/docs/vpc#reserved_ip_addresses_in_every_subnet)

|    Reserved IP | Purpose         |
| -------------: | --------------- |
|        x.x.x.0 | Network Gateway |
|        x.x.x.1 | Subnet Gateway  |
| second to last | broadcast       |
|           last | broadcast       |