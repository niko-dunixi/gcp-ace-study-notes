# Google VPC is global


```mermaid
graph LR
    onprem[On Prem];
    subgraph vpc[Cloud VPC Network]
        vpngw[VPN Gateway];

        subgraph sn_uswest1[Subnet 10.10.0.0/26 us-west1]
            vma[VM A];
        end

        subgraph sn_useast1[Subnet 10.50.0.0/26 us-east1]
            vmb[VM b];
        end
        vpngw ---> vma;
        vpngw ---> vmb;
        vma --> vmb;
        vmb --> vma;
    end
    onprem ----> vpngw
```

Because VPC is global, you can use a single VPN to connect your
on-prem to the VPC network. Even though the two VMs are in discrete
regions, they are on the same VPC network so they can communciate
with internal IPs.