## Lua

**ע�⣺Lua�ű�HTTP��������ʵ���Եġ���������ʹ����Ҫ���Ե����ա������ڱ��������Ա�Ա�¶��API���г��������������н�һ���Ŀ��������Ժ���֤����������ΪLua�������Ѿ��ܵ��㹻��API�ȶ��Բ��ԣ�ͨ������Ϊ����׼������ʱ���þ��潫���Ƴ���**


### ����
HTTP Lua�������������������Ӧ����������Lua�ű���������ʱʹ��[LuaJIT](http://luajit.org/)������Ϊ��ˣ�֧�ֵ�Lua�汾�󲿷���5.1������һЩ5.2�����ԡ��йظ�����ϸ��Ϣ�������[LuaJIT�ĵ�](http://luajit.org/extensions.html)��

�ù�������֧����������ֱ�Ӽ���Lua���롣�����Ҫ�����ļ�ϵͳ���룬�����ʹ�ü򵥵������ű��ӱ��ػ������ش�������ಿ�֡�

��������֧��Lua�ǻ������¸߼���ƣ�

- ����Lua��������ÿ���������̡߳�����ζ��û��������ȫ�����ݡ��κ��ڼ���ʱ����������ȫ�ֱ����ڹ����߳�֮���໥���롣������ȫ��֧�ֿ��ܻ���δ��ͨ��API��ӡ�
- ���нű�����Э�����С�����ζ�ż�ʹ���ǿ���ִ�и��ӵ��첽��������Ҳ����ͬ����ʽ��д�ġ���ʹ�ýű������ױ�д����������/�첽������Envoyͨ��һ��APIִ�С�Envoy�������л�(yield)�ű��������첽�������ʱ�ָ��ű���
- ��Ҫ�ڽű���ִ��������������ΪEnvoy API����������IO���Լ�������ص���Ҫ������


### Ŀǰ֧�ָ߼�����
**ע��Ԥ������Lua�������������е�Ӧ�ã������б�����ʱ������ƶ�����Χ����ЩAPIһֱ���ֺ�С�����⡣Ϊ��ʹ�ű���д�ǳ��򵥺Ͱ�ȫ�������ڷǳ����ӻ�������ܵĳ�������ʹ�ñ���C++������API��**

- �ڴ����������Ӧ��������ͬʱ���ṩͷ�������ĺ�β���ļ�飻
- ��ͷ����β�������޸ģ�
- ��ֹ���߻�������������/��Ӧ���ģ����м�飻
- ����������ִ���첽HTTP���á����������ڻ����������ݵ�ͬʱִ�д����Ա㵱�������ʱ�������޸�����ͷ����
- ֱ��ִ����Ӧ�������������ĵ��������������磬һ���ű����Դ���һ������HTTP��֤���ã�Ȼ��ֱ����403��Ӧ���������Ӧ��

### ����

- [v1 API �ο�](../../v1APIreference/HTTPfilters/Lua.md)
- [v2 API �ο�](../../v2APIreference/Filters/HTTPfilters/Lua.md)

### �ű�ʾ��
�����ṩ��һЩLua�ű���һЩ��������ӣ���Ϊһ�����򵥽��ܺͿ������š��й�֧�ֵ�API�ĸ�����ϸ��Ϣ�������[������API](#������API)��

```
-- Called on the request path.
function envoy_on_request(request_handle)
  -- Wait for the entire request body and add a request header with the body size.
  request_handle:headers():add("request_body_size", request_handle:body():length())
end

-- Called on the response path.
function envoy_on_response(response_handle)
  -- Wait for the entire response body and a response header with the the body size.
  response_handle:headers():add("response_body_size", response_handle:body():length())
  -- Remove a response header named 'foo'
  response_handle:headers():remove("foo")
end
```

```
function envoy_on_request(request_handle)
  -- Make an HTTP call to an upstream host with the following headers, body, and timeout.
  local headers, body = request_handle:httpCall(
  "lua_cluster",
  {
    [":method"] = "POST",
    [":path"] = "/",
    [":authority"] = "lua_cluster"
  },
  "hello world",
  5000)

  -- Add information from the HTTP call into the headers that are about to be sent to the next
  -- filter in the filter chain.
  request_handle:headers():add("upstream_foo", headers["foo"])
  request_handle:headers():add("upstream_body_size", #body)
end
```

```
function envoy_on_request(request_handle)
  -- Make an HTTP call.
  local headers, body = request_handle:httpCall(
  "lua_cluster",
  {
    [":method"] = "POST",
    [":path"] = "/",
    [":authority"] = "lua_cluster"
  },
  "hello world",
  5000)

  -- Response directly and set a header from the HTTP call. No further filter iteration
  -- occurs.
  request_handle:respond(
    {[":status"] = "403",
     ["upstream_foo"] = headers["foo"]},
    "nope")
end
```

### ������API

��Envoy�������м��ؽű�ʱ��������ҽű��ж��������ȫ�ֺ�����

```
function envoy_on_request(request_handle)
end

function envoy_on_response(response_handle)
end
```
һ���ű����Զ��������������е�һ����������������·���У�Envoy������`envoy_on_request`������Ϊһ��Э�̣�����һ��API���������Ӧ·���У�Envoy������`envoy_on_response`��ΪЭ�̣�����һ��API�����

**ע�⣺��Envoy�����н���������ͨ����������ʵ�ֵġ��������Ӧ�ñ����浽�κ�ȫ�ֱ�������Ӧ����Э��֮��ʹ�á�������ʹ�ò�����Envoy����ʧ�ܡ�**

֧����������������

- **headers()**</br>
```
headers = handle:headers()
```
��������ͷ������ֻҪͷ����û�б����͵���һ����������ͷ�����У���ͷ���Ϳ��Ա��޸ġ����磬������`httpCall()`֮�����`body()`���÷���֮���޸����ǡ�������κ�����������޸���ͷ�����ű�����ʧ�ܡ�

 ����һ��[ͷ������](#ͷ������API)��

- **body()**</br>
```
body = handle:body()
```
�����������壨body����������ý�ʹ��Envoy�л���yield���ű���ֱ���������屻���塣��ע�⣬���л���������������������ߡ�Envoy���Ỻ�峬�����ӹ���������������ݷ�Χ��

 ����һ��[�������](#����API)��

- **bodyChunks()**</br>
```
iterator = handle:bodyChunks()
```
����һ���������������������������н��յ����������ݿ顣Envoy���ڴ���������ʱ���л�(yield)�ű��������Ỻ�����ǡ���������������������
```
for chunk in request_handle:bodyChunks() do
  request_handle:log(0, chunk:length())
end
```
ÿ�ε��������ض���һ��[�������](#����API)��

- **trailers()**</br>
```
trailers = handle:trailers()
```
��������β�������û��β�������ܻ᷵���㡣β���ڷ��͵���һ��������֮ǰ���ܻᱻ�޸ġ�

 ����һ��[ͷ�����](#ͷ������API)��

- **log*()**</br>
```
handle:logTrace(message)
handle:logDebug(message)
handle:logInfo(message)
handle:logWarn(message)
handle:logErr(message)
handle:logCritical(message)
```
ʹ��Envoy��Ӧ�ó�����־��¼��Ϣ������`message`����Ҫ��¼���ַ�����

- **httpCall()**</br>
```
headers, body = handle:httpCall(cluster, headers, body, timeout)
```
��������������HTTP���á�Envoy���л��ű���ֱ��������ɻ��д���`cluster`�Ƕ�Ӧ��Ⱥ�����������õ�Ⱥ���ַ�����`headers`��Ҫ���͵�`key/value`��ֵ�Ե��б���ע�⣬��������`:method`��`:path`��`:authority`ͷ����`body`�ǿ�ѡ�ַ�������Ҫ���͵��������塣`timeout`��һ��������ָ���Ժ���Ϊ��λ�ĵ��ó�ʱ��

 ��������Ӧ��`headers`���Լ���`body`�ַ��������û�����������`null`��

- **respond()**</br>
```
handle:respond(headers, body)
```
����������Ӧ����Ҫ���н�һ���Ĺ������������˵��ý�������������Ч�����⣬ֻ��������ͷ��û�д��ݸ�����������������£���Ӧ���ǿ��ܵġ���˼�ǣ������Lua�����Ǵ���ģ�
```
function envoy_on_request(request_handle)
  for chunk in request_handle:bodyChunks() do
    request_handle:respond(
      {[":status"] = "100"},
      "nope")
  end
end
```
`headers`��Ҫ���͵ļ�ֵ�Ե��б���ע�⣬��������`:status`ͷ����`body`��һ���ַ�������Ϊ��ѡ����Ӧ���壬������`nil`��

### ͷ������API

- **add()**</br>
```
headers:add(key, value)
```
Ϊͷ���������һ��ͷ����`key`���ṩͷ�������ַ�����`value`��һ���ṩͷ��ֵ���ַ�����

- **get()**</br>
```
headers:get(key)
```
��ȡͷ������ͷ��ֵ������`key`Ϊ����Ӧ��ͷ����������һ���ַ�����Ϊͷ��ֵ�����û��������ͷ���򷵻�`nil`��


- **__pairs()**</br>
```
for key, value in pairs(headers) do
end
```
����ÿ��ͷ���������ص�`key`��ͷ�������ַ��������ص�`value`�Ƕ�Ӧ��ͷ��ֵ�ַ�����

    **ע�⣺�ڵ�ǰ��ʵ���У��ڵ����ڼ䲻���޸�ͷ���� ���⣬�����Ҫ�ڵ���֮���޸�ͷ�����������ɵ�������ζ�ţ���Ҫʹ��break������������ǰ�˳�ѭ����������ܻ���δ���汾�н��������ơ�**

- **remove()**</br>
```
headers:remove(key)
```
ɾ��ͷ����ֵ�ԡ����`key`��Ӧ��ͷ����ֵ���ᱻɾ����


### ����API

- **length()**
```
size = buffer:length()
```
��ȡ�������Ĵ�С�����ֽ�Ϊ��λ��������һ��������

- **getBytes()**
```
buffer:getBytes(index, length)
```
�ӻ�������ȡ�ֽڡ�Ĭ������£�Envoy���Ὣ���л������ֽڸ��Ƶ�Lua�С��⽫����һ���������α����ơ�`index`��һ�����������ṩҪ���ƵĻ�������ʼ������`length`��һ���������ṩҪ���ƵĻ��������ȡ�`index`+`length`����С�ڻ��������ȡ�




## ����
- [��һ��](../HTTPfilters.md)
- [��ҳĿ¼](../../README.md)