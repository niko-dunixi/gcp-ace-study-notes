# Expand subnets without re-creating instances

You can expand the network ranges without having to shutdown any of your instances.

The things to keep in mind while doing this:
* New subnet masks cannot overlap other subnets in any region within the same VPC
* Each IP range must be a unique and valid CIDR
* The new ranges have to fall within valid _internal_ ranges, you cannot encompase a public IP within your CIDR.
* You can't make your subnet range narrower or broader than a [restricted range](https://cloud.google.com/vpc/docs/vpc#restricted-ranges)
* You can expand, but you can't shrink; which makes this a permanent unidirectional change.
* Auto mode can be expanded from `/20` to `/16`
  * If you need a larger IP range, you can convert the auto mode subnetwork to a custom mode network for full control

> Avoid large subnets! The larger the subnet the more likely
> you will collide with other IPs when you start adding more
> network interfaces and VPC peering or when you configure a
> VPN to an on-prem network.

```mermaid
graph
subgraph project[Project]

nw[Network]

subgraph regiona[Region A]
    sn_a[Subnet 172.16/24]
    sn_b[Subnet 10.126/16]
end
subgraph regionb[Region B]
    sn_c[Subnet 10.130/16]
end
subgraph regionc[Region C]
    sn_d[Subnet 10.132/16]
end

nw --- sn_a;
nw --- sn_b;
nw --- sn_c;
nw --- sn_d;

sn_a --- vm_a[VM]
sn_b --- vm_b[VM]
sn_c --- vm_c[VM]
sn_d --- vm_d[VM]

end
```