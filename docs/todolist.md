# Todolist API

## Get project all todolist

```
GET /projects/{project_id}/todolist
```

>all active unarchived todolists

```
Status: 200 OK
```

## Create todolist

```
POST /projects/{project_id}/todolists
```

Parameters

Name|Type|Description|
--|--|--|
`{ todolist: { name: 'Todolist', desc: 'Todolist Desc' } }`|`json`| todolist info

```
Status: 200 OK
```

## Get todolist

```
GET /todolists/{id}
```

```
Status: 200 OK
```

## Update todolist

```
PATCH /todolists/{id}
```

Parameters

Name|Type|Description|
--|--|--|
`{ todolist: { name: 'Todolist', desc: 'Todolist Desc' } }`|`json`| todolist info

```
Status: 200 OK
```

## Delete todolist

```
DELETE /todolists/{id}
```

```
Status: 200 OK
```


