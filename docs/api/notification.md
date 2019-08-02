# 通知

## 获取通知列表

```
GET https://tower.im/api/v1/teams/{team_id}/notifications
```

参数

| 名称                      | 类型        | 描述               |
| ------------------------- | ----------- | ------------------ |
| `{ page: { number: 1, size: 25 } }` | URLEncoding | page 从 1 开始计数 |

```
Status: 200 OK

{
  "data": [
    {
      "id": "d08045c534335893b63860c8ee63d802",
      "type": "notifications",
      "attributes": {
        "notifyable_type": "Message",
        "read": false,
        "target_guid": "135857b4f34e1bf76418be27b45411a3",
        "created_at": "2019-07-25T08:59:24.000Z",
        "extra_info": {
        }
      },
      "relationships": {
        "progress": {
          "data": {
            "id": "287",
            "type": "progresses"
          }
        }
      }
    }
  ],
  "included": [
    {
      "id": "287",
      "type": "progresses",
      "attributes": {
        "nickname": "毕必隆",
        "avatar": "https://avatar.tower.im/default_avatars/path.jpg",
        "subject_str": "M 0725 165924.390",
        "action_str": "创建了讨论",
        "content_str": "时高时低杀鸡取卵勃然大怒谈虎色变, 人声鼎沸秋月似钩优柔寡断生离死别行云流水, 惊慌失措天昏地暗人山人海千姿百态鱼目混珠毫无希望泪如雨下, 两全其美人声鼎沸万古长青管中窥豹胆小如鼠一毛不拔千变万化徐徐。",
        "progress_ty": "message_add"
      }
    }
  ],
  "jsonapi": {
    "version": "1.0"
  },
  "links": {
    "self": "http://test.host/api/v1/teams/52e91b1c84e56abcc899eef044f32f52/notifications?page%5Bnumber%5D=1&page%5Bsize%5D=25",
    "first": "http://test.host/api/v1/teams/52e91b1c84e56abcc899eef044f32f52/notifications?page%5Bnumber%5D=1&page%5Bsize%5D=25",
    "prev": null,
    "next": null,
    "last": "http://test.host/api/v1/teams/52e91b1c84e56abcc899eef044f32f52/notifications?page%5Bnumber%5D=1&page%5Bsize%5D=25"
  }
}

```