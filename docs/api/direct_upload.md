# 上传附件

# 获取客户端直传签名


> Tower 使用阿里云 OSS 文件存储，支持客户端 javascript 直传，文件上传前需通过本 API 接口获取对应的签名和上传地址等。
>
>[阿里云 OSS 上传相关介绍](https://help.aliyun.com/document_detail/31925.html?spm=a2c4g.11186623.4.1.251f6e28B7NbtY)


```
POST https://tower.im/api/v1/teams/{team_id}/direct_uploads
```

参数

| 名称                      | 类型        | 描述               |
| ------------------------- | ----------- | ------------------ |
| filename | `string` | 文件名 |
| byte_size | `integer` | 文件大小，单位字节 |
| md5 | `string` | 文件内容的 md5 签名 |


Status: 200 OK

```json

{
  "guid": "d326b6e2c7a22d472dab783894fe0024",
  "directUpload": {
    "OSSAccessKeyId": "your_aliyun_key",
    "policy": "eyJleHBpcmF0aW9uIjoiMjAxOS0wNy0yNVQxMjoyMDowMS4wMDBaIiwiY29uZGl0aW9ucyI6W3siYnVja2V0IjoidG93ZXIyIn0sWyJlcSIsIiRrZXkiLCI2NDEvZDMyNmI2ZTJjN2EyMmQ0NzJkYWI3ODM4OTRmZTAwMjQiXV19",
    "Signature": "5r9OKoFQrkZKrAGFd7e9IMoP8N8=",
    "url": "https://alioss.tower.im/",
    "callback": "eyJjYWxsYmFja1VybCI6Imh0dHBzOi8vdG93ZXIuaW0vb3NzL2F0dGFjaG1lbnRzL2NhbGxiYWNrLmpzb24iLCJjYWxsYmFja0hvc3QiOiJ0b3dlci5pbSIsImNhbGxiYWNrQm9keSI6ImtleT0ke29iamVjdH1cdTAwMjZzaXplPSR7c2l6ZX1cdTAwMjZtaW1lVHlwZT0ke21pbWVUeXBlfVx1MDAyNmhlaWdodD0ke2ltYWdlSW5mby5oZWlnaHR9XHUwMDI2d2lkdGg9JHtpbWFnZUluZm8ud2lkdGh9XHUwMDI2ZmlsZW5hbWU9dGVzdC5wbmdcdTAwMjZhdHRmaWxlX2d1aWQ9ZDMyNmI2ZTJjN2EyMmQ0NzJkYWI3ODM4OTRmZTAwMjQiLCJjYWxsYmFja0JvZHlUeXBlIjoiYXBwbGljYXRpb24veC13d3ctZm9ybS11cmxlbmNvZGVkIn0=",
    "key": "641/d326b6e2c7a22d472dab783894fe0024"
  }
}
```

