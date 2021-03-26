# 任务

## 获取清单任务

```
GET https://tower.im/api/v1/todolists/{todolist_id}/todos
```

参数

| 名称                      | 类型        | 描述               |
| ------------------------- | ----------- | ------------------ |
| `{ page: { number: 1 } }` | URLEncoding | page 从 1 开始计数,也可以使用 page[number] = 1 |
| `completed_todo` | boolean | 是否包含已完成任务，默认：false |

```json
Status: 200 OK

{
    "data": [
        {
            "id": "46d952895c10440",
            "type": "todos",
            "attributes": {
                "team_wide_id": 4116, //资源ID
                "content": "任务名称",
                "desc": "任务描述",
                "is_active": true,
                "is_completed": false,
                "due_at": null,
                "closed_at": null,
                "priority": "higher",
                "labels": ["缺陷", "v12.32"]
            },
            "relationships": {
                "creator": {
                    "data": {
                        "id": "043bd9be9c10",
                        "type": "members"
                    }
                },
                "assignee": {
                    "data": null
                },
                "closer": {
                    "data": null
                }
            }
        }
    ],
    "included": [
        {
            "id": "043bd9be9c104f0a",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/avatar",
                "role": "owner",
                "comment": "123123123123121",
                "phone": "123",
                "created_at": "2017-07-12T10:47:29.000+08:00",
                "updated_at": "2018-04-16T10:16:34.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "82196e7031a24ac",
                        "type": "teams"
                    }
                },
                "groups": {
                    "data": [
                        {
                            "id": "ab855eec4b6f49",
                            "type": "subgroups"
                        }
                    ]
                }
            }
        },
        {
            "id": "82196e7031a24",
            "type": "teams",
            "attributes": {
                "name": "name",
                "created_at": "2017-07-12T10:47:29.000+08:00",
                "updated_at": "2018-04-16T10:16:34.000+08:00"
            }
        },
        {
            "id": "ab855eec4b6f49bab8a7589408dcc29d",
            "type": "subgroups",
            "attributes": {
                "name": "groupname"
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```


`priority` 字段说明：

```
highest: 最高
higher: 较高
normal: 普通
lower: 较低
```


## 创建任务

```
POST https://tower.im/api/v1/todolists/{todolist_id}/todos
```

参数

| 名称                                                                                                | 类型   | 描述                                           |
| --------------------------------------------------------------------------------------------------- | ------ | ---------------------------------------------- |
| `{ "todo": { "content": "Todo", "desc": "Todo Desc", "assignee_id": "", "due_at": "2018-01-09", "start_at": "2018-01-01", "attfile_guids": ["guid1", "guid2", "guid3"] } }` | `json` | 任务信息，`assignee_id` 、 `due_at`、`start_at` 可设置为空 |

```json
Status: 200 OK

{
    "data": {
        "id": "2d5de72adb4e414f8f299753f4f1a87a",
        "type": "todos",
        "attributes": {
            "content": "Todo",
            "desc": "Todo Desc",
            "is_active": true,
            "is_completed": false,
            "due_at": null,
            "closed_at": null,
            "created_at": "2018-04-16T16:02:41.000+08:00",
            "updated_at": "2018-04-16T16:02:41.000+08:00"
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "0a81690ff28d45cb94e43ebf431eedff",
                    "type": "projects"
                }
            },
            "todolist": {
                "data": {
                    "id": "cf0b8fcef47d470b906859c861194f6f",
                    "type": "todolists"
                }
            },
            "creator": {
                "data": {
                    "id": "b79acb8a6816467c9a926a3d053ac5f0",
                    "type": "members"
                }
            },
            "assignee": {
                "data": null
            },
            "closer": {
                "data": null
            },
            "todos_check_items": {
                "data": []
            },
            "comments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "0a81690ff28d45cb94e43ebf431eedff",
            "type": "projects",
            "attributes": {
                "name": "艾泽拉斯大事件",
                "is_archived": false
            }
        },
        {
            "id": "cf0b8fcef47d470b906859c861194f6f",
            "type": "todolists",
            "attributes": {
                "name": "部落",
                "is_active": true,
                "is_archived": false,
                "is_default": false
            }
        },
        {
            "id": "b79acb8a6816467c9a926a3d053ac5f0",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
                "role": "admin",
                "comment": "beizhu",
                "phone": "133",
                "created_at": "2017-09-04T15:23:25.000+08:00",
                "updated_at": "2018-04-16T15:57:13.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "82196e7031a24a",
                        "type": "teams"
                    }
                },
                "groups": {
                    "data": []
                }
            }
        },
        {
            "id": "82196e7031a24ac980",
            "type": "teams",
            "attributes": {
                "name": "Me",
                "created_at": "2017-07-12T10:47:29.000+08:00",
                "updated_at": "2018-04-16T10:16:34.000+08:00"
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 获取任务信息

```
GET https://tower.im/api/v1/todos/{todo_id}
```

```json
Status: 200 OK

{
    "data": {
        "id": "c1702c95de6498b176636dde3a41ffff",
        "type": "todos",
        "attributes": {
            "team_wide_id": 5077,                           // 任务全局ID
            "content": "测试任务的子任务",                     // 任务标题
            "desc": "<p>任务描述</p>",                       // 任务描述
            "is_active": true,                             // 任务是否被删除
            "is_completed": true,                          // 任务是否被完成
            "priority": "normal",                          // 优先级
            "start_at": null,                               // 开始时间
            "due_at": "2020-12-25T23:59:59.000+08:00",      // 截止时间
            "closed_at": "2020-12-24T11:59:37.000+08:00",   // 完成时间
            "created_at": "2020-12-24T11:55:58.000+08:00",  // 创建时间
            "updated_at": "2020-12-24T11:59:37.000+08:00",  // 最后更新时间
            "labels": []
        },
        "relationships": {                                   // 关联关系
            "project": {
                "data": {
                    "id": "84b9c4fc92260d19243f357951f57782",   // 所在项目 (将被废弃, 请使用 todolists 字段)
                    "type": "projects"
                }
            },
            "todolist": {                                       // 所在清单 (将被废弃, 请使用 todolists 字段)
                "data": {
                    "id": "22e916a097226715c2d9fab0185191d0",
                    "type": "todolists"
                }
            },
            "creator": {                                      //  创建人
                "data": {
                    "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                    "type": "members"
                }
            },
            "assignee": {                                      // 负责人
                "data": {
                    "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                    "type": "members"
                }
            },
            "closer": {                                      // 完成人
                "data": {
                    "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                    "type": "members"
                }
            },
            "parent": {                                      // 父任务, 若该任务已经是父任务时, 该字段为null
                "data": {
                    "id": "529739f6b7df21647c98d037752cf388",
                    "type": "todos"
                }
            },
            "custom_field_value": {                           // 自定义任务字段
                "data": {
                    "id": "1370",
                    "type": "todos_custom_field_values"
                }
            },
            "sub_todos": {                                      // 子任务
                "data": [
                    {
                        "id": "76edaceffcf8478251a2ca1536d11763",
                        "type": "todos"
                    }
                ]
            },
            "comments": {                                      // 评论
                "data": [
                    {
                        "id": "40f30cadf068d2ca424ef1c3b11f4c03",
                        "type": "comments"
                    }
                ]
            },
            "todolists": {                                      // 所属清单, 当任务被映射到其他清单时, 这个字段会展示该任务所属的所有清单
                "data": [
                    {
                        "id": "a6bd7d78ee75f53356edd743139267ca",
                        "type": "todolists"
                    },
                    {
                        "id": "b6ea561ad149893ae699c4b55935faca",
                        "type": "todolists"
                    }
                ]
            },
            "attachments": {                                      // 附件
                "data": []
            }
        }
    },
    "included": [                                               // 对应relations里相应字段的具体值
        {
            "id": "84b9c4fc92260d19243f357951f57782",
            "type": "projects",
            "attributes": {
                "name": "星辰大海",
                "is_archived": false
            }
        },
        {
            "id": "22e916a097226715c2d9fab0185191d0",
            "type": "todolists",
            "attributes": {
                "name": "清单外任务",
                "is_active": true,
                "is_archived": false,
                "is_default": true
            },
            "relationships": {
                "project": {
                    "data": {
                        "id": "84b9c4fc92260d19243f357951f57782",
                        "type": "projects"
                    }
                }
            }
        },
        {
            "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
            "type": "members",
            "attributes": {
                "nickname": "本地开发",
                "is_active": true,
                "gavatar": "https://avatar-local.oss-cn-hangzhou.aliyuncs.com/default_avatars/jokul.jpg",
                "role": "owner"
            }
        },
        {
            "id": "529739f6b7df21647c98d037752cf388",
            "type": "todos",
            "attributes": {
                "team_wide_id": 5076,
                "content": "测试任务",
                "desc": "<p>任务描述</p>",
                "is_active": true,
                "is_completed": true,
                "priority": "normal",
                "start_at": null,
                "due_at": "2020-12-24T23:59:59.000+08:00",
                "closed_at": "2020-12-24T11:57:59.000+08:00",
                "created_at": "2020-12-24T11:53:57.000+08:00",
                "updated_at": "2020-12-24T11:59:37.000+08:00",
                "labels": []
            },
            "relationships": {
                "project": {
                    "data": {
                        "id": "84b9c4fc92260d19243f357951f57782",
                        "type": "projects"
                    }
                },
                "todolist": {
                    "data": {
                        "id": "a56acdd10c82544673729f6d31bdcf11",
                        "type": "todolists"
                    }
                },
                "creator": {
                    "data": {
                        "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                        "type": "members"
                    }
                },
                "assignee": {
                    "data": {
                        "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                        "type": "members"
                    }
                },
                "closer": {
                    "data": {
                        "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                        "type": "members"
                    }
                },
                "parent": {
                    "data": null
                },
                "custom_field_value": {
                    "data": {
                        "id": "1369",
                        "type": "todos_custom_field_values"
                    }
                },
                "sub_todos": {
                    "data": [
                        {
                            "id": "c1702c95de6498b176636dde3a41ffff",
                            "type": "todos"
                        }
                    ]
                },
                "comments": {
                    "data": [
                        {
                            "id": "4f4d930f374e1c13a8de480442663eef",
                            "type": "comments"
                        }
                    ]
                },
                "todolists": {
                    "data": [
                        {
                            "id": "a56acdd10c82544673729f6d31bdcf11",
                            "type": "todolists"
                        },
                        {
                            "id": "8359dd2b0f0fd7e42ab411809516574d",
                            "type": "todolists"
                        }
                    ]
                },
                "attachments": {
                    "data": []
                }
            }
        },
        {
            "id": "a56acdd10c82544673729f6d31bdcf11",
            "type": "todolists",
            "attributes": {
                "name": "开发中",
                "is_active": true,
                "is_archived": false,
                "is_default": false
            },
            "relationships": {
                "project": {
                    "data": {
                        "id": "84b9c4fc92260d19243f357951f57782",
                        "type": "projects"
                    }
                }
            }
        },
        {
            "id": "1369",
            "type": "todos_custom_field_values",
            "attributes": {
                "custom_fields": {
                    "Y4B7RiMh": {
                        "name": "任务估点",
                        "value": null,
                        "field_type": "number"
                    },
                    "dpuFMjpZ": {
                        "name": "Intercom URL",
                        "value": null,
                        "field_type": "string"
                    },
                    "SkFsCU6t": {
                        "name": "截止日期",
                        "value": null,
                        "field_type": "date"
                    },
                    "member_GrB9U8fJ": {
                        "name": "维护人",
                        "value": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                        "field_type": "member"
                    },
                    "select_WDvNVBqF": {
                        "name": "性别",
                        "value": "男",
                        "field_type": "select"
                    },
                    "hyperlink_u9zxhyL7": {
                        "name": "链接地址",
                        "value": null,
                        "field_type": "hyperlink"
                    },
                    "string_YyDEkeKe": {
                        "name": "地址",
                        "value": null,
                        "field_type": "string"
                    },
                    "select_C4SJPfKe": {
                        "name": "单选字段",
                        "value": "A",
                        "field_type": "select"
                    },
                    "member_CknmgKqD": {
                        "name": "成员选择多选",
                        "value": null,
                        "field_type": "member"
                    }
                }
            }
        },
        {
            "id": "4f4d930f374e1c13a8de480442663eef",
            "type": "comments",
            "attributes": {
                "content": "<p>任务的评论</p>",
                "created_at": "2020-12-24T11:56:18.000+08:00",
                "updated_at": "2020-12-24T11:56:18.000+08:00"
            },
            "relationships": {
                "creator": {
                    "data": {
                        "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                        "type": "members"
                    }
                },
                "attachments": {
                    "data": []
                }
            }
        },
        {
            "id": "8359dd2b0f0fd7e42ab411809516574d",
            "type": "todolists",
            "attributes": {
                "name": "清单外任务",
                "is_active": true,
                "is_archived": false,
                "is_default": true
            },
            "relationships": {
                "project": {
                    "data": {
                        "id": "4317c3fec708d73e6be6f0ec2906254c",
                        "type": "projects"
                    }
                }
            }
        },
        {
            "id": "4317c3fec708d73e6be6f0ec2906254c",
            "type": "projects",
            "attributes": {
                "name": "社交媒体内容投放",
                "is_archived": false
            }
        },
        {
            "id": "1370",
            "type": "todos_custom_field_values",
            "attributes": {
                "custom_fields": {
                    "Y4B7RiMh": {
                        "name": "任务估点",
                        "value": "10",
                        "field_type": "number"
                    },
                    "dpuFMjpZ": {
                        "name": "Intercom URL",
                        "value": null,
                        "field_type": "string"
                    },
                    "SkFsCU6t": {
                        "name": "截止日期",
                        "value": null,
                        "field_type": "date"
                    },
                    "member_GrB9U8fJ": {
                        "name": "1维护人",
                        "value": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                        "field_type": "member"
                    },
                    "select_WDvNVBqF": {
                        "name": "性别",
                        "value": "男",
                        "field_type": "select"
                    },
                    "hyperlink_u9zxhyL7": {
                        "name": "链接地址",
                        "value": null,
                        "field_type": "hyperlink"
                    },
                    "string_YyDEkeKe": {
                        "name": "地址",
                        "value": null,
                        "field_type": "string"
                    },
                    "select_C4SJPfKe": {
                        "name": "单选字段",
                        "value": "B",
                        "field_type": "select"
                    },
                    "member_CknmgKqD": {
                        "name": "成员选择多选",
                        "value": [
                            "73d2b1dfd7b5bfa4aa69c1c8da4af2a0"
                        ],
                        "field_type": "member"
                    }
                }
            }
        },
        {
            "id": "76edaceffcf8478251a2ca1536d11763",
            "type": "todos",
            "attributes": {
                "team_wide_id": 5078,
                "content": "二级子任务",
                "desc": null,
                "is_active": true,
                "is_completed": false,
                "priority": "normal",
                "start_at": null,
                "due_at": "2020-12-24T23:59:59.000+08:00",
                "closed_at": null,
                "created_at": "2020-12-24T11:58:10.000+08:00",
                "updated_at": "2020-12-24T11:58:16.000+08:00",
                "labels": []
            },
            "relationships": {
                "project": {
                    "data": {
                        "id": "84b9c4fc92260d19243f357951f57782",
                        "type": "projects"
                    }
                },
                "todolist": {
                    "data": {
                        "id": "a56acdd10c82544673729f6d31bdcf11",
                        "type": "todolists"
                    }
                },
                "creator": {
                    "data": {
                        "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                        "type": "members"
                    }
                },
                "assignee": {
                    "data": {
                        "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                        "type": "members"
                    }
                },
                "closer": {
                    "data": null
                },
                "parent": {
                    "data": {
                        "id": "c1702c95de6498b176636dde3a41ffff",
                        "type": "todos"
                    }
                },
                "custom_field_value": {
                    "data": null
                },
                "sub_todos": {
                    "data": []
                },
                "comments": {
                    "data": []
                },
                "todolists": {
                    "data": []
                },
                "attachments": {
                    "data": []
                }
            }
        },
        {
            "id": "40f30cadf068d2ca424ef1c3b11f4c03",
            "type": "comments",
            "attributes": {
                "content": "<p>任务评论</p><p> </p>",
                "created_at": "2020-12-24T11:59:15.000+08:00",
                "updated_at": "2020-12-24T11:59:15.000+08:00"
            },
            "relationships": {
                "creator": {
                    "data": {
                        "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                        "type": "members"
                    }
                },
                "attachments": {
                    "data": []
                }
            }
        },
        {
            "id": "a6bd7d78ee75f53356edd743139267ca",
            "type": "todolists",
            "attributes": {
                "name": "清单外任务",
                "is_active": true,
                "is_archived": false,
                "is_default": true
            },
            "relationships": {
                "project": {
                    "data": {
                        "id": "207a56dbce35f9dbaad2b8d8d67fb76e",
                        "type": "projects"
                    }
                }
            }
        },
        {
            "id": "207a56dbce35f9dbaad2b8d8d67fb76e",
            "type": "projects",
            "attributes": {
                "name": "敏捷迭代",
                "is_archived": false
            }
        },
        {
            "id": "b6ea561ad149893ae699c4b55935faca",
            "type": "todolists",
            "attributes": {
                "name": "清单外任务",
                "is_active": true,
                "is_archived": false,
                "is_default": true
            },
            "relationships": {
                "project": {
                    "data": {
                        "id": "363712258930d645ee39072f7255bb41",
                        "type": "projects"
                    }
                }
            }
        },
        {
            "id": "363712258930d645ee39072f7255bb41",
            "type": "projects",
            "attributes": {
                "name": "Bug管理",
                "is_archived": false
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 更新任务信息

```
PATCH https://tower.im/api/v1/todos/{todo_id}
```

参数

| 名称                                                                                                | 类型   | 描述                                           |
| --------------------------------------------------------------------------------------------------- | ------ | ---------------------------------------------- |
| `{ "todo": { "content": "Todo", "desc": "Todo Desc", "assignee_id": "", "due_at": "2018-01-09", "start_at": "2018-01-05", "attfile_guids": ["guid1", "guid2", "guid3"] }, "select_C4SJPfKe(示例)": "fcd8170c", "label_ids": [146],  "hyperlink_jzXUYBJ6": [{"name": "aaaa", "link": "tower.im"}] }` | `json` | 任务信息，`assignee_id` 和 `due_at` 可设置为空,  更新自定义字段时需传自定义字段的key, 单选,多选字段的可填值为选项对应的value(可在网页端检查元素里看到). 标签同理，也需要在网页端找到标签对应的value|

```json
Status: 200 OK
// 字段等同于 [获取任务信息]
{
    "data": {
        "id": "305d8cdbb457ab74091d448b94081507",
        "type": "todos",
        "attributes": {
            "team_wide_id": 5079,
            "content": "更新任务标题",
            "desc": null,
            "is_active": true,
            "is_completed": false,
            "priority": "normal",
            "start_at": null,
            "due_at": null,
            "closed_at": null,
            "created_at": "2020-12-24T16:36:05.000+08:00",
            "updated_at": "2020-12-24T16:36:25.000+08:00",
            "labels": []
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "84b9c4fc92260d19243f357951f57782",
                    "type": "projects"
                }
            },
            "todolist": {
                "data": {
                    "id": "22e916a097226715c2d9fab0185191d0",
                    "type": "todolists"
                }
            },
            "creator": {
                "data": {
                    "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
                    "type": "members"
                }
            },
            "assignee": {
                "data": null
            },
            "closer": {
                "data": null
            },
            "parent": {
                "data": null
            },
            "custom_field_value": {
                "data": {
                    "id": "1371",
                    "type": "todos_custom_field_values"
                }
            },
            "sub_todos": {
                "data": []
            },
            "comments": {
                "data": []
            },
            "todolists": {
                "data": [
                    {
                        "id": "22e916a097226715c2d9fab0185191d0",
                        "type": "todolists"
                    }
                ]
            },
            "attachments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "84b9c4fc92260d19243f357951f57782",
            "type": "projects",
            "attributes": {
                "name": "Tower",
                "is_archived": false
            }
        },
        {
            "id": "22e916a097226715c2d9fab0185191d0",
            "type": "todolists",
            "attributes": {
                "name": "清单外任务",
                "is_active": true,
                "is_archived": false,
                "is_default": true
            },
            "relationships": {
                "project": {
                    "data": {
                        "id": "84b9c4fc92260d19243f357951f57782",
                        "type": "projects"
                    }
                }
            }
        },
        {
            "id": "73d2b1dfd7b5bfa4aa69c1c8da4af2a0",
            "type": "members",
            "attributes": {
                "nickname": "本地开发",
                "is_active": true,
                "gavatar": "https://avatar-local.oss-cn-hangzhou.aliyuncs.com/default_avatars/jokul.jpg",
                "role": "owner"
            }
        },
        {
            "id": "1371",
            "type": "todos_custom_field_values",
            "attributes": {
                "custom_fields": {
                    "select_WDvNVBqF": {
                        "name": "性别",
                        "value": null,
                        "field_type": "select"
                    },
                    "hyperlink_u9zxhyL7": {
                        "name": "链接地址",
                        "value": null,
                        "field_type": "hyperlink"
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

## 删除任务

```
DELETE /todos/{todo_id}
```

```
Status: 204 OK
```

## 完成任务

```
POST https://tower.im/api/v1/todos/{todo_id}/completion
```

```json
Status: 200 OK
// 字段等同于 [获取任务信息]
{
    "data": {
        "id": "2388246f04414e1aa286cd1cdb60a5b3",
        "type": "todos",
        "attributes": {
            "team_wide_id": 4116, //资源ID
            "content": "任务名称",
            "desc": "<p>任务描述</p>",
            "is_active": true,
            "is_completed": false,
            "due_at": null,
            "closed_at": null,
            "created_at": "2018-04-16T16:07:54.000+08:00",
            "updated_at": "2018-04-16T16:08:15.000+08:00"
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "5448bef3f013403db51b82d5ba3c473e",
                    "type": "projects"
                }
            },
            "todolist": {
                "data": {
                    "id": "462c6ca5442c4d6394b8bed46480e195",
                    "type": "todolists"
                }
            },
            "creator": {
                "data": {
                    "id": "8ead8fc12a804eb198c2196abbf1a18e",
                    "type": "members"
                }
            },
            "assignee": {
                "data": null
            },
            "closer": {
                "data": null
            },
            "comments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "5448bef3f013403db51b82d5ba3c473e",
            "type": "projects",
            "attributes": {
                "name": "Project Name",
                "is_archived": false
            }
        },
        {
            "id": "462c6ca5442c4d6394b8bed46480e195",
            "type": "todolists",
            "attributes": {
                "name": "清单名称",
                "is_active": true,
                "is_archived": false,
                "is_default": false
            }
        },
        {
            "id": "8ead8fc12a804eb198c2196abbf1a18e",
            "type": "members",
            "attributes": {
                "nickname": "GaoYu",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:07:35.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
                        "type": "teams"
                    }
                },
                "groups": {
                    "data": []
                }
            }
        },
        {
            "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
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

## 打开任务

```
DELETE https://tower.im/api/v1/todos/{todo_id}/completion

使用 HTTP 的 Delete 方法，对已完成任务完成进行删除，表示重新打开任务。
```

```json
Status: 200 OK

{
    "data": {
        "id": "2388246f04414e1aa286cd1cdb60a5b3",
        "type": "todos",
        "attributes": {
            "team_wide_id": 4116, //资源ID
            "content": "任务名称",
            "desc": "<p>任务描述</p>",
            "is_active": true,
            "is_completed": false,
            "due_at": null,
            "closed_at": null,
            "created_at": "2018-04-16T16:07:54.000+08:00",
            "updated_at": "2018-04-16T16:08:15.000+08:00"
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "5448bef3f013403db51b82d5ba3c473e",
                    "type": "projects"
                }
            },
            "todolist": {
                "data": {
                    "id": "462c6ca5442c4d6394b8bed46480e195",
                    "type": "todolists"
                }
            },
            "creator": {
                "data": {
                    "id": "8ead8fc12a804eb198c2196abbf1a18e",
                    "type": "members"
                }
            },
            "assignee": {
                "data": null
            },
            "closer": {
                "data": null
            },
            "todos_check_items": {
                "data": [
                    {
                        "id": "66c2977494fd4dadb3ec8cd3248744bf",
                        "type": "todos_check_items"
                    }
                ]
            },
            "comments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "5448bef3f013403db51b82d5ba3c473e",
            "type": "projects",
            "attributes": {
                "name": "Project Name",
                "is_archived": false
            }
        },
        {
            "id": "462c6ca5442c4d6394b8bed46480e195",
            "type": "todolists",
            "attributes": {
                "name": "清单名称",
                "is_active": true,
                "is_archived": false,
                "is_default": false
            }
        },
        {
            "id": "8ead8fc12a804eb198c2196abbf1a18e",
            "type": "members",
            "attributes": {
                "nickname": "GaoYu",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:07:35.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
                        "type": "teams"
                    }
                },
                "groups": {
                    "data": []
                }
            }
        },
        {
            "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
            "type": "teams",
            "attributes": {
                "name": "API Team",
                "created_at": "2018-04-16T16:07:34.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            }
        },
        {
            "id": "66c2977494fd4dadb3ec8cd3248744bf",
            "type": "todos_check_items",
            "attributes": {
                "name": "检查项",
                "is_completed": false,
                "due_at": null,
                "completed_at": null
            },
            "relationships": {
                "creator": {
                    "data": {
                        "id": "8ead8fc12a804eb198c2196abbf1a18e",
                        "type": "members"
                    }
                },
                "assignee": {
                    "data": null
                },
                "closer": {
                    "data": null
                }
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 发布评论

```
POST https://tower.im/api/v1/todos/{id}/comments
```

参数

| 名称                                                | 类型     | 描述    |
| --------------------------------------------------- | -------- | ------- |
| `id`                                                | `string` | todo id |
| `{"comment": {"content": "comment content"}}` | `json`   | comment |

> 评论中 @ 他人，需要将评论中的`@Tower`转化成`<a href=\"/members/{member_id}\" data-mention=\"true\">@Tower</a>`

```json
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
                "name": "API Team",
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

## 指派任务负责人

```
PATCH https://tower.im/api/v1/todos/{todo_id}/assignment
```

参数

| 名称                                                     | 类型   | 描述      |
| -------------------------------------------------------- | ------ | --------- |
| `{ "todos_assignment": { "assignee_id": "member_id" } }` | `json` | member id |

```json
Status: 200 OK

{
    "data": {
        "id": "2388246f04414e1aa286cd1cdb60a5b3",
        "type": "todos",
        "attributes": {
            "content": "任务名称",
            "desc": "<p>任务描述</p>",
            "is_active": true,
            "is_completed": false,
            "due_at": null,
            "closed_at": null,
            "created_at": "2018-04-16T16:07:54.000+08:00",
            "updated_at": "2018-04-16T16:08:15.000+08:00"
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "5448bef3f013403db51b82d5ba3c473e",
                    "type": "projects"
                }
            },
            "todolist": {
                "data": {
                    "id": "462c6ca5442c4d6394b8bed46480e195",
                    "type": "todolists"
                }
            },
            "creator": {
                "data": {
                    "id": "8ead8fc12a804eb198c2196abbf1a18e",
                    "type": "members"
                }
            },
            "assignee": {
                "data": null
            },
            "closer": {
                "data": null
            },
            "todos_check_items": {
                "data": [
                    {
                        "id": "66c2977494fd4dadb3ec8cd3248744bf",
                        "type": "todos_check_items"
                    }
                ]
            },
            "comments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "5448bef3f013403db51b82d5ba3c473e",
            "type": "projects",
            "attributes": {
                "name": "Project Name",
                "is_archived": false
            }
        },
        {
            "id": "462c6ca5442c4d6394b8bed46480e195",
            "type": "todolists",
            "attributes": {
                "name": "清单名称",
                "is_active": true,
                "is_archived": false,
                "is_default": false
            }
        },
        {
            "id": "8ead8fc12a804eb198c2196abbf1a18e",
            "type": "members",
            "attributes": {
                "nickname": "GaoYu",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:07:35.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
                        "type": "teams"
                    }
                },
                "groups": {
                    "data": []
                }
            }
        },
        {
            "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
            "type": "teams",
            "attributes": {
                "name": "API Team",
                "created_at": "2018-04-16T16:07:34.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            }
        },
        {
            "id": "66c2977494fd4dadb3ec8cd3248744bf",
            "type": "todos_check_items",
            "attributes": {
                "name": "检查项",
                "is_completed": false,
                "due_at": null,
                "completed_at": null
            },
            "relationships": {
                "creator": {
                    "data": {
                        "id": "8ead8fc12a804eb198c2196abbf1a18e",
                        "type": "members"
                    }
                },
                "assignee": {
                    "data": null
                },
                "closer": {
                    "data": null
                }
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 移除任务负责人

```
DELETE https://tower.im/api/v1/todos/{todo_id}/assignment
```

```
Status: 200 OK
```

## 更新任务到期日

```
PATCH https://tower.im/api/v1/todos/{todo_id}/due
```

参数

| 名称                                          | 类型   | 描述           |
| --------------------------------------------- | ------ | -------------- |
| `{ "todos_due": { "due_at": "2018-01-10" } }` | `json` | 不需要设置时区 |

```json
Status: 200 OK

{
    "data": {
        "id": "2388246f04414e1aa286cd1cdb60a5b3",
        "type": "todos",
        "attributes": {
            "team_wide_id": 4116, //资源ID
            "content": "任务名称",
            "desc": "<p>任务描述</p>",
            "is_active": true,
            "is_completed": false,
            "due_at": null,
            "closed_at": null,
            "created_at": "2018-04-16T16:07:54.000+08:00",
            "updated_at": "2018-04-16T16:08:15.000+08:00"
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "5448bef3f013403db51b82d5ba3c473e",
                    "type": "projects"
                }
            },
            "todolist": {
                "data": {
                    "id": "462c6ca5442c4d6394b8bed46480e195",
                    "type": "todolists"
                }
            },
            "creator": {
                "data": {
                    "id": "8ead8fc12a804eb198c2196abbf1a18e",
                    "type": "members"
                }
            },
            "assignee": {
                "data": null
            },
            "closer": {
                "data": null
            },
            "todos_check_items": {
                "data": [
                    {
                        "id": "66c2977494fd4dadb3ec8cd3248744bf",
                        "type": "todos_check_items"
                    }
                ]
            },
            "comments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "5448bef3f013403db51b82d5ba3c473e",
            "type": "projects",
            "attributes": {
                "name": "Project Name",
                "is_archived": false
            }
        },
        {
            "id": "462c6ca5442c4d6394b8bed46480e195",
            "type": "todolists",
            "attributes": {
                "name": "清单名称",
                "is_active": true,
                "is_archived": false,
                "is_default": false
            }
        },
        {
            "id": "8ead8fc12a804eb198c2196abbf1a18e",
            "type": "members",
            "attributes": {
                "nickname": "GaoYu",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:07:35.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
                        "type": "teams"
                    }
                },
                "groups": {
                    "data": []
                }
            }
        },
        {
            "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
            "type": "teams",
            "attributes": {
                "name": "API Team",
                "created_at": "2018-04-16T16:07:34.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            }
        },
        {
            "id": "66c2977494fd4dadb3ec8cd3248744bf",
            "type": "todos_check_items",
            "attributes": {
                "name": "检查项",
                "is_completed": false,
                "due_at": null,
                "completed_at": null
            },
            "relationships": {
                "creator": {
                    "data": {
                        "id": "8ead8fc12a804eb198c2196abbf1a18e",
                        "type": "members"
                    }
                },
                "assignee": {
                    "data": null
                },
                "closer": {
                    "data": null
                }
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 更新任务描述

```
PATCH https://tower.im/api/v1/todos/{todo_id}/desc
```

参数

| 名称                                        | 类型   | 描述 |
| ------------------------------------------- | ------ | ---- |
| `{ "todos_desc": { "desc": "Todo Desc" } }` | `json` |

```json
Status: 200 OK

{
    "data": {
        "id": "2388246f04414e1aa286cd1cdb60a5b3",
        "type": "todos",
        "attributes": {
            "content": "任务名称",
            "desc": "<p>任务描述</p>",
            "is_active": true,
            "is_completed": false,
            "due_at": null,
            "closed_at": null,
            "created_at": "2018-04-16T16:07:54.000+08:00",
            "updated_at": "2018-04-16T16:08:15.000+08:00"
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "5448bef3f013403db51b82d5ba3c473e",
                    "type": "projects"
                }
            },
            "todolist": {
                "data": {
                    "id": "462c6ca5442c4d6394b8bed46480e195",
                    "type": "todolists"
                }
            },
            "creator": {
                "data": {
                    "id": "8ead8fc12a804eb198c2196abbf1a18e",
                    "type": "members"
                }
            },
            "assignee": {
                "data": null
            },
            "closer": {
                "data": null
            },
            "todos_check_items": {
                "data": [
                    {
                        "id": "66c2977494fd4dadb3ec8cd3248744bf",
                        "type": "todos_check_items"
                    }
                ]
            },
            "comments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "5448bef3f013403db51b82d5ba3c473e",
            "type": "projects",
            "attributes": {
                "name": "Project Name",
                "is_archived": false
            }
        },
        {
            "id": "462c6ca5442c4d6394b8bed46480e195",
            "type": "todolists",
            "attributes": {
                "name": "清单名称",
                "is_active": true,
                "is_archived": false,
                "is_default": false
            }
        },
        {
            "id": "8ead8fc12a804eb198c2196abbf1a18e",
            "type": "members",
            "attributes": {
                "nickname": "GaoYu",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:07:35.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
                        "type": "teams"
                    }
                },
                "groups": {
                    "data": []
                }
            }
        },
        {
            "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
            "type": "teams",
            "attributes": {
                "name": "API Team",
                "created_at": "2018-04-16T16:07:34.000+08:00",
                "updated_at": "2018-04-16T16:07:35.000+08:00"
            }
        },
        {
            "id": "66c2977494fd4dadb3ec8cd3248744bf",
            "type": "todos_check_items",
            "attributes": {
                "name": "检查项",
                "is_completed": false,
                "due_at": null,
                "completed_at": null
            },
            "relationships": {
                "creator": {
                    "data": {
                        "id": "8ead8fc12a804eb198c2196abbf1a18e",
                        "type": "members"
                    }
                },
                "assignee": {
                    "data": null
                },
                "closer": {
                    "data": null
                }
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```
