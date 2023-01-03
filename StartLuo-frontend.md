# StartLuo-frontend 沙漏活動前台

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|資料異常|
|1002|連線異常|
|1003|令牌失效|

## UserUpdateLoginData - 玩家更新登入資料
```
URL：api/UserUpdateLoginData.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserData(object)：API收到的整包玩家登入資料 **必填資料為 memberID、nickName
  UserBalanceData(object)：API收到的整包玩家票券資料 **若無資料請填空值
傳入範例：
  data={"UserData":{"memberID":"xxxxxxx@startluoagent.startluo","nickName":"Daisy00001"......},"UserBalanceData":[{"balance":"0","currencyType":"gold"},{"balance":"0","currencyType":"gem"......}]}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    AuthToken(string)：登入驗證令牌
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"AuthToken":"2ed6ae6a01a532e10211a45d356508b8"}}
失敗範例：
  共用錯誤代碼或
  {"status":1101,"msg":"登入失敗","data":{}}
```
***
