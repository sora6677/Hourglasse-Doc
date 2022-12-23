# StartLuo-frontend 沙漏活動前台

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|

## UserUpdateLoginData - 玩家更新登入資料
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserAccountId(string)：玩家的 accountID
  UserData(object)：API收到的整包玩家登入資料
傳入範例：
  data={"UserData":"{API收到的整包玩家登入資料}"}
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
  {"status":1101,"msg":"登入失敗","data":{}}
```
