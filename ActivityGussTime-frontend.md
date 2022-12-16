## 錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|傳入資料異常|
|1002|資料庫異常|

## GetUserBetD - 取得下注資料
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserId(string)：玩家ID
傳入範例：
  data={"UserId":"testUser02"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    BetDate(string)：競猜時間
    CreateDate(string)：下注時間
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"BetDate":"2022-12-14 12:00:00","CreateDate":"2022-12-14 10:00:00"}}
失敗範例：
  {"status":1101,"msg":"無下注資料","data":{}}
```


## UserPlaceBet - 下注
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserId(string)：玩家ID
  BetDate(string)：競猜時間
傳入範例：
  data={"UserId":"xxx","BetDate":"2022-12-14 10:00:00"}
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
  {"status":1102,"msg":"下注失敗","data":{}}
```

## UserRevisePlaceBet - 修改下注
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserId(string)：玩家ID
  BetDate(string)：競猜時間
傳入範例：
  data={"UserId":"xxx","BetDate":"2022-12-14 10:00:00"}
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
  {"status":1102,"msg":"下注失敗","data":{}}
```
