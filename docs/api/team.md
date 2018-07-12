# 团队

## 获取加入的团队列表

```
GET https://tower.im/api/v1/teams
```

```json
Status: 200 OK

{
    "data": [
        {
            "id": "3fbe491eef5c4fbeaaabc1716b7",
            "type": "teams",
            "attributes": {
                "name": "team 1",
                "created_at": "2014-05-15T10:32:12.000+08:00",
                "updated_at": "2018-02-10T05:44:59.000+08:00"
            }
        },
        {
            "id": "3fbe491eef5c4fbeaaabc1716b7",
            "type": "teams",
            "attributes": {
                "name": "team 2",
                "created_at": "2017-07-12T10:47:29.000+08:00",
                "updated_at": "2018-04-16T10:16:34.000+08:00"
            }
        },
        {
            "id": "3fbe491eef5c4fbeaaabc1716b7",
            "type": "teams",
            "attributes": {
                "name": "team 3",
                "created_at": "2017-11-30T11:51:34.000+08:00",
                "updated_at": "2018-01-23T12:24:34.000+08:00"
            }
        },
        {
            "id": "3fbe491eef5c4fbeaaabc1716b7",
            "type": "teams",
            "attributes": {
                "name": "API Team",
                "created_at": "2018-04-16T16:07:34.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 创建团队

```
POST https://tower.im/api/v1/teams
```

参数

| 名称                                   | 类型   | 描述      |
| -------------------------------------- | ------ | --------- |
| `{ "team": { "name": "Tower Team" } }` | `json` | team name |

```json
Status: 200 OK

{
    "data": {
        "id": "1f9118b07cf1485ba4b97a4cbc5",
        "type": "teams",
        "attributes": {
            "name": "Tower Team",
            "created_at": "2018-04-16T16:35:29.000+08:00",
            "updated_at": "2018-04-16T16:35:29.000+08:00"
        }
    },
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 更改团队名称

```
PATCH https://tower.im/api/v1/teams/{id}
```

参数

| 名称                                 | 类型   | 描述      |
| ------------------------------------ | ------ | --------- |
| `{ team: { name: 'Tower Team 2' } }` | `json` | team name |

```
Status: 200 OK

{
    "data": {
        "id": "1f9118b07cf1485ba4b97a4cbc50bba8",
        "type": "teams",
        "attributes": {
            "name": "Tower Team 2",
            "created_at": "2018-04-16T16:35:29.000+08:00",
            "updated_at": "2018-04-16T16:36:56.000+08:00"
        }
    },
    "jsonapi": {
        "version": "1.0"
    }
}
```


