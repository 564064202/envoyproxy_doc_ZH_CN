## ����

Envoyʹ��[Bazel](https://bazel.build/)���߹���ϵͳ��Ϊ�˼򻯳��ι����Լ��������ţ������ṩ��һ������Ubuntu16��Docker�����������а����˹�����̬����Envoy������������ݣ������[ci/README.md](https://github.com/envoyproxy/envoy/blob/master/ci/README.md)��

�����Ҫ�ֶ��������밴��[bazel/README.md](https://github.com/envoyproxy/envoy/blob/master/bazel/README.md)�е�˵�����в�����

### Ҫ��
Envoy�������Ubuntu 14 LTS�Ͽ����Ͳ���ġ���Ҳ�������κε�����Linux�����У�����Ubuntu 16 LTS��

����Envoy��Ҫ��������Ҫ��

- GCC 5+������֧��C++14����
- [Ԥ����](https://github.com/envoyproxy/envoy/tree/master/ci/build_container/build_recipes)�ĵ�����������
- ��������Bazel���ߡ�

�й��ֶ������ĸ�����Ϣ�����������[CI](https://github.com/envoyproxy/envoy/blob/master/ci/README.md)��[Bazel](https://github.com/envoyproxy/envoy/blob/master/bazel/README.md)�ĵ����ӡ�


### Ԥ�����Ķ������ļ�
��ÿ�����ύ�ϣ����Ǵ���һ�����Envoy�������ļ���������Docker���� ��������ʽ������ʱ�����ǻ����÷����汾���Docker����

- [envoyproxy/envoy](https://hub.docker.com/r/envoyproxy/envoy/tags/)������Ubuntu Xenial��Ŵ��з��ŵĶ������ļ��汾��
- [envoyproxy/envoy-alpine](https://hub.docker.com/r/envoyproxy/envoy-alpine/tags/)������glibc alpine�޷��Ŷ������ļ��汾��
- [envoyproxy/envoy-alpine-debug](https://hub.docker.com/r/envoyproxy/envoy-alpine-debug/tags/)������glibc alpine�ɵ��ԵĶ������ļ��汾��

����Ҳ�ῼ��ͨ�����������������Ӵ����Ȥ������CI����װ���ṩ����Ķ��������͡������Ҫ������GitHub�����һ��[issue](https://github.com/envoyproxy/envoy/issues)��

## ����
- [��һ��](../Buildingandinstallation.md)
- [��ҳĿ¼](../README.md)