## 錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|傳入資料異常|
|1002|資料庫異常|
|1003|登入令牌驗證失效|
|1004|無此權限|
|1005|建立失敗|
|1101|帳號重複|
|1102|無此帳號|
|1103|密碼錯誤|
|1104|查無此ID|
|1105|查無指定聊天室|
|1106|聊天室人數已滿|

## UserRegister - 註冊
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserAccount(string)：玩家帳號 **限制 12 碼以內
  UserNick(string)：玩家暱稱 **限制 12 碼以內
  UserPassword(string)：玩家密碼 **限制 12 碼以內
傳入範例：
  data={"UserAccount":"testUser02","UserNick":"userNick02","UserPassword":"test123"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    AuthToken(string)：登入驗證令牌
    UserId(int)：玩家ID
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"AuthToken":"552bffdb5c5ea4045d88e71c7b8f2b1d","UserId":47988}}
失敗範例：
  {"status":1005,"msg":"建立失敗","data":{}}
  {"status":1101,"msg":"帳號重複","data":{}}
  {"status":1105,"msg":"查無指定聊天室","data":{}}
  {"status":1106,"msg":"聊天室人數已滿","data":{}}
```

## UserLogin - 登入
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserAccount(string)：玩家帳號
  UserPassword(string)：玩家密碼
傳入範例：
  data={"UserAccount":"testUser02","UserPassword":"test123"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    AuthToken(string)：登入驗證令牌
    UserId(int)：玩家ID
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"AuthToken":"79df2a0420d9add88bf3401360104682","UserId":47988}}
失敗範例：
  {"status":1102,"msg":"無此帳號","data":{}}
  {"status":1103,"msg":"密碼錯誤","data":{}}
```
