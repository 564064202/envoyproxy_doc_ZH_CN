## ����ʱ����

���μ�Ⱥ֧����������ʱ���ã�

### �����������

- **health_check.min_interval**</br>
�������������Сֵ��Ĭ��ֵΪ0������״��[�����](../../v1APIreference/Clustermanager/Cluster/Healthchecking.md)������`min_interval`��`max_interval`֮�䡣

- **health_check.max_interval**</br>
��������������ֵ��Ĭ��ֵ��MAX_INT���������������`min_interval`��`max_interval`֮�䡣

- **health_check.verify_cluster**</br>
[������������](../../v1APIreference/Clustermanager/Cluster/Healthchecking.md)��Զ�̷���Ⱥ��д����Ӧ�����Ԥ�ڵ����η�����֤�����������İٷֱȡ�



### ��Ⱥ�쳣���
�й���Ⱥ�쳣���ĸ�����Ϣ����μ��쳣ֵ���[�ܹ�����](../../Introduction/Architectureoverview/Outlierdetection.md)���쳣ֵ���֧�ֵ�����ʱ�����뾲̬���ò�����ͬ������


- **outlier_detection.consecutive_5xx**</br>
�����쳣ֵ����[consecutive_5XX](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.consecutive_gateway_failure**</br>
�����쳣ֵ����[connected_gateway_failure](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.interval_ms**</br>
���쳣ֵ����е�[interval_ms](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.base_ejection_time_ms**</br>
�����쳣ֵ����[base_ejection_time_ms](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.max_ejection_percent**</br>
�쳣ֵ����е�[max_ejection_percent](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.enforcing_consecutive_5xx**</br>
���쳣ֵ�����ִ��[enforcing_consecutive_5xx](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.enforcing_consecutive_gateway_failure**</br>
���쳣ֵ�����ִ��[enforcing_consecutive_gateway_failure](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.enforcing_success_rate**</br>
���쳣ֵ�����ִ��[enforcing_success_rate](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.success_rate_minimum_hosts**</br>
�쳣ֵ����е�[success_rate_minimum_hosts](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.success_rate_request_volume**</br>
�쳣ֵ����е�[success_rate_request_volume](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

- **outlier_detection.success_rate_stdev_factor**</br>
�쳣ֵ����е�[success_rate_stdev_factor](../../v1APIreference/Clustermanager/Cluster/Outlierdetection.md)����

### ����
- **upstream.healthy_panic_threshold**</br>
[�ֻ���ֵ](../../Introduction/Architectureoverview/Loadbalancing.md)�ٷֱ����á�Ĭ��Ϊ50����

- **upstream.use_http2**</br>
����Ⱥ���Ƿ�ʹ��[http2����](../../v1APIreference/Clustermanager/Cluster.md)������Ϊ0������HTTP/2��Ĭ��Ϊ���á�

- **upstream.weight_enabled**</br>
�����ƿ��أ����ڴ򿪻�رռ�Ȩ���ؾ��⡣�������Ϊ��0�������ü�Ȩ���ؾ��⡣Ĭ��Ϊ���á�



### �����֪���ؾ���
- **upstream.zone_routing.enabled**</br>
����·�ɵ���ͬ���������������İٷֱȡ�Ĭ��Ϊ100��������

- **upstream.zone_routing.min_cluster_size**</br>
���Գ��������֪·�ɵ�����Ⱥ������С��С��Ĭ��ֵΪ6���������Ⱥ����СС��`min_cluster_size`���������֪·�ɽ�����ִ�С�

## �۶�
- **circuit_breakers.\<cluster_name>.\<priority>.max_connections**</br>
[��·���������������](../../v1APIreference/Clustermanager/Cluster/Circuitbreakers.md)

- **circuit_breakers.\<cluster_name>.\<priority>.max_pending_requests**</br>
[��·������������������](../../v1APIreference/Clustermanager/Cluster/Circuitbreakers.md)

- **circuit_breakers.\<cluster_name>.\<priority>.max_requests**</br>
[��·�����������������](../../v1APIreference/Clustermanager/Cluster/Circuitbreakers.md)

- **circuit_breakers.\<cluster_name>.\<priority>.max_retries**</br>
[��·��������Դ�������](../../v1APIreference/Clustermanager/Cluster/Circuitbreakers.md)




## ����
- [��һ��](../Clustermanager.md)
- [��ҳĿ¼](../../README.md)