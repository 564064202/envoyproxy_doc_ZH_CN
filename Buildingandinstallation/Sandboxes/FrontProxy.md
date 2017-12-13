## ǰ�˴���

Ϊ�ô�Ҿ����˽�Envoy�����Ϊǰ�˴������Ƿ�����һ��[docker compose](https://docs.docker.com/compose/)ɳ�䣬���ɳ�䲿����һ��ǰ��Envoy����ͼ�����˷��񣨼򵥵�flaskӦ�ã�������һ���������еĺ�����Envoy������������������������Ϊ`envoymesh`�����������С�

��Docker compose�Ĳ���ͼ������ʾ��

![����ͼ](docker_compose_v0.1.svg)

���д��������ͨ��ǰ��Envoy����·�ɣ���Envoy�䵱λ��`envoymesh`�����Ե�ķ�������˿�`80`ͨ��docker composeӳ�䵽�˿�`8000`�������[/examples/front-proxy/docker-compose.yml](https://github.com/envoyproxy/envoy/blob/master//examples/front-proxy/docker-compose.yml)�������⣬��ע�⣬��ǰ��Envoy·�ɵ������ڵķ���ʵ����������������·�ɵ������Envoy������[/examples/front-proxy/front-envoy.json](https://github.com/envoyproxy/envoy/blob/master//examples/front-proxy/front-envoy.json)�����õ�·�ɣ����������������Envoyͨ�����ص�ַ��[/examples/front-proxy/service-envoy.json](https://github.com/envoyproxy/envoy/blob/master//examples/front-proxy/service-envoy.json)�е�·�����ã�������·�ɵ�flaskӦ�ó��򡣴˲�����Envoy���������������ƣ�����������Envoy��������Ч��·�ɵ����ķ���


### ����ɳ��
�����ĵ���������ͼ��������envoy��Ⱥ�����������á�

**��1������װDocker���߼�**

����ȷ���Ѿ���װ�����°汾��`docker`��`docker-compose`��`docker-machine`��

[Docker������](https://www.docker.com/products/docker-toolbox)�ṩ�˼򵥵ķ�������ȡ��Щ���ߡ�

**��2��������Docker Machine**

���������Ǵ���һ���µĻ���������������

```
$ docker-machine create --driver virtualbox default
$ eval $(docker-machine env default)
```

**��3������������Envoy��¡�ֿ⣬���������е�����**

����㻹û�п�¡Envoy�ֿ⣬����git��¡`git clone git@github.com:envoyproxy/envoy`����`git clone https://github.com/envoyproxy/envoy.git`��

```
$ pwd
envoy/examples/front-proxy
$ docker-compose up --build -d
$ docker-compose ps
        Name                       Command               State      Ports
-------------------------------------------------------------------------------------------------------------
example_service1_1      /bin/sh -c /usr/local/bin/ ...    Up       80/tcp
example_service2_1      /bin/sh -c /usr/local/bin/ ...    Up       80/tcp
example_front-envoy_1   /bin/sh -c /usr/local/bin/ ...    Up       0.0.0.0:8000->80/tcp, 0.0.0.0:8001->8001/tcp
```

**��4��������Envoy��·�ɹ���**

�����ڿ���ͨ��ǰ��Envoy����������������

����service1��

```
$ curl -v $(docker-machine ip default):8000/service/1
*   Trying 192.168.99.100...
* Connected to 192.168.99.100 (192.168.99.100) port 8000 (#0)
> GET /service/1 HTTP/1.1
> Host: 192.168.99.100:8000
> User-Agent: curl/7.43.0
> Accept: */*
>
< HTTP/1.1 200 OK
< content-type: text/html; charset=utf-8
< content-length: 89
< x-envoy-upstream-service-time: 1
< server: envoy
< date: Fri, 26 Aug 2016 19:39:19 GMT
< x-envoy-protocol-version: HTTP/1.1
<
Hello from behind Envoy (service 1)! hostname: f26027f1ce28 resolvedhostname: 172.19.0.6
* Connection #0 to host 192.168.99.100 left intact
```

����service2��

```
$ curl -v $(docker-machine ip default):8000/service/2
*   Trying 192.168.99.100...
* Connected to 192.168.99.100 (192.168.99.100) port 8000 (#0)
> GET /service/2 HTTP/1.1
> Host: 192.168.99.100:8000
> User-Agent: curl/7.43.0
> Accept: */*
>
< HTTP/1.1 200 OK
< content-type: text/html; charset=utf-8
< content-length: 89
< x-envoy-upstream-service-time: 2
< server: envoy
< date: Fri, 26 Aug 2016 19:39:23 GMT
< x-envoy-protocol-version: HTTP/1.1
<
Hello from behind Envoy (service 2)! hostname: 92f4a3737bbc resolvedhostname: 172.19.0.2
* Connection #0 to host 192.168.99.100 left intact
```

��ע�⣬ÿ�������ڷ��͸�ǰ��Envoyʱ������ȷ·�ɵ���Ӧ��Ӧ�ó���

**��5��������Envoy�ĸ��ؾ�������**

������չ���ǵ�service1�ڵ�����ʾEnvoy�ļ�Ⱥ������

```
$ docker-compose scale service1=3
Creating and starting example_service1_2 ... done
Creating and starting example_service1_3 ... done
```

���ڣ�������Ƕ����service1��������ǰ��Envoy�Ὣ����ͨ�����ؾ��ⷢ������service1����

```
$ curl -v $(docker-machine ip default):8000/service/1
*   Trying 192.168.99.100...
* Connected to 192.168.99.100 (192.168.99.100) port 8000 (#0)
> GET /service/1 HTTP/1.1
> Host: 192.168.99.100:8000
> User-Agent: curl/7.43.0
> Accept: */*
>
< HTTP/1.1 200 OK
< content-type: text/html; charset=utf-8
< content-length: 89
< x-envoy-upstream-service-time: 1
< server: envoy
< date: Fri, 26 Aug 2016 19:40:21 GMT
< x-envoy-protocol-version: HTTP/1.1
<
Hello from behind Envoy (service 1)! hostname: 85ac151715c6 resolvedhostname: 172.19.0.3
* Connection #0 to host 192.168.99.100 left intact
$ curl -v $(docker-machine ip default):8000/service/1
*   Trying 192.168.99.100...
* Connected to 192.168.99.100 (192.168.99.100) port 8000 (#0)
> GET /service/1 HTTP/1.1
> Host: 192.168.99.100:8000
> User-Agent: curl/7.43.0
> Accept: */*
>
< HTTP/1.1 200 OK
< content-type: text/html; charset=utf-8
< content-length: 89
< x-envoy-upstream-service-time: 1
< server: envoy
< date: Fri, 26 Aug 2016 19:40:22 GMT
< x-envoy-protocol-version: HTTP/1.1
<
Hello from behind Envoy (service 1)! hostname: 20da22cfc955 resolvedhostname: 172.19.0.5
* Connection #0 to host 192.168.99.100 left intact
$ curl -v $(docker-machine ip default):8000/service/1
*   Trying 192.168.99.100...
* Connected to 192.168.99.100 (192.168.99.100) port 8000 (#0)
> GET /service/1 HTTP/1.1
> Host: 192.168.99.100:8000
> User-Agent: curl/7.43.0
> Accept: */*
>
< HTTP/1.1 200 OK
< content-type: text/html; charset=utf-8
< content-length: 89
< x-envoy-upstream-service-time: 1
< server: envoy
< date: Fri, 26 Aug 2016 19:40:24 GMT
< x-envoy-protocol-version: HTTP/1.1
<
Hello from behind Envoy (service 1)! hostname: f26027f1ce28 resolvedhostname: 172.19.0.6
* Connection #0 to host 192.168.99.100 left intact
```

**��6����������������curl����**

����ʹ�������ϵ�curl�⣬���������Լ�����������������curl��Ҫ����һ���������������ʹ��`docker-compose exec <container_name> /bin/bash`�����磬���ǿ��Խ���`front-envoy`����������ִ�б��ص�curl����

```
$ docker-compose exec front-envoy /bin/bash
root@81288499f9d7:/# curl localhost:80/service/1
Hello from behind Envoy (service 1)! hostname: 85ac151715c6 resolvedhostname: 172.19.0.3
root@81288499f9d7:/# curl localhost:80/service/1
Hello from behind Envoy (service 1)! hostname: 20da22cfc955 resolvedhostname: 172.19.0.5
root@81288499f9d7:/# curl localhost:80/service/1
Hello from behind Envoy (service 1)! hostname: f26027f1ce28 resolvedhostname: 172.19.0.6
root@81288499f9d7:/# curl localhost:80/service/2
Hello from behind Envoy (service 2)! hostname: 92f4a3737bbc resolvedhostname: 172.19.0.2
```

**��7��������������ʹ��curl����**

��Envoy����ʱ����Ҳ��`admin`���ӵ�����Ķ˿ڡ���ʾ������`admin`���󶨵�`8001`�˿�.���ǿ���`curl`��������õ���Ϣ�����磬������`curl` `/server_info`����ȡ�й����������е�Envoy�汾��Ϣ�����⣬����ԡ�curl�� ��/stats���õ�ͳ�����ݡ�������`frontenvoy`�������ǿ��Եõ���

```
$ docker-compose exec front-envoy /bin/bash
root@e654c2c83277:/# curl localhost:8001/server_info
envoy 10e00b/RELEASE live 142 142 0
root@e654c2c83277:/# curl localhost:8001/stats
cluster.service1.external.upstream_rq_200: 7
...
cluster.service1.membership_change: 2
cluster.service1.membership_total: 3
...
cluster.service1.upstream_cx_http2_total: 3
...
cluster.service1.upstream_rq_total: 7
...
cluster.service2.external.upstream_rq_200: 2
...
cluster.service2.membership_change: 1
cluster.service2.membership_total: 1
...
cluster.service2.upstream_cx_http2_total: 1
...
cluster.service2.upstream_rq_total: 2
...
```

��ע�⣬���ǻ����Ի������Ⱥ���ĳ�Ա��������ɵ������������й�http��վ����Ϣ�Լ������������õ�ͳ����Ϣ��

## ����
- [��һ��](../Sandboxes.md)
- [��ҳĿ¼](../../README.md)