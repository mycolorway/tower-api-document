# 文件

## 获取项目文件列表

```
GET https://tower.im/api/v1/projects/{project_id}/uploads
```


Status: 200 OK

```json
{
  "data": [
    {
      "id": "0db8c283a993d43b41c1a50ef236767f",
      "type": "uploads",
      "attributes": {
        "name": "upload name",
        "desc": null,
        "created_at": "2019-07-26T02:10:15.000Z",
        "updated_at": "2019-07-26T02:10:15.000Z"
      },
      "relationships": {
        "attachment": {
          "data": {
            "id": "942c61fefe9c8e82071d378588bfa497",
            "type": "attachments"
          }
        },
        "comments": {
          "data": [

          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "942c61fefe9c8e82071d378588bfa497",
      "type": "attachments",
      "attributes": {
        "content_type": "image/png",
        "byte_size": 996,
        "width": 0,
        "height": 0,
        "created_at": "2019-07-26T02:10:15.000Z",
        "filename": "十分可恶",
        "icon_url": "https://alioss.tower.im/oss/ccb0bd47bb7e39efe665cedf483e80af_small?Expires=1564107615&OSSAccessKeyId=your_aliyun_key&Signature=yszDUzihq7TkifCk0skmx%2B9kUGM%3D&response-content-disposition=inline%3Bfilename%3D%22%E5%8D%81%E5%88%86%E5%8F%AF%E6%81%B6%22&response-content-type=image%2Fpng",
        "url": "https://alioss.tower.im/oss/ccb0bd47bb7e39efe665cedf483e80af_large?Expires=1564107615&OSSAccessKeyId=your_aliyun_key&Signature=ykPPDdnY%2FLafzbkwMYMbWi0Yd04%3D&response-content-disposition=inline%3Bfilename%3D%22%E5%8D%81%E5%88%86%E5%8F%AF%E6%81%B6%22&response-content-type=image%2Fpng"
      },
      "relationships": {
        "creator": {
          "data": {
            "id": "e3f9e235e2f322197eb1962ba80fa160",
            "type": "members"
          }
        }
      }
    },
    {
      "id": "e3f9e235e2f322197eb1962ba80fa160",
      "type": "members",
      "attributes": {
        "nickname": "盘典夫",
        "is_active": true,
        "gavatar": "https://avatar.tower.im/default_avatars/waves.jpg",
        "role": "member"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  }
}
```

## 创建文件

```
POST https://tower.im/api/v1/projects/{project_id}/uploads
```

参数

| 名称                                                              | 类型   | 描述          |
| ----------------------------------------------------------------- | ------ | ------------- |
| `attfile_guid` | `string` | 附件 guid |


Status: 200 OK

```json
{
  "data": {
    "id": "72f3648fbedb5d8016568a7309c03ee4",
    "type": "uploads",
    "attributes": {
      "name": "IMG_0012.PNG",
      "desc": "IMG_0012.PNG",
      "created_at": "2019-07-26T02:19:03.000Z",
      "updated_at": "2019-07-26T02:19:03.000Z"
    },
    "relationships": {
      "attachment": {
        "data": {
          "id": "1c27046caba100f6464bcd791c66ef9c",
          "type": "attachments"
        }
      },
      "comments": {
        "data": [

        ]
      }
    }
  },
  "included": [
    {
      "id": "1c27046caba100f6464bcd791c66ef9c",
      "type": "attachments",
      "attributes": {
        "content_type": "image/png",
        "byte_size": 484,
        "width": 0,
        "height": 0,
        "created_at": "2019-07-26T02:19:03.000Z",
        "filename": "IMG_0012.PNG",
        "icon_url": "https://alioss.tower.im/oss/b3b3081844814d528cd776ec83aa3352_small?Expires=1564108143&OSSAccessKeyId=your_aliyun_key&Signature=xz5HAs2LVsWGyIRnwz3YkqJmVlw%3D&response-content-disposition=inline%3Bfilename%3D%22IMG_0012.PNG%22&response-content-type=image%2Fpng",
        "url": "https://alioss.tower.im/oss/b3b3081844814d528cd776ec83aa3352_large?Expires=1564108143&OSSAccessKeyId=your_aliyun_key&Signature=9N%2F8MBOdISg3KNGkPzfZ9YWrnQE%3D&response-content-disposition=inline%3Bfilename%3D%22IMG_0012.PNG%22&response-content-type=image%2Fpng"
      },
      "relationships": {
        "creator": {
          "data": {
            "id": "a9baa588ad4db1e893e1d58fd40571f5",
            "type": "members"
          }
        }
      }
    },
    {
      "id": "a9baa588ad4db1e893e1d58fd40571f5",
      "type": "members",
      "attributes": {
        "nickname": "贡江钰",
        "is_active": true,
        "gavatar": "https://avatar.tower.im/default_avatars/cloud.jpg",
        "role": "owner"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  }
}
```

## 获取文件

```
GET https://tower.im/api/v1/uploads/{id}
```

Status: 200 OK

```json
{
  "data": {
    "id": "c50dd5fa3dee03f77b7612464213a6e0",
    "type": "uploads",
    "attributes": {
      "name": "upload name",
      "desc": null,
      "created_at": "2019-07-26T02:20:55.000Z",
      "updated_at": "2019-07-26T02:20:55.000Z"
    },
    "relationships": {
      "attachment": {
        "data": {
          "id": "9edb50c1ceb80348208691cb6db7fe1b",
          "type": "attachments"
        }
      },
      "comments": {
        "data": [

        ]
      }
    }
  },
  "included": [
    {
      "id": "9edb50c1ceb80348208691cb6db7fe1b",
      "type": "attachments",
      "attributes": {
        "content_type": "image/png",
        "byte_size": 800,
        "width": 0,
        "height": 0,
        "created_at": "2019-07-26T02:20:55.000Z",
        "filename": "鸟语花香",
        "icon_url": "https://alioss.tower.im/oss/054d9db164177fb206c00f613a20dca6_small?Expires=1564108255&OSSAccessKeyId=your_aliyun_key&Signature=dmpdQ9zT1qm1mU35flhYe6Re8kQ%3D&response-content-disposition=inline%3Bfilename%3D%22%E9%B8%9F%E8%AF%AD%E8%8A%B1%E9%A6%99%22&response-content-type=image%2Fpng",
        "url": "https://alioss.tower.im/oss/054d9db164177fb206c00f613a20dca6_large?Expires=1564108255&OSSAccessKeyId=your_aliyun_key&Signature=KIr2RH4lihg72lAClaXxuf%2B8E5g%3D&response-content-disposition=inline%3Bfilename%3D%22%E9%B8%9F%E8%AF%AD%E8%8A%B1%E9%A6%99%22&response-content-type=image%2Fpng"
      },
      "relationships": {
        "creator": {
          "data": {
            "id": "1e567de56ba46e6def9ae89dec6b3485",
            "type": "members"
          }
        }
      }
    },
    {
      "id": "1e567de56ba46e6def9ae89dec6b3485",
      "type": "members",
      "attributes": {
        "nickname": "牟伊妹",
        "is_active": true,
        "gavatar": "https://avatar.tower.im/default_avatars/cloud.jpg",
        "role": "member"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  }
}
```

## 删除文件

```
DELETE https://tower.im/api/v1/uploads/{id}
```

```
Status: 204 OK
```

## 获取附件原始地址

```
GET https://tower.im/api/v1/attfiles/{attfile_id}
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
  "url": "https://aliossdl1.tower.im/123456/62654e459dcae3184643be699a0ff8a4xxx"
}
```
