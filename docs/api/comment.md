# 评论

## 获取任务/任务清单/讨论/文件的评论

```
GET https://tower.im/api/v1/todos/{todo_id}/comments
GET https://tower.im/api/v1/todolists/{todolist_id}/comments
GET https://tower.im/api/v1/topics/{topic_id}/comments
GET https://tower.im/api/v1/uploads/{upload_id}/comments
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
      "type": "comments",
      "attributes": {
        "content": "content",
        "created_at": "2022-08-04T17:00:00.000+08:00",
        "updated_at": "2022-08-04T17:00:00.000+08:00"
      },
      "relationships": {
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
