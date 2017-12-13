## �ο�����
Envoy��Դ���뷢�а��У�����������Ҫ�������͵�����ģ�巶����

- [�����](../Introduction/Deploymenttypes.md)
- [ǰ�˴���](../Introduction/Deploymenttypes.md)
- [˫�ش���](../Introduction/Deploymenttypes.md)

���ĵ�Ŀ��չʾEnvoy�ڸ��Ӳ��𳡾��µ�ȫ�����ܡ������������й��ܡ��й��������ĵ��������[���òο�](../Configurationreference.md)��

### ����������
��������Envoy�Ѿ������Ը��ӡ���Lyft�У�����ʹ��[jinja](http://jinja.pocoo.org/)ģ�����ô����͹������ø����ס�Դ���뷢�а����һ��������������������������������Lyft��ʹ�õİ汾���ơ����ǻ�Ϊ������������ṩ������ʾ������ģ�塣

- �����������ű���[configs/configgen.py](https://github.com/envoyproxy/envoy/blob/master/configs/configgen.py)
- ����ģ�壺[configs/envoy_service_to_service.template.json](https://github.com/envoyproxy/envoy/blob/master/configs/envoy_service_to_service.template.json)
- ǰ�˴���ģ�壺[configs/envoy_front_proxy.template.json](https://github.com/envoyproxy/envoy/blob/master/configs/envoy_front_proxy.template.json)
- ˫�ش���ģ�壺[configs/envoy_double_proxy.template.json](https://github.com/envoyproxy/envoy/blob/master/configs/envoy_double_proxy.template.json)

��Ҫ����ʾ�����ã�����repo��Ŀ¼�����������

```
mkdir -p generated/configs
bazel build //configs:example_configs
tar xvf $PWD/bazel-genfiles/configs/example_configs.tar -C generated/configs
```

��һ�����ʹ��`configgen.py`�ж����һЩ������չ������������ȫ�����á� �����`configgen.py`�е�ע�ͣ��Ի�ȡ�й���ϸ��չ���á�

����ʾ�����õ�һЩע�����

- �ٶ������ַ����ʵ������`discovery.yourcompany.net`�����С�
- �ٶ�����`company.net`��DNS�����˸��ָ����Ķ�����������ģ�����޸���֧�ֲ�ͬ��ʾ����
- ����Ĭ������LightStep��Ҫ���ô˹��ܻ�����[Zipkin](http://zipkin.io)���٣���ɾ���������Ӧ�������á�
- ������ʾ��ʹ��ȫ�����ٷ�����Ҫ���ô˹��ܣ���ɾ��������ص����á�
- ����·�ɷ��ֵķ����Ա��������ø����ã����ٶ�������`rds.yourcompany.net`�����С�
- ���ü�Ⱥ���ֵķ�����Ϊ���òο����ٶ���`cds.yourcompany.net`�����С�


### ����ð�̲���
[configs/google_com_proxy.json](https://github.com/envoyproxy/envoy/blob/master/configs/google_com_proxy.json)���ṩ��һ���ǳ��򵥵�Envoy���ã���������֤������HTTP������������������һ��ʵ�ʵ�Envoy����ֻ���������ð�̲���Envoy���������У�

```
build/source/exe/envoy -c configs/google_com_proxy.json -l debug
curl -v localhost:10000
```

## ����
- [��һ��](../Buildingandinstallation.md)
- [��ҳĿ¼](../README.md)