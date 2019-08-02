# 讨论

## 获取项目讨论列表

```
GET https://tower.im/api/v1/projects/{project_id}/topics
```


Status: 200 OK

```json
{
  "data": [
    {
      "id": "0800afd15d7471e4b90a499e02dc4652",
      "type": "topics",
      "attributes": {
        "content": "失声痛哭洁白如玉婀娜多姿千奇百怪啼冰天雪地, 日月如梭千变万化天经地义泪眼汪汪, 蛛丝马迹齐心协力扬眉吐气一触即发秋雨绵绵霎时间百感交集振奋人心对牛弹琴, 两情相悦果实累累胆小如鼠哗哗啦啦能屈能伸, 一见如故望子成龙千奇百怪乌云翻滚红日东升叶公好龙。",
        "is_archived": false,
        "created_at": "2019-07-26T01:48:37.000Z",
        "title": "M 0726 094837.243"
      },
      "relationships": {
        "creator": {
          "data": {
            "id": "61f5031ccfcabb3dd423a8a4564e3eff",
            "type": "members"
          }
        },
        "comments": {
          "data": [
            {
              "id": "9b30da26e6447c9ea07330f7dc8307b7",
              "type": "comments"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "61f5031ccfcabb3dd423a8a4564e3eff",
      "type": "members",
      "attributes": {
        "nickname": "碧鲁建意",
        "is_active": true,
        "gavatar": "https://avatar.tower.im/default_avatars/path.jpg",
        "role": "member"
      }
    },
    {
      "id": "9b30da26e6447c9ea07330f7dc8307b7",
      "type": "comments",
      "attributes": {
        "content": "C 0726 094837.357 满山遍野承上启下自高自大十分可恶管中窥豹秋高气爽, 暴雨如注众志成城生气勃勃扫视一目十行大名鼎鼎黑白分明轰轰隆隆, 江水滚滚无牵无挂古色古香子雨打风吹桃红柳绿天老地荒, 车轮滚滚暴雨如注静思默想轰轰隆隆春暖花开牛头马面赞叹不已笑容可掬。",
        "created_at": "2019-07-26T01:48:37.000Z",
        "updated_at": "2019-07-26T01:48:37.000Z"
      },
      "relationships": {
        "creator": {
          "data": {
            "id": "663d1d2e60b7f94318d9fcb0b68bf2f1",
            "type": "members"
          }
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "663d1d2e60b7f94318d9fcb0b68bf2f1",
      "type": "members",
      "attributes": {
        "nickname": "理安纯",
        "is_active": true,
        "gavatar": "https://avatar.tower.im/default_avatars/cloud.jpg",
        "role": "member"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  },
  "links": {
    "self": "https://tower.im/api/v1/projects/b0c7b5e87c84c2381ca4611476ec17d5/topics?page%5Bnumber%5D=1&page%5Bsize%5D=25",
    "first": "https://tower.im/api/v1/projects/b0c7b5e87c84c2381ca4611476ec17d5/topics?page%5Bnumber%5D=1&page%5Bsize%5D=25",
    "prev": null,
    "next": null,
    "last": "https://tower.im/api/v1/projects/b0c7b5e87c84c2381ca4611476ec17d5/topics?page%5Bnumber%5D=1&page%5Bsize%5D=25"
  }
}
```

## 创建讨论

```
POST https://tower.im/api/v1/projects/{project_id}/topics
```

参数

| 名称                                                              | 类型   | 描述          |
| ----------------------------------------------------------------- | ------ | ------------- |
| `{ "message": { "subject": "subject", "content": "content Desc" } }` | `json` | message info |
| `attfile_guids` | `array` | 可选项，上传附件列表 |


Status: 200 OK

```json
{
  "data": {
    "id": "5d0042a851132539a7d0f9508ebce48f",
    "type": "topics",
    "attributes": {
      "content": "Non sint accusantium eaque neque.",
      "is_archived": false,
      "created_at": "2019-07-26T01:54:41.000Z",
      "title": "dolorem"
    },
    "relationships": {
      "creator": {
        "data": {
          "id": "8d825acb9925f1c93019f60971f5e5b8",
          "type": "members"
        }
      },
      "comments": {
        "data": [

        ]
      },
      "attachments": {
        "data": [
          {
            "id": "dcbb9e78229637076d76673618ae9fdc",
            "type": "attachments"
          }
        ]
      }
    }
  },
  "included": [
    {
      "id": "8d825acb9925f1c93019f60971f5e5b8",
      "type": "members",
      "attributes": {
        "nickname": "从昇来",
        "is_active": true,
        "gavatar": "https://avatar.tower.im/default_avatars/waves.jpg",
        "role": "owner"
      }
    },
    {
      "id": "dcbb9e78229637076d76673618ae9fdc",
      "type": "attachments",
      "attributes": {
        "content_type": "image/png",
        "byte_size": 475,
        "width": 0,
        "height": 0,
        "created_at": "2019-07-26T01:54:40.000Z",
        "filename": "IMG_0012.PNG",
        "icon_url": "https://alioss.tower.im/oss/ab12dc67f19f8dbe559af0cae267838d_small?Expires=1564106681&OSSAccessKeyId=your_aliyun_key&Signature=MrY7l%2FSUAp0hgaCsJTT8cyLFqYw%3D&response-content-disposition=inline%3Bfilename%3D%22IMG_0012.PNG%22&response-content-type=image%2Fpng",
        "url": "https://alioss.tower.im/oss/ab12dc67f19f8dbe559af0cae267838d_large?Expires=1564106681&OSSAccessKeyId=your_aliyun_key&Signature=nYNSRRgodYuCp0nnpubOeF3RRFs%3D&response-content-disposition=inline%3Bfilename%3D%22IMG_0012.PNG%22&response-content-type=image%2Fpng"
      },
      "relationships": {
        "creator": {
          "data": {
            "id": "8d825acb9925f1c93019f60971f5e5b8",
            "type": "members"
          }
        }
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  }
}
```

## 获取讨论

```
GET https://tower.im/api/v1/topics/{id}
```

Status: 200 OK

```json
{
  "data": {
    "id": "240567b2bccda0740992028cfe2ee4be",
    "type": "topics",
    "attributes": {
      "content": "千疮百孔首烈日当空交头接耳首屈一指万众一心一泻千里名列前茅一瞬间, 满山遍野铿锵有力绿树成阴绿莹莹十万火急, 远望吉祥如意枣红四海为家。",
      "is_archived": false,
      "created_at": "2019-07-26T01:58:50.000Z",
      "title": "M 0726 095850.291"
    },
    "relationships": {
      "creator": {
        "data": {
          "id": "10d203508104b9104304fb8f5504f12d",
          "type": "members"
        }
      },
      "comments": {
        "data": [

        ]
      },
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "included": [
    {
      "id": "10d203508104b9104304fb8f5504f12d",
      "type": "members",
      "attributes": {
        "nickname": "蔡璇珊",
        "is_active": true,
        "gavatar": "https://avatar.tower.im/default_avatars/jokul.jpg",
        "role": "member"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  }
}
```

## 更新讨论

```
PATCH https://tower.im/api/v1/topics/{id}
```

参数

| 名称                                                              | 类型   | 描述          |
| ----------------------------------------------------------------- | ------ | ------------- |
| `{ "message": { "subject": "subject", "content": "content Desc" } }` | `json` | message info |
| `attfile_guids` | `array` | 可选项，上传附件列表，不传则附件不做更新，传空表示删除附件 |


Status: 200 OK

```json
{
  "data": {
    "id": "160846ca76cc680edc341621ff46fbb5",
    "type": "topics",
    "attributes": {
      "content": "Pariatur quas magnam non excepturi qui necessitatibus.",
      "is_archived": false,
      "created_at": "2019-07-26T02:03:24.000Z",
      "title": "soluta"
    },
    "relationships": {
      "creator": {
        "data": {
          "id": "3c1068e542d78318ad61145babcbfd26",
          "type": "members"
        }
      },
      "comments": {
        "data": [

        ]
      },
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "included": [
    {
      "id": "3c1068e542d78318ad61145babcbfd26",
      "type": "members",
      "attributes": {
        "nickname": "愚昆坚",
        "is_active": true,
        "gavatar": "https://avatar.tower.im/default_avatars/noon.jpg",
        "role": "member"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  }
}
```

## 删除讨论

```
DELETE https://tower.im/api/v1/topics/{id}
```

```
Status: 204 OK
```


