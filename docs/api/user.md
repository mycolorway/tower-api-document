# 用户

## 获取当前账号信息

```
GET /user
```

```
Status: 200 OK

{
    "data": {
        "id": "fc6527027d1c4d4c935e618",
        "type": "users",
        "attributes": {
            "nickname": "nickname",
            "email": "email",
            "gavatar": "https://avatar.tower.im/658e00779",
            "created_at": "2014-05-15T10:43:26.000+08:00",
            "updated_at": "2018-04-16T15:55:31.000+08:00"
        }
    },
    "jsonapi": {
        "version": "1.0"
    }
}
```
