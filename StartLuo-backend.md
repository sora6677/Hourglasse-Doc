# StartLuo-backend.md 活動後台

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|資料異常|
|1002|連線異常|
|1003|令牌失效|
|1004|無此權限|

## ManagerLogin - 管理員登入
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  ManagerAccount(string)：管理員帳號
  ManagerPassword(string)：管理員密碼
傳入範例：
  data={"ManagerAccount":"test123","ManagerPassword":"test123"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    ManagerId(string)：管理員ID
    ManagerToken(string)：管理員令牌
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"ManagerId":"1","AuthToken":"1bab341c06ca0d432e3d37adc892a4a1"}}
失敗範例：
  {"status":1101,"msg":"登入失敗","data":{}}
  {"status":1102,"msg":"密碼錯誤","data":{}}
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
## 頁面說明
### 各頁面類型對應
|類型代碼|說明|
|---|---|
|101|官網主頁|
|102|發財開始囉|
|103|賺錢開始鑼|
|104|最新活動|
|105|音樂祭活動|
|106|沙漏活動|
|107|皂飛車活動|
|108|品牌與名人|
|109|服務條款|

### 頁面內容參考
[StartLuo 頁面內容文件](https://github.com/kd20220905/StartLuo_back/blob/main/back.md#startluo)

## SetPageContent - 寫入前台頁面訊息
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  pageType(int)：頁面類型代碼 **參考 各頁面類型對應
  pageContent(string)：頁面內容
傳入範例：
  data={"pageType":101,"pageContent":{""}}
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
