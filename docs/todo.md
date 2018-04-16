# Todo API

## Get todolist all todos

```
GET /todolists/{todolist_id}/todos
```
>all active uncompleted todos

```
Status: 200 OK
```

## Create Todo

```
POST /todolists/{todolist_id}/todos
```

Parameters

Name|Type|Description|
--|--|--|
`{ todo: { content: 'Todo', desc: 'Todo Desc', assignee_id: '', due_at: '2018-01-09' } }`|`json`| todo info

```
Status: 200 OK
```

## Get Todo

```
GET /todos/{todo_id}
```

```
Status: 200 OK
```

## Update Todo

```
PATCH /todos/{todo_id}
```

Parameters

Name|Type|Description|
--|--|--|
`{ todo: { content: 'Todo', desc: 'Todo Desc', assignee_id: '', due_at: '2018-01-09' } }`|`json`| todo info

> dueAt and assignee is optional.

```
Status: 200 OK
```

## Delete Todo

```
DELETE /todos/{todo_id}
```

```
Status: 200 OK
```

## Complete todo

```
POST /todos/{todo_id}/completion
```

```
Status: 200 OK
```

## Open todo

```
DELETE /todos/{todo_id}/completion
```

```
Status: 200 OK
```

## Comment

```
POST /todos/{id}/comments
```

Parameters

Name|Type|Description|
--|--|--|
`id`|`string`|todo id
`{"todos_comment": {"content": "comment content"}}`|`json`|comment

> 评论中 @ 他人，需要将评论中的`@Tower`转化成`<a href=\"/members/{member_id}\" data-mention=\"true\">@Tower</a>`

```
Status: 200 OK

{
    "data": {
        "id": "9dce33eb2cd24",
        "type": "comments",
        "attributes": {
            "content": "text",
            "created_at": "2018-03-28T11:10:30.000+08:00",
            "updated_at": "2018-03-28T11:10:30.000+08:00"
        },
        "relationships": {
            "creator": {
                "data": {
                    "id": "b79acb8a6816467c9a926a3d053ac5f0",
                    "type": "members"
                }
            }
        }
    },
    "included": [
        {
            "id": "b79acb8a6816",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/gavatar",
                "role": "admin",
                "created_at": "2017-09-04T15:23:25.000+08:00",
                "updated_at": "2018-03-27T15:14:26.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "82196e7031a24",
                        "type": "teams"
                    }
                }
            }
        },
        {
            "id": "82196e7031a24a",
            "type": "teams",
            "attributes": {
                "name": "Me",
                "created_at": "2017-07-12T10:47:29.000+08:00",
                "updated_at": "2018-03-27T09:57:54.000+08:00"
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## Assigned todo

```
PATCH	/todos/{todo_id}/assignment
```

Parameters

Name|Type|Description|
--|--|--|
`{ todos_assignment: { assignee_id: 'member id' } }`|`json`| member id

```
Status: 200 OK
```

## Remove assigner

```
DELETE /todos/{todo_id}/assignment
```

```
Status: 200 OK
```

## Set due date

```
PATCH /todos/{todo_id}/due
```

Parameters

Name|Type|Description|
--|--|--|
`{ todos_due: { due_at: '2018-01-10' } }`|`json`| member id

```
Status: 200 OK
```

## Set todo description

```
PATCH /todos/{todo_id}/desc
```

Parameters

Name|Type|Description|
--|--|--|
`{ todos_desc: { desc: 'Todo Desc' } }`|`json`| member id

```
Status: 200 OK
```


