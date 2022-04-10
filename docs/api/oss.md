# OSS 文件

## 获取 OSS URL

```
GET https://tower.im/api/v1/attfiles/{attfile_id}/oss_url
```

> https://attachments.tower.im/tower/d15268555b8f30220bcc595cb451df9d
>
> attfile_id => d15268555b8f30220bcc595cb451df9d

参数

| 名称                      | 类型        | 描述               |
| ------------------------- | ----------- | ------------------ |
| filename | `string` | 自定义文件名 |
| version | `string` | 自定义图片大小, small、medium、large |
| download | `string` | 指定为下载链接 |
| content_type | `string` | 自定义 Content Type |

Status: 200 OK

```json
{
  "attfile_id": "d15268555b8f30220bcc595cb451df9d",
  "oss_url": "https://aliossdl1.tower.im/123456/62654e459dcae3184643be699a0ff8a4?Expires=1649587195&OSSAccessKeyId=LTAI4FzdzJ63WYH36wjrvT56&Signature=jcyeTSWOIU%2Fqm4q35ayUq2spLDg%3D&response-content-disposition=inline%3Bfilename%3D%22%E7%9C%BC%E9%95%9C%E7%8C%B4%EF%BC%9B%E5%BF%86%E6%98%94%E5%85%AE%E7%9F%A3++++-3.jpg.jpeg%22&response-content-type=image%2Fjpeg"
}
```
