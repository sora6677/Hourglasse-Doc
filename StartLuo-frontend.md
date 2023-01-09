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
    AuthToken(string)：身分驗證令牌
    NowPeriodId(string)：當前期數
    UserPhone(string)：玩家手機
    NowBalance(int)：玩家剩餘票券
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"AuthToken":"20901e076c658af37e7765d1902d2e63","NowPeriodId":"token:hourglass:0","UserPhone":"0988888888","NowBalance":1}}
失敗範例：
  共用錯誤代碼或
  {"status":1101,"msg":"登入失敗","data":{}}
```

## GetUserData - 取得玩家資料
```
Header：
  MemberId(string)：API收到的 **memberID
  AuthToken(string)：身分驗證令牌
```

```
URL：api/GetUserData.php
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
  {"status":200,"msg":"成功","data":{"UserPhone":"0988547582"}}
失敗範例：
  共用錯誤代碼
```

## UserUpdatePhone - 玩家更新手機
```
Header：
  MemberId(string)：API收到的 **memberID
  AuthToken(string)：身分驗證令牌
```

```
URL：api/UserUpdatePhone.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserUpdatePhone(string)：玩家手機
傳入範例：
  data={"UserPhone":"0912345619"}
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
  {"status":1112,"msg":"手機格式不符","data":{}}
```

***

## GetPeriodList - 取得期數列表
```
Header：
  MemberId(string)：API收到的 **memberID
  AuthToken(string)：身分驗證令牌
```

```
URL：api/startluo/GetPeriodList.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  RowCount(int)：取得筆數 範圍 10 ~ 100
  GetPage(int)：取得頁數 範圍 >1
傳入範例：
  data={"RowCount":10,"GetPage":1}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    TotalPage(int)：總頁數
    TotalCount(int)：總筆數
    PeriodList(object array)：
      PeriodId(int)：期數ID
      StartDateTime(string)：活動開始時間
      EndDateTime(string)：活動結束時間
      IsNow(int)：期數是否進行中 0:不在活動時間 1:進行中
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TotalPage":1,"TotalCount":1,"PeriodList":[{"PeriodId":1,"StartDateTime":"2023-01-06 12:00:00","EndDateTime":"2023-01-14 16:59:59","IsNow":1}]}}
失敗範例：
  {"status":1102,"msg":"玩家不存在","data":{}}
  {"status":1105,"msg":"期數異常","data":{}}
```

## GetUserBetList - 取得競猜注單列表
```
Header：
  MemberId(string)：API收到的 **memberID
  AuthToken(string)：身分驗證令牌
```

```
URL：api/startluo/GetUserBetList.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  RowCount(int)：取得筆數 範圍 10 ~ 100
  GetPage(int)：取得頁數 範圍 >1
  PeriodId(int)：指定期數
傳入範例：
  data={"RowCount":10,"GetPage":1,"PeriodId":1}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    TotalPage(int)：總頁數
    TotalCount(int)：總筆數
    BetList(object array)：
      BetNo(int)：注單編號
      PeriodId(string)：期數
      QuizTime(string)：猜沙漏結束時間 時間格式: HH:ii:ss (24 小時制)
      UpdateDateTime(string)：注單更新時間
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TotalPage":1,"TotalCount":1,"BetList":[{"BetNo":1,"PeriodId":1,"QuizTime":"15:36:00","UpdateDateTime":"2023-01-05 04:01:59"}]}}
失敗範例：
  {"status":1102,"msg":"玩家不存在","data":{}}
  {"status":1105,"msg":"期數異常","data":{}}
```

## CreateUserBet - 建立競猜注單
```
Header：
  MemberId(string)：API收到的 **memberID
  AuthToken(string)：身分驗證令牌
```

```
URL：api/startluo/CreateUserBet.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  QuizTime(string)：猜沙漏結束時間 時間格式: HH:ii:ss (24 小時制)
  UserPhone(string)：玩家手機
傳入範例：
  data={"QuizTime":"15:36:00","UserPhone":"0988888888"}
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
  {"status":1102,"msg":"玩家不存在","data":{}}
  {"status":1103,"msg":"禁止下注","data":{}}
  {"status":1105,"msg":"期數異常","data":{}}
  {"status":1106,"msg":"票券餘額不足","data":{}}
  {"status":1107,"msg":"取票券餘額失敗","data":{}}
  {"status":1108,"msg":"下注失敗","data":{}}
  {"status":1109,"msg":"票券使用異常","data":{}}
  {"status":1110,"msg":"下注處理中","data":{}}
```

## CreateUserMultiBet - 建立多筆競猜注單
```
Header：
  MemberId(string)：API收到的 **memberID
  AuthToken(string)：身分驗證令牌
```

```
URL：api/startluo/CreateUserMultiBet.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  StartQuizTime(string)：猜沙漏結束時間-起始 時間格式: HH:ii:ss (24 小時制)
  TotalSecond(int)：包牌總秒數
  UserPhone(string)：玩家手機
傳入範例：
  data={"StartQuizTime":"15:36:00","TotalSecond":2,"UserPhone":"0988888888"}
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
  {"status":1102,"msg":"玩家不存在","data":{}}
  {"status":1103,"msg":"禁止下注","data":{}}
  {"status":1105,"msg":"期數異常","data":{}}
  {"status":1106,"msg":"票券餘額不足","data":{}}
  {"status":1107,"msg":"取票券餘額失敗","data":{}}
  {"status":1108,"msg":"下注失敗","data":{}}
  {"status":1109,"msg":"票券使用異常","data":{}}
  {"status":1110,"msg":"下注處理中","data":{}}
```

## UpdateUserBet - 修改競猜注單
```
Header：
  MemberId(string)：API收到的 **memberID
  AuthToken(string)：身分驗證令牌
```

```
URL：api/startluo/UpdateUserBet.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  BetNo(int)：注單編號
  QuizTime(string)：猜沙漏結束時間 時間格式: HH:ii:ss (24 小時制)
傳入範例：
  data={"BetNo":1,"QuizTime":"13:02:01"}
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
  {"status":1102,"msg":"玩家不存在","data":{}}
  {"status":1103,"msg":"禁止下注","data":{}}
  {"status":1105,"msg":"期數異常","data":{}}
  {"status":1111,"msg":"查無此注單編號","data":{}}
```

## UpdateUserMultiBet - 修改多筆競猜注單
```
Header：
  MemberId(string)：API收到的 **memberID
  AuthToken(string)：身分驗證令牌
```

```
URL：api/startluo/UpdateUserMultiBet.php
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  StartBetNo(int)：注單編號-起始
  StartQuizTime(string)：猜沙漏結束時間-起始 時間格式: HH:ii:ss (24 小時制)
  TotalSecond(int)：包牌總秒數
傳入範例：
  data={"StartBetNo":1,"StartQuizTime":"13:02:01","TotalSecond":20}
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
  {"status":1102,"msg":"玩家不存在","data":{}}
  {"status":1103,"msg":"禁止下注","data":{}}
  {"status":1105,"msg":"期數異常","data":{}}
  {"status":1111,"msg":"查無此注單編號","data":{}}
```
