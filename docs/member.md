# 成员

## 获取团队全部成员

```
GET /teams/{team_id}/members
```

```
Status: 200 OK

{
    "data": [
        {
            "id": "c979895c5a754c35b3e98f1c7268724c",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/658e007790c24bcb9745172",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:35:29.000+08:00",
                "updated_at": "2018-04-16T16:36:50.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "1f9118b07cf1485ba4b97a4cbc50",
                        "type": "teams"
                    }
                },
                "groups": {
                    "data": []
                }
            }
        }
    ],
    "included": [
        {
            "id": "1f9118b07cf1485ba4b97a4cbc50b",
            "type": "teams",
            "attributes": {
                "name": "Tower Team",
                "created_at": "2018-04-16T16:35:29.000+08:00",
                "updated_at": "2018-04-16T16:36:56.000+08:00"
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 获取当前账户在团队中的信息

```
GET /teams/{team_id}/member
```

```
Status: 200 OK

{
    "data": {
        "id": "c979895c5a754c35b3e98f1c72",
        "type": "members",
        "attributes": {
            "nickname": "nickname",
            "is_active": true,
            "gavatar": "https://avatar.tower.im/658e007790c24bcb9745172",
            "role": "owner",
            "comment": null,
            "phone": null,
            "created_at": "2018-04-16T16:35:29.000+08:00",
            "updated_at": "2018-04-16T16:36:50.000+08:00"
        },
        "relationships": {
            "team": {
                "data": {
                    "id": "1f9118b07cf1485ba4b97a4c",
                    "type": "teams"
                }
            },
            "groups": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "1f9118b07cf1485ba4b97a4cb",
            "type": "teams",
            "attributes": {
                "name": "Tower Team",
                "created_at": "2018-04-16T16:35:29.000+08:00",
                "updated_at": "2018-04-16T16:36:56.000+08:00"
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 获取成员信息

```
GET /member/{member_id}
```

```
Status: 200 OK
```

## 获取指派给成员未完成任务

```
GET /members/{member_id}/assigned_uncompleted_todos	
```
> box 为分类属性，不要使用到期日作为分类。
> `0`代表新任务，`1`代表今天，`2`代表接下来，`3`代表以后

```
Status: 200 OK
```

## 获取指派给成员已完成任务

```
GET /members/{member_id}/assigned_completed_todos	
```

参数

名称|类型|描述|
--|--|--|
`{ page: { number: 1 } }`|URLEncoding| page 从 1 开始计数

```
Status: 200 OK
```

## 获取成员创建的未完成任务

```
GET /members/{member_id}/created_uncompleted_todos	
```

```
Status: 200 OK
```

## 获取成员创建的已完成任务

```
GET /members/{member_id}/created_completed_todos	
```

参数

名称|类型|描述|
--|--|--|
`{ page: { number: 1 } }`|URLEncoding| page 从 1 开始计数

```
Status: 200 OK
```

