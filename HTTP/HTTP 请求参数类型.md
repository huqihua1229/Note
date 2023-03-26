# HTTP 请求参数类型

## GET 请求

URL参数拼接方式：url + ？ 参数 = 参数内容 & 参数 = 参数类型 &...

## POST 请求

* **form-data(multipart/form-data)，支持上传文件的表单类型**
  
  form-data对应着http请求中的Content-Type=multipart/form-data, 一般在表单中如果需要进行文件上传时，就需要使用该格式。
  
  它会将表单的数据处理为一条消息，以标签为单元，用分隔符分开。既可以上传键值对，也可以上传文件File。当上传的字段是文件时，会有Content-Type来说明文件类型；content-disposition用来说明一些字段信息；
  
  由于有boundary隔离，所以multipart/form-data既可以上传文件，也可以上传键值对，它采用了键值对的方式，所以**可以上传多个文件**

* **x-www-form-urlencoded，表单类型的接口请求**
  
  对应着http请求中的Content-Type为application/x-www-from-urlencoded,会将表单内的数据转换为键值对，比如,name=python&age = 22，这种方式**只能以键值对形式发送参数**，一般如果不指定content-type，默认便是application/x-www-form-urlencoded

* **raw（支持各种原生的类型，JSON类型的接口请求）**
  
  如：Content-Type=application/json时，则可以使用这种方式，这个是实际接口测试中，使用到最多的方式了。越来越多的人把它作为请求头，用来告诉服务端消息主体是序列化后的 JSON 字符串
  
  他是**可以上传任意格式的参数**，可以上传text、json、xml、html、js

* **binary（二进制，流类型的接口请求 ）**
  
  对应着http请求中的Content-Type:application/octet-stream，只可以上传二进制数据，通常用来上传文件，由于没有键值，所以，**一次只能上传一个文件**


