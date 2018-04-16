<center><img src="media/TowerLogo.png"></center>
<br>
<br>
# 文档说明

Tower API 是提供给 [Tower Pro](https://tower.im/pro) 用户的一项专属服务，您可以通过 API 在其他平台上创建、更改或删除相关信息，便于集成 [Tower](https://tower.im) 到您的系统中。

Tower API 部署在 [GitHub Page](https://github.com/mycolorway/tower-api-document) 上，对于文中出现的错误我们非常欢迎您进行反馈，您可以创建 issue 或 pull request 进行更正。

## 起步

Tower API 的网址为:

```
https://tower.im/api/v1
``` 
>授权地址在下方示例中

API 使用 OAuth2.0 进行认证，`Access Token` 是全局唯一接口调用凭据，开发者调用各接口时都需使用 `Access Token`，请妥善保存。`Access Token` 的有效期目前为2个小时，需定时刷新，重复获取将导致上次获取的 `Access Token` 失效。

您在获取后，将 `Access Token` 添加到 API 的 Headers 中，从而确保能够获得正确的数据。

更多关于 OAuth2.0 的信息可以在[这里](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html)查看和了解。

## OAuth 示例

### 生成 Access Token

>请注意，OAuth 授权地址为
>https://tower.im

```
POST https://tower.im/oauth/token
```

Parameters

名称|类型|描述|
--|--|--|
`client_id`|`string`| 由 Pro 用户在应用中心中创建
`client_secret`|`string`| 由 Pro 用户在应用中心中创建
`username`|`string`| 用户账号
`password`|`string`| 用户密码
`grant_type`|`string`| 此处填写为`password`
`captcha`|`string`| *可选项*若开启两步验证，此处填写验证码。使用这个 API 完成第一次请求后，会自动通过微信发送验证码，第二次请求时候，将验证码填入此参数即可


```json
未开启两步验证

Status: 200 OK

{
    "access_token": "d4e949df783404f22e882430158f3b0440b608709d833f9b981e9a96b850f05c",
    "token_type": "bearer",
    "expires_in": 7199,
    "refresh_token": "c426d5ab6a211310df088c77b36b38592f6752d5238f291b79174d93f7dc2ed5",
    "created_at": 1523420694,
    "email": "tower@tower.im"
}
```

```json
开启两步验证，此时会收到验证码

Status： 401

{
    "error": "otp_required",
    "error_description": "The authorization server encountered an unexpected condition which prevented it from fulfilling the request."
}
```

### 刷新 Access Token

每一个 Token 默认在 2 小时后到期，此时需要用户进行刷新，同时您也需要注意 API 返回的 `expires_in` 数据，确保代码对过期时间改变后能够自动做出应对。

```
POST https://tower.im/oauth/token
```

Headers

名称|类型|描述|
--|--|--|
`Authorization`|`string`| 此处应该填写为`Bearer access_token`


Parameters

名称|类型|描述|
--|--|--|
`refresh_token`|`string`| refresh token
`grant_type`|`string`| 此处应该填写为`refresh_token`

```json
Status: 200 OK

{
    "access_token": "d4e949df783404f22e882430158f3b0440b608709d833f9b981e9a96b850f05c",
    "token_type": "bearer",
    "expires_in": 7199,
    "refresh_token": "c426d5ab6a211310df088c77b36b38592f6752d5238f291b79174d93f7dc2ed5",
    "created_at": 1523420694,
    "email": "tower@tower.im"
}
```


## API 示例

获取当前用户在团队中的信息

```
GET https://tower.im/api/v1/teams/{team_id}/member
```

Headers

名称|类型|描述|
--|--|--|
`Authorization`|`string`| 此处应该填写为`Bearer access_token`




