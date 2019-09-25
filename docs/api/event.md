# 动态

## 获取动态列表

```
GET https://tower.im/api/v1/teams/{team_id}/events
```

参数

| 名称                      | 类型        | 描述               |
| ------------------------- | ----------- | ------------------ |
| `last_item_id` | Integer | 上一次获取的最后一条动态 ID, 用于分页; 默认为空 |
| `limit` | Integer | 限制获取条数，默认：20 |
| `by_member` | String | 允许为空，指定成员产生的动态 |
| `by_project` | String | 允许为空，指定项目产生的动态 |

```
Status: 200 OK

{
  "data": [
    {
      "id": "24",
      "type": "events",
      "attributes": {
        "ancestor_type": "Project",
        "ancestor_name": "Proj 0725 170506.175",
        "created_at": "2019-07-25T09:05:07.000Z",
        "action": "创建了回复",
        "title": "M 0725 170506.408"
      },
      "relationships": {
        "creator": {
          "data": {
            "id": "5206fad7bbce4c23a8e0984ba5875f0b",
            "type": "members"
          }
        }
      }
    },
    {
      "id": "23",
      "type": "events",
      "attributes": {
        "ancestor_type": "Project",
        "ancestor_name": "Proj 0725 170506.175",
        "created_at": "2019-07-25T09:05:06.000Z",
        "action": "创建了讨论",
        "title": "M 0725 170506.408"
      },
      "relationships": {
        "creator": {
          "data": {
            "id": "5206fad7bbce4c23a8e0984ba5875f0b",
            "type": "members"
          }
        }
      }
    }
  ],
  "included": [
    {
      "id": "5206fad7bbce4c23a8e0984ba5875f0b",
      "type": "members",
      "attributes": {
        "nickname": "银群惟",
        "is_active": true,
        "gavatar": "https://avatar.tower.im/default_avatars/waves.jpg",
        "role": "owner"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  }
}
```