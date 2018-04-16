# Project API

## Get projects

```
GET /teams/{team_id}/projects	
```

>all published normal projects

```
Status: 200 OK
```

## Create project

```
POST /teams/{team_id}/projects
```

Parameters

Name|Type|Description|
--|--|--|
`{ project: { name: 'Project', desc: 'Project Desc', member_ids: [] } }`|`json`| project info

```
Status: 200 OK
```

## Get project

```
GET /projects/{id	}
```

```
Status: 200 OK
```

## Update project

```
PATCH	/projects/{id}	
```

Parameters

Name|Type|Description|
--|--|--|
`{ project: { name: 'Project', desc: 'Project desc', member_ids: [] } }`|`json`| project info

```
Status: 200 OK
```

## Delete project

```
DELETE /projects/{id}
```

```
Status: 200 OK
```

## Get project member

```
GET /projects/{project_id}/members
```

```
Status: 200 OK
```


