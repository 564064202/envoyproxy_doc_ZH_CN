## ����ע��

����ע������������ڲ���΢����Բ�ͬ��ʽ���ϵĻָ��������ù�����������ע���ӳٺ���ֹ���󣬲������û�ָ���Ĵ�����룬�Ӷ��ܹ�����ͬ�Ĺ���������������ϣ�������أ��������ӳ٣���������ȡ�����ע��������ڻ�������ģ�Ŀ�ĵأ����μ�Ⱥ���Լ��ض���һ��Ԥ���������ͷ�顣

����ע��ķ�Χ������ͨ���������ͨ�ŵ�Ӧ�ó����Լ��ɹ۲쵽�ķ�Χ���޷�ģ�Ȿ�������ϵ�CPU�ʹ��̹��ϡ�

Ŀǰ������ע����������������ƣ�
- ��ֹ����Ĵ�����������HTTP״̬��
- �ӳٱ�������һ����ʱ����

δ���İ汾������֧�����ƹ��ϵ��ض���·�ɣ�ע��gRPC��HTTP/2�ض��Ĵ������ͻ��ڷֲ��ĳ���ʱ�ӡ�

### ����
**ע�⣺����ע��������������κ�����������������·������������֮ǰ���롣**

- [v1 API�ο�](../../v1APIreference/HTTPfilters/FaultInjection.md)
- [v2 API�ο�](../../v2APIreference/Filters/HTTPfilters/FaultInjection.md)

### ����ʱ����
HTTP����ע�������֧������ȫ������ʱ���ã�

- **fault.http.abort.abort_percent**</br>
���ͷ��ƥ�䣬������ֹ����İٷֱȡ���������Ĭ��ʹ��`abort_percent`ֵ��������ò�����`abort`���`abort_percent`Ĭ��Ϊ0��

- **fault.http.abort.http_status**</br>
�������������HTTP״̬�룬���ͷ��ƥ�䣬�����󽫱���ֹ��Ĭ��Ϊ������ָ����`http_status `��������ò�����`abort`���`http_status`Ĭ��Ϊ0��

- **fault.http.delay.fixed_delay_percent**</br>
���ͷ��ƥ�䣬���󽫱��ӳٵİٷֱȡ�Ĭ��Ϊ������ָ����`delay_percent`������Ϊ0��

- **fault.http.delay.fixed_duration_ms**</br>
�ӳ�ʱ���Ժ���Ϊ��λ�����δָ������ʹ��������ָ����`fixed_duration_ms`�����������ʱ��������ȱ������ֶΣ��򲻻�ע���ӳ١�

**��ע�⣬���ض�����Ⱥ���У����������������ʱ����ֵ������Ϲ�����Ĭ��ֵ�ᱻ���ǡ�����������ָ��������ʱ����ֵ��**

- `fault.http.<downstream-cluster>.abort.abort_percent`
- `fault.http.<downstream-cluster>.abort.http_status`
- `fault.http.<downstream-cluster>.delay.fixed_delay_percent`
- `fault.http.<downstream-cluster>.delay.fixed_duration_ms`

���μ�Ⱥ����ȡ��HTTP `x-envoy-downstream-service-cluster`ͷ�������������ϵͳ���Ҳ�������Ĭ��ʹ��ȫ������ʱ����Ϊȱʡ���á�

### ͳ��
���Ϲ��������ͳ����Ϣ�����ռ�Ϊ`http.<stat_prefix>.fault.`��`stat_prefix`������ӵ�е�HTTP���ӹ�������

|	����	|	����	|	����	|
|-----	|-------|-------|
|	`delays_injected`	|	Counter	|	�ӳ���������	|
|	`aborts_injected`	|	Counter	|	����ֹ����������	|
|	`<downstream-cluster>.delays_injected`	|	Counter	|	ָ������Ⱥ�����ӳ���������	|
|	`<downstream-cluster>.aborts_injected`	|	Counter	|	ָ������Ⱥ������ֹ��������	|



## ����
- [��һ��](../HTTPfilters.md)
- [��ҳĿ¼](../../README.md)