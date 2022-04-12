# 工时

## 获取项目下所有工时

```
GET https://tower.im/api/v1/projects/{project_id}/time_logs
```

参数

| 名称                      | 类型        | 描述               |
| ------------------------- | ----------- | ------------------ |
| `{ page: { number: 1 } }` | URLEncoding | page 从 1 开始计数,也可以使用 page[number] = 1 |
| creator_id | `string` | 负责人 |
| starts_at_start | `string` | 开始时间起 |
| starts_at_end | `string` | 开始时间止 |
| ends_at_start | `string` | 结束时间起 |
| ends_at_end | `string` | 结束时间止 |

```json
Status: 200 OK

{
  "data": [
    {
      "id": "1",
      "type": "time_logs",
      "attributes": {
        "desc": "description",
        "starts_at": "2022-04-04T16:00:00.000+08:00",
        "ends_at": "2022-04-04T17:00:00.000+08:00",
        "duration": 10,
        "created_at": "2022-04-04T17:00:00.000+08:00",
        "updated_at": "2022-04-04T17:00:00.000+08:00"
      },
      "relationships": {
        "todo": {
          "data": {
            "id": "d8d23843e2fcbe71355b1ffb0dc12a5b",
            "type": "todos"
          }
        },
        "creator": {
          "data": {
            "id": "227a7273e8cc049495a832091160369b",
            "type": "members"
          }
        }
      }
    },
  ],
  "included": [
    {
      "id": "227a7273e8cc049495a832091160369b",
      "type": "members",
      "attributes": {
        "nickname": "nickname",
        "is_active": true,
        "gavatar": "https://avatar.tower.im",
        "role": "admin"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  },
}
```

## 获取任务下所有工时

```
GET https://tower.im/api/v1/todos/{todo_id}/time_logs
```

参数

| 名称                      | 类型        | 描述               |
| ------------------------- | ----------- | ------------------ |
| `{ page: { number: 1 } }` | URLEncoding | page 从 1 开始计数,也可以使用 page[number] = 1 |

```json
Status: 200 OK

{
  "data": [
    {
      "id": "1",
      "type": "time_logs",
      "attributes": {
        "desc": "description",
        "starts_at": "2022-04-04T16:00:00.000+08:00",
        "ends_at": "2022-04-04T17:00:00.000+08:00",
        "duration": 10,
        "created_at": "2022-04-04T17:00:00.000+08:00",
        "updated_at": "2022-04-04T17:00:00.000+08:00"
      },
      "relationships": {
        "todo": {
          "data": {
            "id": "d8d23843e2fcbe71355b1ffb0dc12a5b",
            "type": "todos"
          }
        },
        "creator": {
          "data": {
            "id": "227a7273e8cc049495a832091160369b",
            "type": "members"
          }
        }
      }
    },
  ],
  "included": [
    {
      "id": "227a7273e8cc049495a832091160369b",
      "type": "members",
      "attributes": {
        "nickname": "nickname",
        "is_active": true,
        "gavatar": "https://avatar.tower.im",
        "role": "admin"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  },
}
```


## 添加工时

```
POST https://tower.im/api/v1/todos/{todo_id}/time_logs
```

参数

| 名称                                                                                                | 类型   | 描述                                           |
| --------------------------------------------------------------------------------------------------- | ------ | ---------------------------------------------- |
| `{ "time_log": { "starts_at": "2022-04-04T14:00", "ends_at": "2022-04-04T16:00", "creator_id": "227a7273e8cc049495a832091160369b", "desc": "description"} }` | `json` | 开始时间、结束时间、负责人（成员 ID）、工时描述 |

```json
Status: 200 OK

{
  "data": {
    "id": "1",
    "type": "time_logs",
    "attributes": {
      "desc": "description",
      "starts_at": "2022-04-04T14:00:00.000+08:00",
      "ends_at": "2022-04-04T16:00:00.000+08:00",
      "duration": 120,
      "created_at": "2022-04-04T19:01:11.000+08:00",
      "updated_at": "2022-04-04T19:01:11.000+08:00"
    },
    "relationships": {
      "todo": {
        "data": {
          "id": "1961732fadad7d9fe5e50426a45b8817",
          "type": "todos"
        }
      },
      "creator": {
        "data": {
          "id": "227a7273e8cc049495a832091160369b",
          "type": "members"
        }
      }
    }
  },
  "included": [
    {
      "id": "227a7273e8cc049495a832091160369b",
      "type": "members",
      "attributes": {
        "nickname": "nickname",
        "is_active": true,
        "gavatar": "https://avatar.tower.im",
        "role": "admin"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  }
}
```

## 更新工时信息

```
PATCH https://tower.im/api/v1/time_logs/{time_log_id}
```

参数

| 名称                                                                                                | 类型   | 描述                                           |
| --------------------------------------------------------------------------------------------------- | ------ | ---------------------------------------------- |
| `{ "time_log": { "starts_at": "2022-04-04T14:00", "ends_at": "2022-04-04T16:00", "creator_id": "227a7273e8cc049495a832091160369b", "desc": "new description"} }` | `json` | 开始时间、结束时间、负责人（成员 ID）、工时描述 |

```json
Status: 200 OK

{
  "data": {
    "id": "1",
    "type": "time_logs",
    "attributes": {
      "desc": "new description",
      "starts_at": "2022-04-04T14:00:00.000+08:00",
      "ends_at": "2022-04-04T16:00:00.000+08:00",
      "duration": 120,
      "created_at": "2022-04-04T19:01:11.000+08:00",
      "updated_at": "2022-04-04T19:01:11.000+08:00"
    },
    "relationships": {
      "todo": {
        "data": {
          "id": "1961732fadad7d9fe5e50426a45b8817",
          "type": "todos"
        }
      },
      "creator": {
        "data": {
          "id": "227a7273e8cc049495a832091160369b",
          "type": "members"
        }
      }
    }
  },
  "included": [
    {
      "id": "227a7273e8cc049495a832091160369b",
      "type": "members",
      "attributes": {
        "nickname": "nickname",
        "is_active": true,
        "gavatar": "https://avatar.tower.im",
        "role": "admin"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  }
}
```

## 删除工时

```
DELETE https://tower.im/api/v1/time_logs/{time_log_id}
```

```
Status: 204 OK
```
