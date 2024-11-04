### Node launch deep dive:Scheduling
![scheduling](image-1.png)

### Batching
![alt text](image-2.png)

### Binpacking
![alt text](image-3.png)
kube-scheduler is using searching for node, but karpenter is not like that because of large space, gerenation is karpenter use

![alt text](image-4.png)
What happen if there is no available capacity in the zone user perfer?
What happen if the pods and nodes changes while we’re doing the math?
the situation is changed when we execute
kube-scheduler is using searching for node, but karpenter is not like that because of large space, gerenation is karpenter use

### Launch decsion
![alt text](image-5.png)
Spot allocation strategy is find out the cheapest instance type but is not about to be disrupted through EC2 Fleet API


### Onboarding Karpenter
![alt text](image-6.png)
![alt text](image-7.png)
![alt text](image-8.png)
![alt text](image-9.png)
![alt text](image-10.png)
![alt text](image-11.png)
![alt text](image-12.png)
![alt text](image-13.png)
![alt text](image-14.png)
Simply remove the old custsom ami `ami-123`, that point the ami drift
![alt text](image-15.png)
Conslidation is related to bin-packing and choose the cheapest instance for user
![alt text](image-16.png)

### Node disruption deep dive
Disruption is event happened in cluster cause to remove node
PDB is essential for using Karpenter
![alt text](image-17.png)
![alt text](image-18.png)


## Reference
[re:Invent 2023 | 利用 Karpenter 的力量扩展、优化和升级 Kubernetes](https://www.bilibili.com/video/BV1cj411L7qh/?spm_id_from=333.337.search-card.all.click&vd_source=2b3537c234d02f82c699d6ee46f94a38)