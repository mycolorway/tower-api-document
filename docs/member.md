# Member API

## Get team members

```
GET /teams/{team_id}/members
```

```
Status: 200 OK
```

## Get current user member info in team

```
GET /teams/{team_id}/member
```

```
Status: 200 OK
```

## Get member info

```
GET /member/{member_id}
```

```
Status: 200 OK
```

## Get assigned uncompleted todos

```
GET /members/{member_id}/assigned_uncompleted_todos	
```
> box 为分类属性，不要使用到期日作为分类。
> `0`代表新任务，`1`代表今天，`2`代表接下来

```
Status: 200 OK
```

## Get assigned completed todos

```
GET /members/{member_id}/assigned_completed_todos	
```

Parameters

Name|Type|Description|
--|--|--|
`{ page: { number: 1 } }`|URLEncoding| page 从 1 开始计数

```
Status: 200 OK
```

## Get created_uncompleted_todos

```
GET /members/{member_id}/created_uncompleted_todos	
```

```
Status: 200 OK
```

## Get created completed todos

```
GET /members/{member_id}/created_completed_todos	
```

Parameters

Name|Type|Description|
--|--|--|
`{ page: { number: 1 } }`|URLEncoding| page 从 1 开始计数

```
Status: 200 OK
```

