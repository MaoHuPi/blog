<!-- title: Web請求 -->
<!-- subtitle: Web請求格式與cURL基本使用 -->
<!-- category: notes -->
<!-- tags: web, computing -->
<!-- published time: 2023/09/16 -->
<!-- author: MaoHuPi -->

# Web請求

---

## 參考資料

* HTB Academy - Web Request

---

HTTP是一種請求協議，常用於處理網頁前後端之溝通。

## URL (uniform resource locator)

定型化資源定位器，簡稱網址，用於向伺服器請求網路資源。  
其形式如下：

```txt
https://username:password@domainname.com/filename.php?key=value&key2=value2#footer
|------|-----------------|--------------|------------|---------------------|-----|
 scheme       user            host          path          query string   fragment
```

* 方案 (scheme)  
連線協議種類，常見的有`http`、`https`、`ftp`、`ftps`等
* 用戶 (user)  
瀏覽者的帳號、密碼，以「:」分隔其二者
* 主機 (host)  
為子域名、域名所組成的`Fully Qualified Domain Name`
* 路徑 (path)  
訪問之處理檔案的路徑，預設為`index.{副檔名}`，其可為動態或靜態檔案之路徑
* 參數 (query string)
用於指定訪問時鎖鑰附加的參數鍵值對，以「?」與路徑分隔，並以「&」串接每個由`{鍵}={值}`型式組成的鍵值對
* 區段 (fragment)  
用於指定要訪問的內容區段，在瀏覽器中會以「捲動至id為該值之元素的所在位置」的方式來呈現其作用

## RESTful API

用於處理資料交換之資刪改查的一種型式。

|請求目的|請求方式|參數說明|
|---|---|---|
|新增 (Create)|POST|使用`content`來附加欲新增實體的內容|
|查詢 (Read)|GET|使用`query string`來指定要查詢的實體|
|修改 (Update)|PUT/PATCH|使用`query string`來指定要修改的實體，並用`content`來附加欲修改成的內容，`PUT`用於覆蓋式更改；`PATCH`用於對實體做部分修改|
|刪除 (Delete)|DELETE|使用`query string`來指定要刪除的實體|

## cURL

使用cURL可以以無`GUI`的方式檢視回應內容，有利於測試`API`與暴力破解他人之服務。

### 常用參數

* `<url>`  
用於指定要訪問的目標網址
* `-o <filename>`  
用於指定輸出檔案的路徑，並寫入至本地檔案
* `-O`  
使用原檔案名稱作為輸出檔案的名稱，並寫入至本地檔案
* `-v`  
顯示請求與回應的標頭
* `-i`  
顯示回應的完整內容 (標頭與內容)
* `-I`  
僅顯示標頭
* `-H <headers>`  
用於指定附加的標頭參數
* `-u <username>:<password>`  
用於指定訪問時的使用者資訊
* `-d <data>`  
用於附加請求的`content`
* `-b <cookies>`  
用於附加請求的`cookie`
* `-k`  
忽略SSL憑證有效性的檢查

## 回應狀態 (HTTP request status)

|狀態碼|整體性狀態說明|
|---|---|
|1xx|回報狀態而不影響處理|
|2xx|處理成功|
|3xx|重新導向 (網址跳轉)|
|4xx|處理錯誤 (請求格式錯誤或找不到檔案等)|
|5xx|無法處理 (伺服器服務出錯)|

## 標頭參數

* 通用標頭
	* `Date`  
	用於標註請求發送時的時間，以便於檢查是否有請求逾時之狀況，使用`UTC`時間格式
	* `Connection`  
	說明是否需要進行連續請求，若是其值為`keep-alive`，反之則為`close`
* 實體標頭
	* `Content-Type`  
	用於標註內容的格式與編碼格式，內容格式使用`MIME Type`來註記，編碼格式則是以`;charset={編碼格式}`來註記
	* `Media-Type`  
	用於標註數據的格式與編碼格式，數據格式使用`MIME Type`來註記，編碼格式則是以`;charset={編碼格式}`來註記
	* `Boundary`  
	用於當作多個內容區段的分段標記
	* `Content-Length`  
	用於標註數傳輸內容的長度
	* `Content-Encoding`  
	用於標註數傳輸前的轉換或壓縮格式
* 請求頭
	* `Host`  
	用於標註目標主機的域名或`IP`
	* `User-Agent`  
	用於標註請求時所使用的工具名稱與版本，`cURL`為`curl/{版本}`
	* `Referer`  
	用於標註連進的來源網址，比如從`google`點擊搜尋結果連結進入網站，那麼此標頭之值便為`https://google.com`
	* `Accept`  
	用於標註請求方可解析的內容類型，使用`MIME Type`來註記
	* `Cookie`  
	用於標註`cookie`的鍵值對
	* `Authorization`  
	用於驗證使用者的身分，獨立於`cookie`外，與`session id`不同
* 回應頭
	* `Server`  
	用於標註伺服器的伺服器軟體版本與作業系統
	* `Set-Cookie`  
	用於標註新的`cookie`
	* `WWW-Authenticate`  
	用於標註所需的身分驗證
* 安全標頭
	* `Content-Security-Policy`  
	用於標註網站對於外部資源的限制，用於預防`XSS攻擊`
	* `Strict-Transport-Security`  
	用於阻止瀏覽器通過`HTTP`來進行溝通，以防止`MiTM攻擊`或`網路嗅探`
	* `Referrer-Policy`  
	用於防止瀏覽器使用`Referrer`標頭而造成的`非公開url外洩`