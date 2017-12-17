## ͳ��

- [����](#����)
- [�������ͳ��](#�������ͳ��)
- [��Ⱥ���ͳ��](#��Ⱥ���ͳ��)
- [��̬HTTPͳ��](#��̬HTTPͳ��)
- [��̬HTTP������ͳ��](#��̬HTTP������ͳ��)
- [����������̬HTTPͳ��](#����������̬HTTPͳ��)
- [���ؾ���ͳ��](#���ؾ���ͳ��)
- [���ؾ����Ӽ�ͳ��](#���ؾ����Ӽ�ͳ��)

### ����
��Ⱥ��������ͳ������Ϊ`cluster_manager.`�������ͳ���������κ�`:`�ַ���ͳ�������еı��滻Ϊ`_`��

|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	cluster_added	|	Counter	|	��Ⱥ����ӣ�ͨ����̬���û�CDS��	|
|	cluster_modified	|	Counter	|	��Ⱥ���޸ģ�ͨ��CDS��	|
|	cluster_removed	|	Counter	|	��Ⱥ��ɾ����ͨ��CDS��	|
|	total_clusters	|	Gauge	|	��ǰ���ص�Ⱥ������	|

ÿ��Ⱥ������һ����`cluster.<name>.`Ϊ����ͳ������ͳ�����£�

|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	upstream_cx_total	|	Counter	|	��������	|
|	upstream_cx_active	|	Gauge	|	�ܻ������	|
|	upstream_cx_http1_total	|	Counter	|	��HTTP/1.1������	|
|	upstream_cx_http2_total	|	Counter	|	��HTTP/2������	|
|	upstream_cx_connect_fail	|	Counter	|	������ʧ��	|
|	upstream_cx_connect_timeout	|	Counter	|	�����ӳ�ʱ	|
|	upstream_cx_connect_attempts_exceeded	|	Counter	|	������������ʧ�ܳ������õ����ӳ���	|
|	upstream_cx_overflow	|	Counter	|	��Ⱥ���Ӷ�·��������ܴ���	|
|	upstream_cx_connect_ms	|	Histogram	|	���ӽ�������	|
|	upstream_cx_length_ms	|	Histogram	|	���ӳ��Ⱥ���	|
|	upstream_cx_destroy	|	Counter	|	�ܻٻ�������	|
|	upstream_cx_destroy_local	|	Counter	|	�������ڱ��ر�����	|
|	upstream_cx_destroy_remote	|	Counter	|	�����ӱ�Զ������	|
|	upstream_cx_destroy_with_active_rq	|	Counter	|	�ܹ����ӱ�1�����������	|
|	upstream_cx_destroy_local_with_active_rq	|	Counter	|	�ܹ���1��������ڱ�������	|
|	upstream_cx_destroy_remote_with_active_rq	|	Counter	|	�ܹ����ӱ�1�������Զ������	|
|	upstream_cx_close_notify	|	Counter	|	������ͨ��HTTP/1.1���ӹرձ�ͷ��HTTP/2 GOAWAY�ر�	|
|	upstream_cx_rx_bytes_total	|	Counter	|	�յ��������ֽ�����	|
|	upstream_cx_rx_bytes_buffered	|	Gauge	|	���յ���ǰ����������ֽ�	|
|	upstream_cx_tx_bytes_total	|	Counter	|	���͵������ֽ�����	|
|	upstream_cx_tx_bytes_buffered	|	Gauge	|	���͵�ǰ����������ֽ�	|
|	upstream_cx_protocol_error	|	Counter	|	Э��������������	|
|	upstream_cx_max_requests	|	Counter	|	�������������ر���������	|
|	upstream_cx_none_healthy	|	Counter	|	����û�н�����������û�н�����������	|
|	upstream_rq_total	|	Counter	|	������	|
|	upstream_rq_active	|	Gauge	|	�ܻ����	|
|	upstream_rq_pending_total	|	Counter	|	�������ӳ����ӵ���������	|
|	upstream_rq_pending_overflow	|	Counter	|	���ӳض�·�����ʧ�ܵ���������	|
|	upstream_rq_pending_failure_eject	|	Counter	|	�������ӳ�����ʧ�ܶ�����ʧ�ܵ���������	|
|	upstream_rq_pending_active	|	Gauge	|	�ȴ����ӳ����ӵĻ��������	|
|	upstream_rq_cancelled	|	Counter	|	��ȡ���ӳ�����֮ǰ��ȡ������������	|
|	upstream_rq_maintenance_mode	|	Counter	|	����ά��ģʽ��������������503�����������	|
|	upstream_rq_timeout	|	Counter	|	��ʱ�ȴ���Ӧ����������	|
|	upstream_rq_per_try_timeout	|	Counter	|	ÿ�γ��Գ�ʱ����������	|
|	upstream_rq_rx_reset	|	Counter	|	��Զ�����õ���������	|
|	upstream_rq_tx_reset	|	Counter	|	�ڱ������õ���������	|
|	upstream_rq_retry	|	Counter	|	�������Դ���	|
|	upstream_rq_retry_success	|	Counter	|	�������Գɹ�����	|
|	upstream_rq_retry_overflow	|	Counter	|	�����۶ϣ�δ���Ե���������	|
|	upstream_flow_control_paused_reading_total	|	Counter	|	�������ƣ���������ͣ��ȡ���ܴ���	|
|	upstream_flow_control_resumed_reading_total	|	Counter	|	�������ƣ������λָ���ȡ���ܴ���	|
|	upstream_flow_control_backed_up_total	|	Counter	|	�������ӱ��ݡ���ͣ���ζ�ȡ���ܴ���	|
|	upstream_flow_control_drained_total	|	Counter	|	��������������ָ����ζ�ȡ���ܴ���	|
|	membership_change	|	Counter	|	�ܼ�Ⱥ��Ա�仯	|
|	membership_healthy	|	Gauge	|	��ǰȺ��������Ա�������������������쳣ֵ��⣩	|
|	membership_total	|	Gauge	|	��ǰ�ļ�Ⱥ��Ա����	|
|	retry_or_shadow_abandoned	|	Counter	|	���ڻ��������ƣ����Ի����ԡ���ȡ�����ܴ���	|
|	config_reload	|	Counter	|	���ڲ�ͬ�����ã������������¼��ص�API���ô���	|
|	update_attempt	|	Counter	|	�ܼ�Ⱥ��Ա���³��Դ���	|
|	update_success	|	Counter	|	�ܼ�Ⱥ��Ա���³ɹ�����	|
|	update_failure	|	Counter	|	�ܼ�Ⱥ��Ա����ʧ�ܴ���	|
|	version	|	Gauge	|	�����ϴ�API���ü��سɹ������ݹ�ϣ	|
|	max_host_weight	|	Gauge	|	Ⱥ�����������������Ȩ��	|
|	bind_errors	|	Counter	|	���׽��ְ󶨵����õ�Դ��ַ��������	|


### �������ͳ��
��������˽�����飬��ô��Ⱥ����һ����`cluster.<name>.health_check.`Ϊ����ͳ������ͳ�����£�

|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	attempt	|	Counter	|	�������Ĵ���	|
|	success	|	Counter	|	�������ɹ��Ĵ���	|
|	failure	|	Counter	|	ִ�н���������ʧ�ܵĴ����������磺HTTP 503���Լ�������ϣ�	|
|	passive_failure	|	Counter	|	�򱻶��¼����µĽ������ʧ�ܵĴ��������磺`x-envoy-immediate-health-check-fail`��	|
|	network_failure	|	Counter	|	������������µĽ������ʧ�ܴ���	|
|	verify_cluster	|	Counter	|	���Լ�Ⱥ������֤�Ľ�����������	|
|	healthy	|	Gauge	|	������Ա������	|


### ��Ⱥ���ͳ��
���ΪȺ����������Ⱥ�쳣��⣬��ͳ����Ϣ����`cluster.<name>.outlier_detection.`Ϊ�����������������ݣ�

|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	ejections_enforced_total	|	Counter	|	�����κ��쳣���͵��µ�ǿ�����������	|
|	ejections_active	|	Gauge	|	��ǰ���������������	|
|	ejections_overflow	|	Counter	|	��ﵽ����������ֹ�����ٷ�ռ��	|
|	ejections_enforced_consecutive_5xx	|	Counter	|	ִ�е�����5xx�������	|
|	ejections_detected_consecutive_5xx	|	Counter	|	��⵽������5xx�����������ʹδ��ǿ��ִ�У�	|
|	ejections_enforced_success_rate	|	Counter	|	ִ�гɹ����쳣ֵ����Ĵ���	|
|	ejections_detected_success_rate	|	Counter	|	��⵽�ĳɹ����쳣ֵ�����������ʹδִ�У�	|
|	ejections_enforced_consecutive_gateway_failure	|	Counter	|	ִ�е��������ع����������	|
|	ejections_detected_consecutive_gateway_failure	|	Counter	|	��⵽���������ع��������������ʹδ��ǿ��ִ�У�	|
|	ejections_total	|	Counter	|	**�ѹ�ʱ**�������κ��쳣ֵ���ͣ���ʹδǿ��ִ�У�	|
|	ejections_consecutive_5xx	|	Counter	|	**�ѹ�ʱ**��������5xx�������������ʹδ��ǿ��ִ�У�	|


### ��̬HTTPͳ��
��������HTTP����̬HTTP��Ӧͳ����ϢҲ���á���Щ�ɸ����ڲ�ϵͳ���Լ�����·�ɡ���������֮��Ĺ��������ɵ�ͳ�ơ���`cluster.<name>.`Ϊ��������������ͳ����Ϣ��

|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	upstream\_rq\_<*xx>	|	Counter	|	HTTP��Ӧ�����ͳ�ƣ����磺2xx��3xx�ȣ�	|
|	upstream\_rq_<*>	|	Counter	|	�����HTTP��Ӧ��ͳ�ƣ����磺201��302�ȣ�	|
|	upstream\_rq_time	|	Histogram	|	����ʱ�䣬��λ����	|
|	canary.upstream\_rq_<*xx>	|	Counter	|	���λҶȷ����ڼ��HTTP��Ӧ��ͳ��	|
|	canary.upstream\_rq_<*>	|	Counter	|	���λҶȷ����ڼ�����HTTP��Ӧ��ͳ��	|
|	canary.upstream_rq_time	|	Histogram	|	���λҶȷ����ڼ�����ʱ�����	|
|	internal.upstream\_rq_<*xx>	|	Counter	|	�����ڲ���HTTP��Ӧ��ͳ��	|
|	internal.upstream\_rq_<*>	|	Counter	|	�����ڲ������HTTP��Ӧ��ͳ��	|
|	internal.upstream_rq_time	|	Histogram	|	�����ڲ�����ʱ�䣬��λ����	|
|	external.upstream\_rq_<*xx>	|	Counter	|	�����ⲿHTTP��Ӧ�����ͳ��	|
|	external.upstream\_rq_<*>	|	Counter	|	�����ⲿ�����HTTP��Ӧ��ͳ��	|
|	external.upstream_rq_time	|	Histogram	|	�����ⲿ����ʱ�䣬��λ����	|


### ��̬HTTP������ͳ��
��������˽�����ͳ����Ϣ�����ǽ���`cluster.<name>.<alt name>. `Ϊ�����ռ䡣���ɵ�ͳ����Ϣ������Ķ�̬HTTPͳ����Ϣ��ͬ��

### ����������̬HTTPͳ��
��������������ڱ��ط���ͨ��`--service-zone`��������Ⱥ������Envoy����`cluster.<name>.zone.<from_zone>.<to_zone>`Ϊ�����ռ䡣ͳ����Ϣ���£�

|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	upstream\_rq_<*xx>	|	Counter	|	HTTP��Ӧ�����ͳ�ƣ����磺2xx��3xx�ȣ�	|
|	upstream\_rq_<*>	|	Counter	|	�����HTTP��Ӧ��ͳ�ƣ����磺201��302�ȣ�	|
|	upstream_rq_time	|	Histogram	|	����ʱ�䣬��λ����	|


### ���ؾ���ͳ��
��ظ��ؾ�����ߵ�ͳ����Ϣ��ͳ����Ϣ��`cluster.<name>.`Ϊ��������������ͳ����Ϣ��

|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	lb_healthy_panic	|	Counter	|	�ֻ�ģʽ�³��ظ��ؾ������������	|
|	lb_zone_cluster_too_small	|	Counter	|	��������Ⱥ����С���������֪·�ɾ��ߴ���	|
|	lb_zone_routing_all_directly	|	Counter	|	��������ֱ�ӷ��͵�ͬһ��������ߴ���	|
|	lb_zone_routing_sampled	|	Counter	|	����һЩ����ͬһ��������ߴ���	|
|	lb_zone_routing_cross_zone	|	Counter	|	�����֪·��ģʽ�������뷢�ͽ�������Ĵ���	|
|	lb_local_cluster_not_ok	|	Counter	|	����������δ���ã������Ǳ���Ⱥ�����ڻ���ģʽ	|
|	lb_zone_number_differs	|	Counter	|	���غ�����Ⱥ���е�������Ŀ��ͬ�Ĵ���	|


### ���ؾ����Ӽ�ͳ��
�����`<arch_overview_load_balancer_subsets>`���������ؾ������Ӽ���ͳ����Ϣ��ͳ����Ϣ��`cluster.<name>.`������������ͳ����Ϣ��


|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	lb_subsets_active	|	Gauge	|	��ǰ�����Ӽ�������	|
|	lb_subsets_created	|	Counter	|	�������Ӽ�����	|
|	lb_subsets_removed	|	Counter	|	����û����������ɾ�����Ӽ�����	|
|	lb_subsets_selected	|	Counter	|	ѡ���κ��Ӽ����и���ƽ��Ĵ���	|
|	lb_subsets_fallback	|	Counter	|	���˲��Ա����õĴ���	|


## ����
- [��һ��](../Clustermanager.md)
- [��ҳĿ¼](../../README.md)