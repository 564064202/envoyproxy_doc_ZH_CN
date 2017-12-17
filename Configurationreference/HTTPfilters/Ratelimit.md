## ��������

- ��������[�ܹ�����](../../Introduction/Architectureoverview/Globalratelimiting.md)
- [v1 API �ο�](../../v1APIreference/HTTPfilters/Ratelimit.md)
- [v2 API �ο�](../../v2APIreference/Filters/HTTPfilters/Ratelimit.md)

�������·�ɻ�����������һ���������Ϲ��������õ�������������ʱ��HTTP�������ƹ������������������Ʒ���·�ɿ���ѡ������������������������á������ö��Ӧ��������ÿ���������������ᵼ�±����͵��������Ʒ���

����������Ʒ��񱻵��ã������κ���Ӧ�������Ƶ�����������������429��Ӧ��

### ��ɲ���
**ע�⣺������Ϊv1 API��д�ģ�����Щ����Ҳ������v2 API��������δ���汾��ʹ��v2 API��д��**

·�ɻ����������ϵ�ÿ���������Ʋ�������Ҫһ����������Ϊ���롣��Ҫ���������ӵ���������������������һ��������������˳�������ϲ�����������������������ָ��������˳�������䡣

**��1**

���磬Ҫ����������������
```
("generic_key", "some_value")
("source_cluster", "from_cluster")
```

���ý��ǣ�
```
{
  "actions" : [
  {
    "type" : "generic_key",
    "descriptor_value" : "some_value"
  },
  {
    "type" : "source_cluster"
  }
  ]
}
```

**��2**

���ĳ��������������������Ŀ���򲻻�Ϊ������������������

�����������ã�

```
{
  "actions" : [
  {
    "type" : "generic_key",
    "descriptor_value" : "some_value"
  },
  {
    "type" : "remote_address"
  },
  {
    "type" : "souce_cluster"
  }
  ]
}
```

�������û������[x-forwarded-for](../../Configurationreference/HTTPconnectionmanager/HTTPheadermanipulation.md)���򲻻�������������

�������������[x-forwarded-for](../../Configurationreference/HTTPconnectionmanager/HTTPheadermanipulation.md)���������������������

```
("generic_key", "some_value")
("remote_address", "<trusted address from x-forwarded-for>")
("source_cluster", "from_cluster")
```

### ͳ��
�����������������Ⱥ�е�ͳ����Ϣ��`cluster.<route target cluster>.ratelimit.`Ϊ�����ռ䡣429��Ӧ�����͵�������Ⱥ��[��̬HTTPͳ��](../../Configurationreference/Clustermanager/Statistics.md)��

|	����	|	����	|	����	|
|	 -------------	|	 -------------	|	 -------------	|
|	ok	|	Counter	|	��������������������Ʒ�������	|
|	error	|	Counter	|	�����������Ʒ����ʧ������	|
|	over_limit	|	Counter	|	��������������������Ʒ�������	|

### ����ʱ����
HTTP�������ƹ�����֧����������ʱ���ã�

- **ratelimit.http_filter_enabled**</br>
�������������Ʒ��������İٷֱȡ�Ĭ��Ϊ100��

- **ratelimit.http_filter_enforcing**</br>
�������������Ʒ���ִ�о���������ٷֱȡ�Ĭ��Ϊ100�����������������ȫִ�н��֮ǰ�ᷢ��ʲô��

- **ratelimit.`<route_key>`.http_filter_enabled**</br>
��������������������ָ���ĸ���`route_key`���������Ʒ�������İٷֱȡ�Ĭ��Ϊ100��

## ����
- [��һ��](../HTTPfilters.md)
- [��ҳĿ¼](../../README.md)