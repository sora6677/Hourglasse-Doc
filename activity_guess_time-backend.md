# activity_guess_time-backend 猜時間活動後台

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|傳入資料異常|
|1002|資料庫異常|
|1003|登入令牌驗證失效|
|1004|無此權限|
|1005|建立失敗|

## ManagerLogin - 管理員登入
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  ManagerAccount(string)：管理員帳號
  ManagerPassword(string)：管理員密碼
傳入範例：
  data={"ManagerAccount":"chat_user","ManagerPassword":"123456"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    ManagerId(string)：管理員ID
    AuthToken(string)：管理員令牌
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"ManagerId":"10000","AuthToken":"1bab341c06ca0d432e3d37adc892a4a1","ManagerType":0}}
失敗範例：
  {"status":1102,"msg":"無此帳號","data":{}}
  {"status":1103,"msg":"密碼錯誤","data":{}}
```

## ManagerLogout - 管理員登出
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
MetHod：GET
傳入參數：
傳入JSON：
傳入範例：
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
  {"status":1001,"msg":"傳入資料異常","data":{}}
```
