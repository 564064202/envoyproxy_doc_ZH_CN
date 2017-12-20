## ��Ⱥ����


- [��Ⱥ](Clustermanager/Cluster.md)
- [�쳣���](Clustermanager/Outlierdetection.md)
- [��Ⱥ���ַ���](Clustermanager/Clusterdiscoveryservice.md)
- [�����ַ���](Clustermanager/Servicediscoveryservice.md)


### Cluster manager
Cluster manager architecture overview.

```
{
  "clusters": [],
  "sds": "{...}",
  "local_cluster_name": "...",
  "outlier_detection": "{...}",
  "cds": "{...}"
}
```
- **clusters**</br>
	([required](#), array) A list of upstream clusters that the cluster manager performs service discovery, health checking, and load balancing on.

- **sds**</br>
	([sometimes required](#), object) If any defined clusters use the sds cluster type, a global SDS configuration must be specified.

- **local_cluster_name**</br>
	([optional](#), string) Name of the local cluster (i.e., the cluster that owns the Envoy running this configuration). In order to enable zone aware routing this option must be set. If local_cluster_name is defined then clusters must contain a definition of a cluster with the same name.

- **outlier_detection**</br>
	([optional](#), object) Optional global configuration for outlier detection.

- **cds**</br>
	([optional](#), object) Optional configuration for the cluster discovery service (CDS) API.



## ����
- [��һ��](../v1APIreference.md)
- [��ҳĿ¼](../README.md)