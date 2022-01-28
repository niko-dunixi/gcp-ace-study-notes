# Networks isolate systems

#### Project

| Region | Network #1 | Network #2 | Network #3 | Network #... |
| --- | --- | --- | --- | --- |
| us-east1 | VM A | VM C | VM D |     |
| europe-west1 | VM B |      |      |     |

* VM A and VM B can communicate over internal IPs even though they are in different regions.
* VM C and VM D must communicate over external IPs even though they're in the same region.
