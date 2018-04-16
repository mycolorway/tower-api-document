# Team API

## Get Team

```
GET /teams
```

```
Status: 200 OK
```

## Create Team 

```
POST /teams
```

Parameters

Name|Type|Description|
--|--|--|
`{ team: { name: 'Tower Team' } }`|`json`| team name

```
Status: 200 OK
```

## Update Team 

```
PATCH /teams/{id}
```

Parameters

Name|Type|Description|
--|--|--|
`{ team: { name: 'Tower Team' } }`|`json`| team name

```
Status: 200 OK
```

