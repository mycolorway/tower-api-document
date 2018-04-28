# 项目

## 获取团队中所有项目

```
GET /teams/{team_id}/projects
```

```json
Status: 200 OK

{
    "data": [
        {
            "id": "974de405781644e09e187109bb0386de",
            "type": "projects",
            "attributes": {
                "name": "熟悉 Tower",
                "desc": "工欲善其事，必先利其器。",
                "is_pinned": false,
                "is_archived": false
            },
            "relationships": {
                "project_groups": {
                    "data": []
                }
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 创建项目

```
POST /teams/{team_id}/projects
```

参数

| 名称                                                                             | 类型   | 描述     |
| -------------------------------------------------------------------------------- | ------ | -------- |
| `{ "project": { "name": "Project", "desc": "Project Desc", "member_ids": [] } }` | `json` | 项目信息 |

```json
Status: 200 OK

{
    "data": {
        "id": "fa9413082dc0456ab98576d2e882",
        "type": "projects",
        "attributes": {
            "name": "Project",
            "desc": "Project Desc",
            "is_archived": false,
            "created_at": "2018-04-16T16:49:27.000+08:00",
            "updated_at": "2018-04-16T16:49:27.000+08:00"
        },
        "relationships": {
            "team": {
                "data": {
                    "id": "1f9118b07cf1485ba4b97a4cbc5",
                    "type": "teams"
                }
            },
            "creator": {
                "data": {
                    "id": "c979895c5a754c35b3e98f1c726",
                    "type": "members"
                }
            },
            "todolists": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "1f9118b07cf1485ba4b97a4cbc50",
            "type": "teams",
            "attributes": {
                "name": "Tower Team123",
                "created_at": "2018-04-16T16:35:29.000+08:00",
                "updated_at": "2018-04-16T16:36:56.000+08:00"
            }
        },
        {
            "id": "c979895c5a754c35b3e98f1c7268",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:35:29.000+08:00",
                "updated_at": "2018-04-16T16:36:50.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "1f9118b07cf1485ba4b97a4cbc50bba8",
                        "type": "teams"
                    }
                },
                "groups": {
                    "data": []
                }
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 获取项目信息

```
GET /projects/{project_id}
```

```json
Status: 200 OK

{
    "data": {
        "id": "5448bef3f013403db51b82d5ba3c473e",
        "type": "projects",
        "attributes": {
            "name": "Project Name",
            "desc": "Project desc",
            "is_archived": false,
            "created_at": "2018-04-16T16:07:48.000+08:00",
            "updated_at": "2018-04-16T16:26:12.000+08:00"
        },
        "relationships": {
            "team": {
                "data": {
                    "id": "3fbe491eef5c4fbeaaabc1716b7a1f00",
                    "type": "teams"
                }
            },
            "creator": {
                "data": {
                    "id": "8ead8fc12a804eb198c2196abbf1a18e",
                    "type": "members"
                }
            },
            "todolists": {
                "data": [
                    {
                        "id": "462c6ca5442c4d6394b8bed46480e195",
                        "type": "todolists"
                    },
                    {
                        "id": "382dbd2306194d9380e3f96221b26720",
                        "type": "todolists"
                    }
                ]
            }
        }
    },
    "included": [
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
            "id": "8ead8fc12a804eb198c2196abbf1a18e",
            "type": "members",
            "attributes": {
                "nickname": "GaoYu",
                "is_active": true,
                "gavatar": "https://avatar.tower.im",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:07:35.000+08:00",
                "updated_at": "2018-04-16T16:09:27.000+08:00"
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
            "id": "462c6ca5442c4d6394b8bed46480e195",
            "type": "todolists",
            "attributes": {
                "name": "清单名称",
                "desc": "",
                "is_active": true,
                "is_archived": false,
                "is_default": false,
                "position": 1
            },
            "relationships": {
                "todos": {
                    "data": [
                        {
                            "id": "2388246f04414e1aa286cd1cdb60a5b3",
                            "type": "todos"
                        }
                    ]
                }
            }
        },
        {
            "id": "2388246f04414e1aa286cd1cdb60a5b3",
            "type": "todos",
            "attributes": {
                "content": "任务名称",
                "desc": "<p>任务描述</p>",
                "is_active": true,
                "is_completed": false,
                "due_at": null,
                "closed_at": "2018-04-16T16:17:50.000+08:00"
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
            "id": "382dbd2306194d9380e3f96221b26720",
            "type": "todolists",
            "attributes": {
                "name": "清单外任务",
                "desc": null,
                "is_active": true,
                "is_archived": false,
                "is_default": true,
                "position": 0
            },
            "relationships": {
                "todos": {
                    "data": []
                }
            }
        }
    ],
    "jsonapi": {
        "version": "1.0"
    }
}
```

## 更新项目信息

```
PATCH	/projects/{id}
```

参数

名称|类型|描述|

--|--|--|
`{ project: { name: 'Project', desc: 'Project desc', member_ids: [] } }`|`json`| project info

```
Status: 200 OK
```

## 删除项目

```
DELETE /projects/{id}
```

```
Status: 204 OK
```

## 获取项目成员

```
GET /projects/{project_id}/members
```

```
Status: 200 OK

{
    "data": [
        {
            "id": "8ead8fc12a804eb198c2196abbf",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:07:35.000+08:00",
                "updated_at": "2018-04-16T16:09:27.000+08:00"
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
        }
    ],
    "included": [
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
