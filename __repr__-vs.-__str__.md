# \_\_repr\_\_ vs.  \_\_str\_\_

## \_\_repr\_\_ vs. \_\_str\_\_

在指令互動環境中，所使用的是來自於 \_\_repr\_\_物件的repr\(\)函式來顯示運算結果，其採用正式\(official\)的顯示方式，是對於解釋器較好解讀的方式，所回傳的是沒有歧義的字串表示\(Unambigous\)。

而print\(\)函式則使用來自於 \_\_str\_\_物件的str\(\)函式來顯示較非正式\(unofficial\)的顯示方式，是對於使用者較好解讀的方式，所回傳的是可讀式的字串表示\(Readable\)。



> 在Python中，底線開頭的是暗示說直接呼叫或直接使用。除此之外，其實可以自定義\_\_str\_\_與 \_\_repr\_\_，讓其客製化產生你所想要顯示的格式。

由下圖可以發現，當傳入整數時，str\(\)與repr\(\)並無差異，然而若傳入字串時，repr\(\)會多出兩個雙引號。

> eval函式的功用是接收字串格式，並將當作一段Python的程式碼執行產生內容。

```text
>>> str('Hello World')
'Hello World'
>>> repr('Hello World')
'"Hellow World"'
```

由下圖可更清楚地看出，str\(\)函式會計算並回傳傳入值內容的字串格式，而repr\(\)函式則會回傳可以產生相應Object的Python程式碼之字串格式，需用eval\(\)函式來得到內容。  
  
除此之外，亦可得到一個訊息，那就是repr\(\)的輸入值除了字串以外，亦可是任一Object。

```text
>>> import datetime
>>> currentTime = datetime.datetime.now()
>>> str(currentTime)
'2018-05-11 17:31:53.557488'
>>> repr(currentTime)
'datetime.datetime(2018, 5, 11, 17, 31, 53, 557488)'
>>> eval(repr(currentTime))
datetime.datetime(2018, 5, 11, 17, 31, 53, 557488)
```



