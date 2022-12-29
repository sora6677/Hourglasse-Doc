# StartLuoPage-frontend-Doc 開始囉頁面前台

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
URL：api/startpage/GetPageIndex.php
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
**尚未從後台建立資料時預設回傳
成功範例：
  {"status":200,"msg":"成功","data":{"content":{"imageUrl":"","events":[]}}}
失敗範例：
  共用錯誤代碼
```

## GetPageRichStart - 發財開始囉
```
URL：api/startpage/GetPageRichStart.php
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
**尚未從後台建立資料時預設回傳
成功範例：
  {"status":200,"msg":"成功","data":{"content":{"imageUrl":"","detailImage":"","detailImage_phone":"","eventRule":"","titleImage":"","startTime":"","timeText":"","locationText":"","btnImage_1":"","btnImage_2":"","link_1":"","link_2":""}}}
失敗範例：
  共用錯誤代碼
```

## GetPageMoneyStart - 賺錢開始鑼
```
URL：api/startpage/GetPageMoneyStart.php
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
**尚未從後台建立資料時預設回傳
成功範例：
  {"status":200,"msg":"成功","data":{"content":{"imageUrl":"","detailImage":"","detailImage_phone":"","eventRule":"","titleImage":"","startTime":"","timeText":"","locationText":"","btnImage_1":"","btnImage_2":"","link_1":"","link_2":""}}}
失敗範例：
  共用錯誤代碼
```

## GetPageNewActivity - 最新活動
```
URL：api/startpage/GetPageNewActivity.php
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
**尚未從後台建立資料時預設回傳
成功範例：
  {"status":200,"msg":"成功","data":{"content":{"imageUrl":"","titleImage":"","content":"","cards":[]}}}
失敗範例：
  共用錯誤代碼
```

## GetPageMusicActivity - 音樂祭活動
```
URL：api/startpage/GetPageMusicActivity.php
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
**尚未從後台建立資料時預設回傳
成功範例：
  {"status":200,"msg":"成功","data":{"content":{"imageUrl":"","titleImage":"","contentImage":"","startTime":"","timeText":"","locationText":"","btnImage":"","link":""}}}
失敗範例：
  共用錯誤代碼
```

## GetPageStartLuoActivity - 沙漏活動
```
URL：api/startpage/GetPageStartLuoActivity.php
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
**尚未從後台建立資料時預設回傳
成功範例：
  {"status":200,"msg":"成功","data":{"content":{"eventRule":""}}}
失敗範例：
  共用錯誤代碼
```

## GetPageFlyingCarActivity - 皂飛車活動
```
URL：api/startpage/GetPageFlyingCarActivity.php
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
**尚未從後台建立資料時預設回傳
成功範例：
  {"status":200,"msg":"成功","data":{"content":{"timeText":"","locationText":"","eventRule":"","btnImage":"","link":""}}}
失敗範例：
  共用錯誤代碼
```

## GetPageBrand - 品牌與名人
```
URL：api/startpage/GetPageBrand.php
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
**尚未從後台建立資料時預設回傳
成功範例：
  {"status":200,"msg":"成功","data":{"content":{"cards":[],"brands":[]}}}
失敗範例：
  共用錯誤代碼
```

## GetPageServiceInfo - 服務條款
```
URL：api/startpage/GetPageServiceInfo.php
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
**尚未從後台建立資料時預設回傳
成功範例：
  {"status":200,"msg":"成功","data":{"content":{"personalInfo":"","gameManage":"","usersContract":"","returnHandle":"","privacy":""}}}
失敗範例：
  共用錯誤代碼
```
