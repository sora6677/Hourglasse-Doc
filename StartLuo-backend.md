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

***
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

***
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

***
## StartLuoList - 沙漏期數列表
```
**目前僅列當期
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：api/startluo/StartLuoList.php
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
    HourClassEndTime(string)：沙漏結束時間
    CtrlMethod(int)：控制方式 0:自動 1:後台手動
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":[{"PeriodId":1,"StartDateTime":"2023-01-03 00:00:00","EndDateTime":"2023-01-06 00:00:00","BetEndDateTime":"2023-01-05 00:00:00","HourClassEndTime":"15:36:00","CtrlMethod":0}]}
失敗範例：
  參考共用錯誤代碼
```

## SwitchCtrlMethod - 切換控制方式
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：api/startluo/SwitchCtrlMethod.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  PeriodId(int)：期數ID
  CtrlMethod(int)：控制方式 0:自動 1:後台手動
傳入範例：
  data={"PeriodId":1,"CtrlMethod":1}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object Array)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  參考共用錯誤代碼
```

## StartLuoStart - 活動開始
```
*** 當 (CtrlMethod)控制方式 = 後台手動時呼叫才會成功
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：api/startluo/StartLuoStart.php
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
  參考共用錯誤代碼 或
  {"status":1104,"msg":"期數資料異常","data":{}}
  {"status":1105,"msg":"期數控制方式非手動","data":{}}
```

## StartLuoEnd - 活動結束
```
*** 當 (CtrlMethod)控制方式 = 後台手動時呼叫才會成功
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：api/startluo/StartLuoEnd.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  PeriodId(int)：期數ID
  EndDateTime(string)：開始時間 格式:yyyy-mm-dd HH:ii:ss (24 小時制)
傳入範例：
  data={"PeriodId":1,"EndDateTime":"2022-12-30 13:00:00"}
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
  參考共用錯誤代碼 或
  {"status":1104,"msg":"期數資料異常","data":{}}
  {"status":1105,"msg":"期數控制方式非手動","data":{}}
```

## BetStop - 停止下注
```
*** 當 (CtrlMethod)控制方式 = 後台手動時呼叫才會成功
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：api/startluo/BetStop.php
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

## HourglassEnd - 沙漏結束
```
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：api/startluo/HourglassEnd.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  PeriodId(int)：期數ID
  EndTime(string)：結束時間 格式:HH:ii:ss (24 小時制)
傳入範例：
  data={"PeriodId":1,"EndTime":"16:00:00"}
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
  參考共用錯誤代碼 或
  {"status":1104,"msg":"期數資料異常","data":{}}
```

## WinList - 中獎列表
```
**目前僅列當期
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
URL：api/startluo/WinList.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  RowCount(int)：取得筆數 範圍 10 ~ 100
  GetPage(int)：取得頁數 範圍 >1
  StartDateTime(string)：最後修改注單時間-起始時間 格式:yyyy-mm-dd HH:ii:ss (24 小時制)
  EndDateTime(string)：最後修改注單時間-結束時間 格式:yyyy-mm-dd HH:ii:ss (24 小時制)
傳入範例：
  data={"RowCount":10,"GetPage":1,"StartDateTime":"2023-01-03 15:00:00","EndDateTime":"2023-01-03 18:00:00"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object Array)：
    MemberId(string)：玩家的 memberID
    NickName(string)：玩家暱稱
    PeriodId(int)：期數
    QuizDateTime(string)：競猜時間
    UpdateDateTime(string)：最後修改注單時間
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":[{"MemberId":"LFtjoUck3CPDEWtkxfI77Csudfg2","NickName":"Daisy00001","PeriodId":1,"QuizDateTime":"2023-01-03 15:36:00","UpdateDateTime":"2023-01-03 17:17:57"}]}
失敗範例：
  參考共用錯誤代碼
```
