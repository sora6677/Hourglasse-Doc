# StartLuoPage-frontend-Doc 開始囉頁面前抬

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|連線異常|

### 頁面內容參考
[StartLuo 頁面內容文件](https://github.com/kd20220905/StartLuo_back/blob/main/back.md#startluo)

## GetPageIndex - 取首頁
```
MetHod：GET
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    pageContent(string)：頁面內容
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"content":{......}}}
失敗範例：
  共用錯誤代碼
```
