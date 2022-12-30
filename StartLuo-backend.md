# StartLuo-backend.md 活動後台

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|資料異常|
|1002|連線異常|
|1003|令牌失效|
|1004|更新失敗|


## ManagerLogin - 管理員登入
```
URL：api/manager/ManagerLogin.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  ManagerAccount(string)：管理員帳號
  ManagerPassword(string)：管理員密碼
傳入範例：
  data={"ManagerAccount":"xxx","ManagerPassword":"xxx"}
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
URL：api/manager/ManagerLogout.php
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
  參考共用錯誤代碼
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

## SetPageContent - 寫入頁面訊息
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：api/startpage/SetPageContent.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  pageType(int)：頁面類型代碼 **參考 各頁面類型對應
  pageContent(string)：頁面內容
傳入範例：
  data={"pageType":101,"pageContent":{......}}
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
  {"status":1103,"msg":"查無此頁面","data":{}}
```

## GetPageContent - 取得頁面訊息
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：api/startpage/GetPageContent.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  pageType(int)：頁面類型代碼 **參考 各頁面類型對應
傳入範例：
  data={"pageType":101}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    content(object)：頁面內容
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"content":{......}}}
失敗範例：
  {"status":1103,"msg":"查無此頁面","data":{}}
```

## StartLuoList - 沙漏期數列表
```
**目前僅列當期
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：
MetHod：GET
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object array)：
    PeriodId(int)：期數ID
    StartDateTime(string)：活動開始時間
    EndDateTime(string)：活動結束時間
    BetEndDateTime(string)：下注結束時間
    HourClassStartDateTime(string)：沙漏開始時間
    HourClassEndDateTime(string)：沙漏結束時間
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":[{"PeriodId":1,"StartDateTime":"2022-12-18 00:00:00","EndDateTime":"2022-12-24 17:59:59","BetEndDateTime":"2022-12-24 12:00:00","HourClassStartDateTime":"2022-12-18 00:00:00","HourClassEndDateTime":"2022-12-24 17:59:59"}]}
失敗範例：
  參考共用錯誤代碼
```

## StartLuoStart - 活動開始
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  PeriodId(int)：期數ID
  StartDateTime(string)：開始時間 格式:yyyy-mm-dd HH:ii:ss (24 小時制)
傳入範例：
  data={"PeriodId":1,"StartDateTime":"2022-12-30 13:00:00"}
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
  參考共用錯誤代碼
```

## HourglassStart - 開始沙漏
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  PeriodId(int)：期數ID
  StartDateTime(string)：開始時間 格式:yyyy-mm-dd HH:ii:ss (24 小時制)
傳入範例：
  data={"PeriodId":1,"StartDateTime":"2022-12-30 16:00:00"}
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
  參考共用錯誤代碼
```

## HourglassEnd - 沙漏結束
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  PeriodId(int)：期數ID
  EndDateTime(string)：結束時間 格式:yyyy-mm-dd HH:ii:ss (24 小時制)
傳入範例：
  data={"PeriodId":1,"EndDateTime":"2022-12-30 16:00:00"}
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
  參考共用錯誤代碼
```

## BetStop - 停止下注
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  PeriodId(int)：期數ID
  StopDateTime(string)：下注停止時間 格式:yyyy-mm-dd HH:ii:ss (24 小時制)
傳入範例：
  data={"PeriodId":1,"StopDateTime":"2022-12-30 16:00:00"}
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
  參考共用錯誤代碼
```
