### Rate limit service
Rate limit configuration overview.

```
{
  "type": "grpc_service",
  "config": {
    "cluster_name": "..."
  }
}
```
- **type**</br>
	([required](#), string) Specifies the type of rate limit service to call. Currently the only supported option is grpc_service which specifies Lyft��s global rate limit service and associated IDL.

- **config**</br>
	([required](#), object) Specifies type specific configuration for the rate limit service.


- **cluster_name**</br>
	([required](#), string) Specifies the cluster manager cluster name that hosts the rate limit service. The client will connect to this cluster when it needs to make rate limit service requests.





## ����
- [��һ��](../v1APIreference.md)
- [��ҳĿ¼](../README.md)