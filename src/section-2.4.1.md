# 3 VPC network types

### Default
* Every project
* One subnet per region
* Default firewall rules

> Default is actuall an auto mode network with [default firewall rules](https://cloud.google.com/vpc/docs/firewalls#more_rules_default_vpc)
> setup for ingressing ICMP, RDP, SSH and all protocols/ports for
> traffic within the network

### Auto Mode
* Default network
* One subnet per region
* Regional IP allocation
* Fixed `/20` subnetwork per region
* Expandable up to `/16`

> All subnets fit within `10.128.0.0/9` CIDR

### Custom Mode
* No default subnets created
* Full control of IP ranges
* Regional IP allocation
* Expandable to IP ranges you specify

> You can convert an Automode network to a Custom mode network,
> but this is a uni-directional conversion and cannot be undone
