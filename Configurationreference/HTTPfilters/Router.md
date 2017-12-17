## ·��

·�ɹ�����ʵ����HTTPת������������Envoy�����HTTP����������ʹ�á�����������Ҫ��������ѭ·�ɱ������õ�ָ�����ת�����ض���֮�⣬���������������ԣ�ͳ�Ƶȡ�

- [v1 API �ο�](../../v1APIreference/HTTPfilters/Router.md)
- [v2 API �ο�](../../v2APIreference/Filters/HTTPfilters/Router.md)

### HTTPͷ��
·�����ڳ���/�����Լ����/��Ӧ·�������Ѻ����ø���HTTPͷ���������ڱ��½�����˵����

- [x-envoy-expected-rq-timeout-ms](#x-envoy-expected-rq-timeout-ms)
- [x-envoy-max-retries](#x-envoy-max-retries)
- [x-envoy-retry-on](#x-envoy-retry-on)
- [x-envoy-retry-grpc-on](#x-envoy-retry-grpc-on)
- [x-envoy-upstream-alt-stat-name](#x-envoy-upstream-alt-stat-name)
- [x-envoy-upstream-canary](#x-envoy-upstream-canary)
- [x-envoy-upstream-rq-timeout-alt-response](#x-envoy-upstream-rq-timeout-alt-response)
- [x-envoy-upstream-rq-timeout-ms](#)
- [x-envoy-upstream-rq-per-try-timeout-ms](#x-envoy-upstream-rq-timeout-ms)
- [x-envoy-upstream-service-time](#x-envoy-upstream-service-time)
- [x-envoy-original-path](#x-envoy-original-path)
- [x-envoy-immediate-health-check-fail](#x-envoy-immediate-health-check-fail)
- [x-envoy-overloaded](#x-envoy-overloaded)
- [x-envoy-decorator-operation](#x-envoy-decorator-operation)

#### x-envoy-expected-rq-timeout-ms

����·��������������ɵ�ʱ�䣨�Ժ���Ϊ��λ����Envoy�������HTTPͷ�����Ա����������ڽ����������Ը�������ʱ����������������ǰ�˳����������ڲ����������õģ����Դ�[x-envoy-upstream-rq-timeout-ms](#x-envoy-upstream-rq-timeout-ms)ͷ����[·�ɳ�ʱ](../../v1APIreference/HTTPRouteconfiguration/Route.md)�а�˳���ȡ��

#### x-envoy-max-retries
�����[���Բ���](../../v1APIreference/HTTPRouteconfiguration/Route.md)��Envoy��Ĭ������һ�Σ�������ȷָ����������[·����������](../../v1APIreference/HTTPRouteconfiguration/Route.md)��ͨ��ʹ�ô�ͷ����ʽ�������Դ��������δ�������Բ��ԣ�����δָ��[x-envoy-retry-on](#x-envoy-retry-on)��[x-envoy-retry-grpc-on](#x-envoy-retry-grpc-on)ͷ����Envoy����������ʧ�ܵ�����

����Envoy������Ե�һЩ˵����

- ·�ɳ�ʱ��ͨ��[x-envoy-upstream-rq-timeout-ms](#x-envoy-upstream-rq-timeout-ms)��[·����������](../../v1APIreference/HTTPRouteconfiguration/Route.md)�������������ԡ� ��ˣ��������ʱ����Ϊ3�룬���ҵ�һ����������Ҫ2.7�룬�����ԣ������˱ܣ�ֻ��0.3sʱ����ɡ��������������������/��ʱ����ָ��������
- Envoyʹ����ȫ������ָ���˱��㷨�������ԣ����׼ʱ��Ϊ25ms����һ�����Խ���0-24ms֮������ӳ٣��ڶ�����0-74ms֮�䣬��������0-174ms֮�䣬�������ơ�
- ���������Դ�����ͷ����·�����ö������ã����ڻ�������ֵ���������������Դ�����

#### x-envoy-retry-on

�ڳ������������ô˱�ͷ������Envoy��������ʧ�ܵ��������Դ���Ĭ��Ϊ1������ͨ��[x-envoy-max-retries](#x-envoy-max-retries)ͷ����·���������Բ��Խ��п��ƣ�������[x-envoy-retry-on](#x-envoy-retry-on)ͷ��ֵ��ʾ���Բ��ԡ�����ʹ��','�ָ��б���ָ��һ���������ԡ�֧�ֵĲ����У�

- **5xx**</br>
   ������η�������Ӧ�κ�5xx����Ӧ���룬���߸���û����Ӧ���Ͽ�/����/��ȡ��ʱ����Envoy�������������󡣣���������ʧ�ܺ;ܾ�����

   ע�������󳬹�[x-envoy-upstream-rq-timeout-ms](#x-envoy-upstream-rq-timeout-ms)������504�����룩ʱ��Envoy���������ԡ���������ڸ��������ϳ��Գ���ʱ������ԣ���ʹ��[x-envoy-upstream-rq-per-try-timeout-ms](#x-envoy-upstream-rq-per-try-timeout-ms)��`x-envoy-upstream-rq-timeout-ms`��������ⲿʱ�����ƣ������������κ����ԡ�

- **connect-failure**</br>
   ����������η���������ʧ�ܶ���������ʧ�ܣ����ӳ�ʱ�ȣ���Envoy���������ԡ���������5xx�У�

   ע������ʧ��/��ʱ��TCP���𣬶��������󼶱��ⲻ����ͨ��[x-envoy-upstream-rq-timeout-ms](#x-envoy-upstream-rq-timeout-ms)��ͨ��[·������](../../v1APIreference/HTTPRouteconfiguration/Route.md)ָ������������ʱ��

- **retriable-4xx**</br>
   ������η�������Ӧ�ɻظ���4xx��Ӧ���룬Envoy���������ԡ�Ŀǰ����������Ψһ����Ӧ������409��

   ע��С�Ĵ򿪴��������͡���ĳЩ����£�409���ܱ�����Ҫ�����ֹ����汾����ˣ������߲�Ӧ�����Բ�����Ҫ��ȡ��Ȼ���ٳ���д�롣������������͵�����·������ԣ�����������һ��409ʧ�ܡ�

- **refused-stream**</br>
   ������η�����ʹ��`REFUSED_STREAM`���������������Envoy���������ԡ����������ͱ�ʾ������԰�ȫ�����ԡ���������5xx�У�
���Դ�������ͨ��[x-envoy-max-retries](#x-envoy-max-retries)ͷ��ͨ��[·������](../../v1APIreference/HTTPRouteconfiguration/Route.md)�����ơ�

��ע�⣬���Բ���Ҳ����Ӧ����[·�ɼ���](../../v1APIreference/HTTPRouteconfiguration/Route.md)��

Ĭ������£�Envoy����ִ�����ԣ��������Ѿ���������ķ�ʽ�������ǡ�

#### x-envoy-retry-grpc-on
�ڳ������������ô˱�ͷ�ᵼ��Envoy��������ʧ�ܵ��������Դ���Ĭ��Ϊ1������ͨ��[x-envoy-max-retries](#x-envoy-max-retries)ͷ��·������[���Բ���](../../v1APIreference/HTTPRouteconfiguration/Route.md)���п��ƣ���gRPC���Ե�ǰ��֧����Ӧͷ�е�gRPC״̬�롣׷�����е�gRPC״̬�벻�ᴥ�������߼�������ʹ��','�ָ��б���ָ��һ���������ԡ�֧�ֵĲ����ǣ�

- **cancelled**</br>
 �����Ӧͷ�е�gRPC״̬�뱻��cancelled����1����Envoy����������;

- **deadline-exceeded**</br>
 �����Ӧͷ�е�gRPC״̬���ǡ�deadline-exceeded����4����Envoy����������;

- **resource-exhausted**</br>
 �����Ӧͷ�е�gRPC״̬���ǡ�resource-exhausted����8����Envoy����������;
 

ͬ��`x-envoy-retry-grpc-on`ͷ�����Դ���������ͨ��[x-envoy-max-retries](#x-envoy-max-retries)ͷ������

��ע�⣬���Բ���Ҳ����Ӧ����[·�ɼ���](../../v1APIreference/HTTPRouteconfiguration/Route.md)��

Ĭ������£�Envoy����ִ�����ԣ��������Ѿ���������ķ�ʽ�������ǡ�

#### x-envoy-upstream-alt-stat-name

�ڳ����������������ͷ���ᵼ��Envoy��������Ӧ����/ʱ��ͳ����Ϣ���͵�˫��ͳ�����������Envoy��֪����Ӧ�ó��򼶱������£����ܺ����á����[ͳ������ĵ�](../Clustermanager/Statistics.md)��

#### x-envoy-upstream-canary

��������������������ͷ����·������ʹ���������ɽ�˿ȸ���Ҷ���������ص�ͳ����Ϣ�����[ͳ������ĵ�](../Clustermanager/Statistics.md)��

#### x-envoy-upstream-rq-timeout-alt-response

�ڳ������������ô�ͷ���ᵼ��Envoy������ʱ�����������һ��204��Ӧ���루������504����ͷ��ʵ�ʵ�ֵ������; ֻ�������Ĵ��ڡ�����μ�[x-envoy-upstream-rq-timeout-ms](#x-envoy-upstream-rq-timeout-ms)��

#### x-envoy-upstream-rq-timeout-ms

�ڳ������������ô˱�ͷ������Envoy��·�����á���ʱʱ������Ժ���Ϊ��λָ�����������[x-envoy-upstream-rq-per-try-timeout-ms](#x-envoy-upstream-rq-per-try-timeout-ms)��

#### x-envoy-upstream-rq-per-try-timeout-ms

�ڳ������������ô�ͷ��������Envoy��·������������ÿ�γ��Գ�ʱ���˳�ʱ����<=ȫ��·�ɳ�ʱ�������[x-envoy-upstream-rq-timeout-ms](#x-envoy-upstream-rq-timeout-ms)�������򽫱����ԡ������������ÿ�ζ��������ó�ʱ���ԣ�ͬʱ���ֺ�����ܳ�ʱ��

#### x-envoy-upstream-service-time

�������������������������ѵ�ʱ�䣨�Ժ���Ϊ��λ��������ͻ���Ҫȷ�������ӳ�����������ʱ�����Աȣ��������õġ����ͷ������Ӧ�����õġ�

#### x-envoy-original-path

���·��ʹ��`prefix_rewrite`��Envoy�Ὣԭʼ·��ͷ���������ͷ���������־��¼�͵��Ժ����á�

#### x-envoy-immediate-health-check-fail

��������������ش�ͷ��������Ϊ�κ�ֵ������Envoy�������ж����������������������ʧ�ܣ�����ѽ�Ⱥ������Ϊ[�����������](../../Configurationreference/Clustermanager/Healthchecking.md)��������ͨ����׼����ƽ������ϱ������������������ϣ�������ȴ���һ�����н�����鳬ʱ����������Ҳ����ͨ����׼��������������ٴα�ý����������[����������](../../Introduction/Architectureoverview/Healthchecking.md)�˽������Ϣ��

#### x-envoy-overloaded

������ͷ���������������ˣ�Envoy�������ԡ�Ŀǰ������ͷ����ֵ��ֻ�����Ƿ���ڡ����⣬�������[ά��ģʽ](#����ʱ����)������[�۶�](../../Introduction/Architectureoverview/Circuitbreaking.md)����������ʧ��Envoy����������Ӧ�����ô�ͷ����

#### x-envoy-decorator-operation

�����ͷ����������������ϣ����ͷ����ֵ�������ɸ��ٻ������ɵķ�����span�ϵ��κα��ض���Ĳ������ƣ�span name����ͬ��������ڳ�����Ӧ�г��ִ�ͷ������ֵ�����ǿͻ��˷�Χ�ϵ��κα��ض���Ĳ������ƣ�span name����

### ͳ��

·�����ڼ�Ⱥ�����ռ���������ͳ����Ϣ��ȡ������ѡ·����ָ���ļ�Ⱥ�������[�˴�](../../Configurationreference/Clustermanager/Statistics.md)��ȡ������Ϣ��

·���������������ͳ����Ϣ�����ռ�Ϊ`http.<stat_prefix>.`������`stat_prefix`����ӵ�е�[HTTP���ӹ�����](../../v1APIreference/Networkfilters/HTTPconnectionmanager.md)��

|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	no_route	|	Counter	|	��û��·�ɶ�����404�������������	|
|	no_cluster	|	Counter	|	��Ŀ�꼯Ⱥ�����ڶ�����404�������������	|
|	rq_redirect	|	Counter	|	�����ض�����Ӧ����������	|
|	rq_total	|	Counter	|	��·��������	|


��������⼯Ⱥͳ����Ϣ���ƿռ�Ϊ`vhost.<virtual host name>.vcluster.<virtual cluster name>.`������������ͳ����Ϣ��

|	Name	|	Type	|	Description	|
|	 -------------	|	 -------------	|	 -------------	|
|	`upstream_rq_<*xx>`	|	Counter	|	HTTP��Ӧ������ܣ����磬2xx��3xx�ȣ�	|
|	`upstream_rq_<*>`	|	Counter	|	�ض���HTTP��Ӧ�루���磺201��302�ȣ�	|
|	`upstream_rq_time`	|	Histogram	|	����ʱ�䣬��λ����	|

### ����ʱ����

·����������֧����������ʱ���ã�

- **upstream.base_retry_backoff_ms**</br>
ָ�������˱�ʱ�����ȡ�Ĭ��Ϊ25ms�����[�˴�](../../Introduction/Architectureoverview/HTTProuting.md)��ȡ������Ϣ��

- **upstream.maintenance_mode.\<cluster name>**</br>
��������������503��Ӧ����İٷֱȡ���Ḳ�����`<cluster name>`��Ⱥ���κ�·��������Ϊ�����������ж�أ�����ע��ȡ�Ĭ��Ϊ���á�

- **upstream.use_retry**</br>
���ʸ�ʹ�����Ե�����ٷֱȡ����κ�������������֮ǰ�������ã������Ҫ�������ڽ�������Envoy�����ԡ�

## ����
- [��һ��](../HTTPfilters.md)
- [��ҳĿ¼](../../README.md)