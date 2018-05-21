# 任务清单

## 获取项目中所有任务清单

```
GET /projects/{project_id}/todolists
```

```json
Status: 200 OK

{
    "data": [
        {
            "id": "2d1fbfd51ed7429296bc1a5fcb",
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
                            "id": "fb31376b01894058b2a434813ffd",
                            "type": "todos"
                        }
                    ]
                }
            }
        },
        {
            "id": "862ed55e1564487f85dc1343ca45",
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
    "included": [
        {
            "id": "fb31376b01894058b2a434813ffda",
            "type": "todos",
            "attributes": {
                "content": "任务",
                "desc": "",
                "is_active": true,
                "is_completed": false,
                "due_at": null,
                "closed_at": null
            },
            "relationships": {
                "creator": {
                    "data": {
                        "id": "8ead8fc12a804eb198c2196abbf1a",
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
            "id": "8ead8fc12a804eb198c2196abbf1a1",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
                "role": "owner",
                "comment": null,
                "phone": null,
                "created_at": "2018-04-16T16:07:35.000+08:00",
                "updated_at": "2018-04-16T16:09:27.000+08:00"
            },
            "relationships": {
                "team": {
                    "data": {
                        "id": "3fbe491eef5c4fbeaaabc1716b7a1",
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

## 创建任务清单

```
POST /projects/{project_id}/todolists
```

参数

| 名称                                                              | 类型   | 描述          |
| ----------------------------------------------------------------- | ------ | ------------- |
| `{ "todolist": { "name": "Todolist", "desc": "Todolist Desc" } }` | `json` | todolist info |

```json
Status: 200 OK

{
    "data": {
        "id": "da8aef40e9c04feb8e289529aa23b63e",
        "type": "todolists",
        "attributes": {
            "name": "Todolist",
            "desc": "Todolist Desc",
            "is_active": true,
            "is_archived": false,
            "is_default": false,
            "completed_at": null,
            "created_at": "2018-04-16T17:10:38.000+08:00",
            "updated_at": "2018-04-16T17:10:38.000+08:00"
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "fd746ae1145c46398973b61876a3f0a6",
                    "type": "projects"
                }
            },
            "creator": {
                "data": {
                    "id": "8ead8fc12a804eb198c2196abbf1a18e",
                    "type": "members"
                }
            },
            "archiver": {
                "data": null
            },
            "todos": {
                "data": []
            },
            "comments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "fd746ae1145c46398973b61876a3f0a6",
            "type": "projects",
            "attributes": {
                "name": "Project Name",
                "is_archived": false
            }
        },
        {
            "id": "8ead8fc12a804eb198c2196abbf1a18e",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
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

## 获取任务清单信息

```
GET /todolists/{id}
```

```json
Status: 200 OK

{
    "data": {
        "id": "da8aef40e9c04feb8e289529aa23b63e",
        "type": "todolists",
        "attributes": {
            "name": "Todolist",
            "desc": "Todolist Desc",
            "is_active": true,
            "is_archived": false,
            "is_default": false,
            "completed_at": null,
            "created_at": "2018-04-16T17:10:38.000+08:00",
            "updated_at": "2018-04-16T17:10:38.000+08:00"
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "fd746ae1145c46398973b61876a3f0a6",
                    "type": "projects"
                }
            },
            "creator": {
                "data": {
                    "id": "8ead8fc12a804eb198c2196abbf1a18e",
                    "type": "members"
                }
            },
            "archiver": {
                "data": null
            },
            "todos": {
                "data": []
            },
            "comments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "fd746ae1145c46398973b61876a3f0a6",
            "type": "projects",
            "attributes": {
                "name": "Project Name",
                "is_archived": false
            }
        },
        {
            "id": "8ead8fc12a804eb198c2196abbf1a18e",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
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

## 更新任务列表

```
PATCH /todolists/{id}
```

参数

| 名称                                                              | 类型   | 描述          |
| ----------------------------------------------------------------- | ------ | ------------- |
| `{ "todolist": { "name": "Todolist", "desc": "Todolist Desc" } }` | `json` | todolist info |

```
Status: 200 OK

{
    "data": {
        "id": "da8aef40e9c04feb8e289529aa23b63e",
        "type": "todolists",
        "attributes": {
            "name": "Todolist",
            "desc": "Todolist Desc",
            "is_active": true,
            "is_archived": false,
            "is_default": false,
            "completed_at": null,
            "created_at": "2018-04-16T17:10:38.000+08:00",
            "updated_at": "2018-04-16T17:10:38.000+08:00"
        },
        "relationships": {
            "project": {
                "data": {
                    "id": "fd746ae1145c46398973b61876a3f0a6",
                    "type": "projects"
                }
            },
            "creator": {
                "data": {
                    "id": "8ead8fc12a804eb198c2196abbf1a18e",
                    "type": "members"
                }
            },
            "archiver": {
                "data": null
            },
            "todos": {
                "data": []
            },
            "comments": {
                "data": []
            }
        }
    },
    "included": [
        {
            "id": "fd746ae1145c46398973b61876a3f0a6",
            "type": "projects",
            "attributes": {
                "name": "Project Name",
                "is_archived": false
            }
        },
        {
            "id": "8ead8fc12a804eb198c2196abbf1a18e",
            "type": "members",
            "attributes": {
                "nickname": "nickname",
                "is_active": true,
                "gavatar": "https://avatar.tower.im/",
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

## 删除任务清单

```
DELETE /todolists/{id}
```

```
Status: 204 OK
```
