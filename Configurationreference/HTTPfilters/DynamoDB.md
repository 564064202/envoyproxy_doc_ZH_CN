## DynamoDB
- [DynamoDB�ܹ�����](../../Introduction/Architectureoverview/DynamoDB.md)
- [v1 API �ο�](../../v1APIreference/HTTPfilters/DynamoDB.md)
- [v2 API �ο�](../../v2APIreference/Filters/Networkfilters/HTTPconnectionmanager.md)

### ͳ��

DynamoDB���������ͳ����Ϣ�����ռ�Ϊ`http.<stat_prefix>.dynamodb.`������`stat_prefix`������ӵ�е�HTTP���ӹ�������

ÿ��������ͳ����Ϣ�����������ռ�`http.<stat_prefix>.dynamodb.operation.<operation_name>.`�ҵ���

|	����	|	����	|	����	|
|	 -------------	|	 -------------	|	 -------------	|
|	upstream_rq_total	|	Counter	|	Total number of requests with <operation_name>	|
|	upstream_rq_time	|	Histogram	|	Time spent on <operation_name>	|
|	upstream_rq_total_xxx	|	Counter	|	Total number of requests with <operation_name> per response code (503/2xx/etc)	|
|	upstream_rq_time_xxx	|	Histogram	|	Time spent on <operation_name> per response code (400/3xx/etc)	|


ÿ�����ͳ����Ϣ�����������ռ�`http.<stat_prefix>.dynamodb.table.<table_name>.`���ҵ��� DynamoDB�Ĵ󲿷ֲ������漰��������`BatchGetItem`��`BatchWriteItem`���԰��������Envoy�����������������ʹ����ͬ�ı�ʱ�Ÿ���ÿ�����ͳ����Ϣ��

|	����	|	����	|	����	|
|	 -------------	|	 -------------	|	 -------------	|
|	upstream_rq_total	|	Counter	|	Total number of requests on <table_name> table	|
|	upstream_rq_time	|	Histogram	|	Time spent on <table_name> table	|
|	upstream_rq_total_xxx	|	Counter	|	Total number of requests on <table_name> table per response code (503/2xx/etc)	|
|	upstream_rq_time_xxx	|	Histogram	|	Time spent on <table_name> table per response code (400/3xx/etc)	|

*������������ע�⣬������δ�㷺ʹ�õ�Ԥ���а汾��Amazon DynamoDB���ܡ�*
ÿ�������Ͳ���ͳ����Ϣ�����������ռ�`http.<stat_prefix>.dynamodb.table.<table_name>.`�ҵ�����������������Envoy�������в�����ʹ����ͬ�ı�ʱ����ÿ�������Ͳ���ͳ����Ϣ��


|	����	|	����	|	����	|
|	 -------------	|	 -------------	|	 -------------	|
|	`capacity.<operation_name>.__partition_id=<last_seven_characters_from_partition_id>`	|	Counter	|	Total number of capacity for `<operation_name>` on `<table_name>` table for a given `<partition_id>`	|

������ϸͳ����Ϣ��

- ����4xx��Ӧ�Ͳ������������ʧ�ܣ��������ռ�` http.<stat_prefix>.dynamodb.error.<table_name>.`�и���ָ���ı�ʧ�ܵ��ܴ�����

|	����	|	����	|	����	|
|	 -------------	|	 -------------	|	 -------------	|
|	`<error_type>`	|	Counter	|	Total number of specific `<error_type>` for a given `<table_name>`	|
|	BatchFailureUnprocessedKeys	|	Counter	|	Total number of partial batch failures for a given `<table_name>`	|

### ����ʱ����
DynamoDB������֧����������ʱ���ã�

- **dynamodb.filter_enabled**</br>
���ù�����������ٷֱȡ�Ĭ����100����

## ����
- [��һ��](../HTTPfilters.md)
- [��ҳĿ¼](../../README.md)