# 说明

* 所有 HTTP 请求响应均为 JSON，UTF-8 编码，需指定 header：

    ```Content-type:application/json
    Accept:application/json```

* 请求示例：

    成功示例：
    ```javascript
    {"errcode": 0, "errmsg": "OK"}
    ```

    失败示例：
    ```javascript
    {"errcode": 123, "errmsg": "该邮件地址已经被使用，你已经注册？"}```

    附带数据的示例：
    ```javascript
    {"errcode": 0, "errmsg": "OK", "data": [{"task1", ...}, {"task2", ...}]}```

* 获取用户信息的 API 都需要登陆并且有权限（用户在该组织）访问，否则会返回错误：

    ```javascript
    {"errcode": 3, "errmsg": "you need sign in"}```

    ```javascript
    {"errcode": 4, "errmsg": "permission denied"}```

    后面示例不一一说明

* 以下示例省略请求前缀：https://api.starfish.im/v1

# 用户
## 创建用户

### 参数：

```javascript
{"phone": "1234", "password": "foobar12345", "name": "your-name", "token": "xxx", "gender": 1}```

#### 说明：

* 如果用 email 注册，则 "phone": "1234" 改为 "email": "xx@xx"

* token 是Email/手机号通过验证得到的验证码，获取 token 的方法见：创建 Token。

### 返回：

```javascript
{
  "data": {
    "name": "alice",
    "email": "alice@gmail.com",
    "phone": "123",
    "avatar": "http://zhanweitu.com/100/100/avatar",
    "id": 1
  },
  "errcode": 0,
  "errmsg": "OK"
}
```

注：该 API 可以上传一个头像文件，此时不能用 JSON 编码，Content-Type 必须是multipart/form-data，如果不上传头像，Content-Type 必须是 application/json。

## 获取用户详情
## 检索用户
## 更新用户信息
