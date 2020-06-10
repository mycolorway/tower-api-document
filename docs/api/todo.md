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
                "closed_at": null
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

## 创建任务

```
POST https://tower.im/api/v1/todolists/{todolist_id}/todos
```

参数

| 名称                                                                                                | 类型   | 描述                                           |
| --------------------------------------------------------------------------------------------------- | ------ | ---------------------------------------------- |
| `{ "todo": { "content": "Todo", "desc": "Todo Desc", "assignee_id": "", "due_at": "2018-01-09" } }` | `json` | 任务信息，`assignee_id` 和 `due_at` 可设置为空 |

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
            "custom_field_value": {
                "data": {
                    "id": "2",
                    "type": "todos_custom_field_values"
                }
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
        },
        {
            "id": "2",
            "type": "todos_custom_field_values",
            "attributes": {
                "custom_fields": {
                    "number_Y4B7RiMh": {
                        "name": "任务估点",
                        "value": "8",
                        "field_type": "number"
                    },
                    "multi_select_QeTbTNAR": {
                        "name": "所属平台",
                        "value": [
                            "微信",
                            "安卓",
                            "企业微信"
                        ],
                        "field_type": "multi_select"
                    },
                    "date_SkFsCU6t": {
                        "name": "截止日期",
                        "value": "2019-07-25",
                        "field_type": "date"
                    },
                    "string_i5timka4": {
                        "name": "备注",
                        "value": "备注信息",
                        "field_type": "string"
                    },
                    "member_GrB9U8fJ": {
                        "name": "维护人",
                        "value": "2a4b425e1f0d663668ce19b94ed3688d",
                        "field_type": "member"
                    },
                    "select_WDvNVBqF": {
                        "name": "性别",
                        "value": "男",
                        "field_type": "select"
                    },
                    "boolean_ZFxG2S6U": {
                        "name": "是否停用",
                        "value": "true",
                        "field_type": "boolean"
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

## 更新任务信息

```
PATCH https://tower.im/api/v1/todos/{todo_id}
```

参数

| 名称                                                                                                | 类型   | 描述                                           |
| --------------------------------------------------------------------------------------------------- | ------ | ---------------------------------------------- |
| `{ "todo": { "content": "Todo", "desc": "Todo Desc", "assignee_id": "", "due_at": "2018-01-09" } }` | `json` | 任务信息，`assignee_id` 和 `due_at` 可设置为空 |

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
