# StartLuo-frontend 沙漏活動前台

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|連線異常|

## UserUpdateLoginData - 玩家更新登入資料
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserData(object)：API收到的整包玩家登入資料
  UserBalanceData(object)：API收到的整包玩家票券資料
傳入範例：
  data={"UserData":{"accountID":"00000019","nickName":"Daisy00001"......},"UserBalanceData":[{"balance":"0","currencyType":"gold"},{"balance":"0","currencyType":"gem"......}]}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    LoginToken(string)：登入令牌
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  共用錯誤代碼或
  {"status":1101,"msg":"登入失敗","data":{}}
```

## GetUserBetList - 玩家競猜注單列表
```
Header：
  UserAccount(string)：玩家 (唯一碼)
  CheckToken(string)：身分驗證令牌
```

```
MetHod：GET
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  共用錯誤代碼或
  {"status":1101,"msg":"登入失敗","data":{}}
```

## CreateUserBet - 建立玩家競猜注單
```
Header：
  UserAccount(string)：玩家 (唯一碼)
  CheckToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  QuizDateTime(string)：競猜時間
傳入範例：
  data={"QuizDateTime":"2022-12-30 13:02:01"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  共用錯誤代碼或
  {"status":1101,"msg":"登入失敗","data":{}}
```

## UpdateUserBet - 修改玩家競猜注單
```
Header：
  UserAccount(string)：玩家 (唯一碼)
  CheckToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  BetId(string)：注單ID
  QuizDateTime(string)：競猜時間
傳入範例：
  data={"QuizDateTime":"2022-12-30 13:02:01"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  共用錯誤代碼或
  {"status":1101,"msg":"登入失敗","data":{}}
```
