## gRPC HTTP/1.1 �Ž�
- [gRPC �ܹ�����](../../Introduction/Architectureoverview/gRPC.md)
- [v1 API �ο�](../../v1APIreference/HTTPfilters/gRPCHTTP11bridge.md)
- [v2 API �ο�](../../v2APIreference/Filters/Networkfilters/HTTPconnectionmanager.md)

����һ���򵥵Ĺ����������Խ���֧��gRPC��Ӧ��HTTP/1.1�ͻ����Žӵ����ݵ�gRPC�����������Ĺ���ԭ�����£�

- ��������ʱ����������鿴�����Ƿ�ΪHTTP/1.1��������������Ϊ`application/grpc`��
- ��������������յ���Ӧʱ���������Ỻ�沢�ȴ�Ԥ��Ƭ��Ȼ����`grpc-status`���롣�����Ϊ�㣬���������HTTP��Ӧ�����л�Ϊ503��������`grpc-status`��`grpc-message`���Ƶ���Ӧͷ���У��Ա�ͻ��˿��Ը�����Ҫ�鿴���ǡ�
- �ͻ���Ӧ�÷��ͷ��������α�ױ��HTTP/1.1����
 - `:method:` POST
 - `:path:` `<gRPC-METHOD-NAME>`
 - `content-type:` application/grpc
- BodyӦ�������л���grpc body��
 - 1���ֽڵ��㣨δѹ������
 - ����˳��4���ֽڵ�ԭʼ��Ϣ���ȡ�
 - ���л���ԭʼ��Ϣ��
- ��Ϊ����������뻺����Ӧ���Բ���`grpc-status`��������ֻ������һԪgRPC API��

������Ϣ��http://www.grpc.io/docs/guides/wire.html

�˹��������ռ�����gRPC���������ͳ����Ϣ����ʹ��Щ������ͨ��HTTP/2���������gRPC����

### ͳ��
�������ռ���ͳ����Ϣ�����ռ�Ϊ`cluster.<route target cluster>.grpc.`��

|	����	|	����	|	����	|
|	 -------------	|	 -------------	|	 -------------	|
|	`<grpc service>.<grpc method>.success`	|	Counter	|	Total successful service/method calls	|
|	`<grpc service>.<grpc method>.failure`	|	Counter	|	Total failed service/method calls	|
|	`<grpc service>.<grpc method>.total`	|	Counter	|	Total service/method calls	|


## ����
- [��һ��](../HTTPfilters.md)
- [��ҳĿ¼](../../README.md)