### www��World Wide Web��
> ��Ҫ����������
- URI �׳���ַ
- HTTP ��̨����֮��Ĵ���Э��
- HTML ���ı�������ԣ�����ҳ����ת
> URL���������������һ����ҳ��HTTP���������������������ҳ�棬HTML�������ܿ��������ҳ��
### URI ��ʲô��ͳһ��Դ��ʶ����
URI��Ϊ����URL��ͳһ��Դ��λ������URN��ͳһ��Դ���ƣ�
#### URN
> ISBN:9934123123123 ��ţ������һ��URN ����ȷ��һ��"Ψһ��"��Դ
#### URL
> https://www.baidu.com/s?wd=hello&rev_spt=1#5
- https����--Э��
- www.baidu.com ����--����
- /s����--·��
- wd=hello&rev_spt=1����--��ѯ����
- ��#5�� ����--ê�� 
> .com����һ��(����)���� baidu����������� www����������
> ����һ��Ĺ���ʦ�����.com���Ե�,��baidu����һ������ ��ʱҪ�Բ���˵���Ǵ��
### URL�ĳ������
#### DNS ����������
> ������������ nslookup www.baidu.com�Ϳ��Կ��������ַ��Ӧ�����������Ϣ
```

Server: 192.168.5.1   
������ҵ�·��(��ȥ�ʵĵ��ţ����Ű��������ַ��Ӧ��ip����Ϊʲô֪���㻨Ǯ��)
Address:  192.168.5.1#53

Name:  www.baidu.com 
Address:  119.75.213.61 ���������������ٶȵ�ip ÿ���˷��ص�IP��һ��

```
> dns�����һ����������һ��ip 
���ҿ��Բ�����ָ��һ��ip�����ԣ����������ƹ�dns�Լ�ָ��һ��ip
�ǳ�ʱ�ڿ����޸�host�ļ�(windowϵͳ)�Լ�ָ��google��ip
��Ϊ���ŷ��ص�ip�Ǵ�ġ�


![ʾ��ͼ](https://sltrust.github.io/note/img/note006_1.png)

#### http
![ʾ��ͼ](https://sltrust.github.io/note/img/note006_2.png)

#### curl ����
```
 curl -s -v -H "hjx:xxx" -- "https://www.baidu.com"
```
- -s������ʾ����
- -v������ʾ�������Ӧ
- -H "hjx:xxx" ���һ������ͷ
- -- 'https://www.baidu.com ' ����Ҫ�������ַ
```
* Rebuilt URL to: https://www.baidu.com/
*   Trying 119.75.216.20...
* TCP_NODELAY set
...
*  SSL certificate verify ok.

> GET / HTTP/1.1    "/"�����Ŀ¼ HTTP/1.1����Э��Ͱ汾��
> Host: www.baidu.com   ���Ƿ��ʵ�����
> User-Agent: curl/7.55.1  ���õ�ʲô����������Ӧ
> Accept: */*   �ҽ����㷵�ظ��ҵ��κ�����
> hjx:xxx   ����ɾ��û���κ�����  ɾ�� - H�����Ϳ���
>    

< HTTP/1.1 200 OK
< Accept-Ranges: bytes
< Cache-Control: private, no-cache, no-store, proxy-revalidate, no-transform
< Connection: Keep-Alive
< Content-Length: 2443
< Content-Type: text/html
< Date: Tue, 02 Jan 2018 15:44:59 GMT
< Etag: "588603ec-98b"
< Last-Modified: Mon, 23 Jan 2017 13:23:56 GMT
< Pragma: no-cache
< Server: bfe/1.0.8.18
< Set-Cookie: BDORZ=27315; max-age=86400; domain=.baidu.com; path=/
<
* Connection #0 to host www.baidu.com left intact
```
-  *��ͷ�Ĵ���ע��
- ��>�� ������������
- ��<�� ������Ӧ����

�����޸�����
```
curl -X POST -s -v -H "hjx:xxx" -- "https://www.baidu.com" 
```
���������Ϊ
```
POST / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
hjx: xxx
```
�����޸�
```
curl -X POST -d "1234567890" -s -v -H "hjx: xxx" -- "https://www.baidu.com"
```
```
POST / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
hjx: xxx
Content-Length: 10  �����ϴ����ݵ��ֽ�
Content-Type: application/x-www-form-urlencoded �ϴ��ĸ�ʽ

1234567890
```
#### get��post������
- get���ǻ�ȡ���� 
- post�����ϴ�����
> ���� 
```
curl -s -v -H "host:www.qq.com" -- "https://www.baidu.com" �޸ķ��ʵ�����
�൱����ȥ��������û���ϱ��������
```
### ����ĸ�ʽ
>1 ���� ·�� Э��/�汾   ��һ����·�����д һ��Ҫ��"/"��ͷ
2 Key1: value1      �ڶ����� ��ֵ��
2 Key2: value2
2 Key3: value3
2 Content-Type: application/x-www-form-urlencoded
2 Host: www.baidu.com
2 User-Agent: curl/7.54.0
3   �س�     ��һ��Ŀ������ �ڶ����ֺ͵��Ĳ��� 
4 Ҫ�ϴ�������

1.�����������Ĳ��֣����ٰ��������֡���Ҳ����˵���Ĳ��ֿ���Ϊ�գ�
2.����������Զ����һ���س���\n��
3.������ GET POST PUT PATCH DELETE HEAD OPTIONS ��
- PUT ���� ���л��滻��һ�� �������
- PATCH ���� ���л�������һ���滻 һ�� �ֲ�����
- DELETE ɾ��
4.�����·����������ѯ������������������ê�㡹
5.�����û��д·������ô·��Ĭ��Ϊ /
6.�� 2 �����е� Content-Type ��ע�˵� 4 ���ֵĸ�ʽ
> x-www-form-urlencoded 
- x ����û�б�д��淶�ĸ�ʽ
- www ��ά��
- urlencoded ��������

#### �� Chrome �鿴��Ӧ
1.�� Network
2.������ַ
3.ѡ�е�һ����Ӧ
4.�鿴 Response Headers�������view source���������view source���������view source��
5.��ῴ����Ӧ��ǰ������
6.�鿴 Response ���� Preview����ῴ����Ӧ�ĵ� 4 ����
#### http ��https
> http�����Ĵ��� ������ĵ�¼������˱��˿��Կ������Ǽ��ܵ�
> https ���� ������Щ�����Ǿ������ܵ� �޷�ֱ�ӿ�������

### ��Ӧ
������֮��Ӧ�ö��ܵõ�һ����Ӧ�����Ƕ����ˣ����߷�����崻��ˡ�

��Ӧʾ��
������������ʾ����ǰ���������Ӧ����Ӧ�ֱ�Ϊ

HTTP/1.1 200 OK
Accept-Ranges: bytes
Cache-Control: private, no-cache, no-store, proxy-revalidate, no-transform
Connection: Keep-Alive
Content-Length: 2443
Content-Type: text/html
Date: Tue, 10 Oct 2017 09:14:05 GMT
Etag: "5886041d-98b"
Last-Modified: Mon, 23 Jan 2017 13:24:45 GMT
Pragma: no-cache
Server: bfe/1.0.8.18
Set-Cookie: BDORZ=27315; max-age=86400; domain=.baidu.com; path=/

<!DOCTYPE html>
<!--STATUS OK--><html> <head> ����̫����ʡ���ˡ���
HTTP/1.1 302 Found
Connection: Keep-Alive
Content-Length: 17931
Content-Type: text/html
Date: Tue, 10 Oct 2017 09:19:47 GMT
Etag: "54d9749e-460b"
Server: bfe/1.0.8.18

<html>
<head>
<meta http-equiv="content-type" content="text/html;charset=utf-8"> ����̫����ʡ���ˡ���
GET ����� POST �����Ӧ����Ӧ����һ����Ҳ���Բ�һ��
��Ӧ�ĵ��Ĳ��ֿ��Ժܳ��ܳ��ܳ�
��Ӧ�ĸ�ʽ
>1 Э��/�汾�� ״̬�� ״̬����
2 Key1: value1
2 Key2: value2
2 Content-Length: 17931
2 Content-Type: text/html 
3
4 Ҫ���ص�����

#### ״̬��Ҫ�����Ƿ������������˵�Ļ�
1xx ������
2xx ��ʾ�ɹ�  
3xx ��ʾ����
4xx ��ʾ��Ѿ����
5xx ��ʾ�ðɣ��Ҵ���
>200 һ��ĳɹ�  
204 �����ɹ� һ��post����204
301 ��ʾ����ʵ���Դ�Ѿ������� Ǩ�Ƶ������������������µĵ�ַ
>302 ��ʾ����ʵ���Դֻ����ʱ������ ������Ϣ�����һ��ʱ��
304 ��ʾ����ʵ����ݺ���һ��һ��,������һ�ε�����
404 δ�ҵ�ҳ��  ��ַ����
502 ����������

״̬����ûʲô��
�� 2 �����е� Content-Type ��ע�˵� 4 ���ֵĸ�ʽ
�� 2 �����е� Content-Type ��ѭ MIME �淶
�� Chrome �鿴��Ӧ
�� Network
������ַ
ѡ�е�һ����Ӧ
�鿴 Response Headers�������view source���������view source���������view source��
��ῴ����Ӧ��ǰ������
�鿴 Response ���� Preview����ῴ����Ӧ�ĵ� 4 ����

