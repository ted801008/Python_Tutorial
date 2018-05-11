# 打印資料

## Hello World!

學習程式語言一開始不免俗就是要來Hello World一下囉，基本上所有程式人一開始所學的就是要如何在結果輸出顯示Hello World。  
方法非常的簡單，如下：

```text
>>> 'Hello World'
```

如此一來，就可顯示出Hello World啦～  
其中用單引號或雙引號所圍住的內容會被以字串型態被Python建立，因此我們的'Hello World'物件的型態也會是字串囉。

## 顯示

在Python中，將指定內容顯示在螢幕上的方法有以下幾種：  
1. sys.stdout.write\(\)：將指定內容打印於螢幕中，上面的Hello World的程式碼即是透過此方法來顯示出Hello World的。  
2. print\(\)：此方法其實是調動sys.stdout.write\(\)方法，並在指定內容最後加上換行符號'\n'。

print\(\)的函式架構為如下，可接收多個數值，而sep的是各數值間是以何種內容連結，end的則是顯示內容的最後以何種內容結束。

```text
print(value1, value2, value3, ..., sep=' ', end='\n', file=sys.stdout)
```

### 取得用戶所輸入的內容

有時我們需要取得用戶所輸入的內容並加以處理\(如帳號密碼等等\)，而當然用戶不會知道需要輸入什麼內容，因此需要給予提示訊息，這一切僅需使用input\(\)函式即可完成。

```text
# 以下程式代碼會先在螢幕中打印出「請輸入您的姓名」的內容，並等待接收用戶所輸入的資訊。
>>> input('請輸入您的姓名')
```

除此之外，你亦可使用sys.sdin來取得用戶所輸入的內容，如下：

```text
>>> import sys
>>> sys.stdin.readline()
Hello World
'Hello World\n'
```

可以發現上面的程式碼輸出最後是有換行符號\n的，這也是其與input\(\)函式的差別，input\(\)函式的輸出最後並無換行符號。

### 將打印內容轉至檔案中

我們可以將目標文檔的引用賦給sys.stdout，如此print\(\)函式所輸出的內容則會直接寫至該目標文檔中。

```text
>>> import sys
#下段程式碼為建立可寫入資料的檔案
>>> outputLog = open('outputLog','w')
>>> sys.sdout = outputLog
>>> print('Hello World')
#因此print()函式所輸出的內容並不會顯示於螢幕上，而是寫至目標文檔中。
```

此時，只要調動任何print\(\)函式，則都會將指定內容寫至目標文檔中。因此，若還想要輸出一些不想寫至檔案而顯示於螢幕上的內容時，最好將原始的console引用保存下來，當在途中要顯示於螢幕上時，即可恢復，如下。

```text
>>> __console__ = sys.stdout
#...
#輸出導向至目標檔案
#...
>>> sys.stdout = __console__
#此時已重新回復輸出預設
```

####  \_\_repr\_\_ vs. \_\_str\_\_ {#__repr__-vs-__str__}

在指令互動環境中，所使用的是repr\(\)函式來顯示運算結果，其採用正式\(official\)的顯示方式，是對於解釋器較好解讀的方式。而print\(\)函式則使用str\(\)函式來顯示較非正式\(unofficial\)的顯示方式，是對於使用者較好解讀的方式。 簡單說，repr\(\)函式是來自於 \_\_repr\_\_物件所產生的字串格式，所回傳的是沒有歧義的字串表示\(Unambigous\)。而str\(\)函式則是來自於 \_\_str\_\_物件所產生的字串格式，所回傳的是可讀式的字串表示\(Readable\)。

> 在Python中，底線開頭的是暗示說直接呼叫或直接使用。除此之外，其實可以自定義\_\_str\_\_與 \_\_repr\_\_，讓其客製化產生你所想要顯示的格式。

由下圖可以發現，當傳入整數時，str\(\)與repr\(\)並無差異，然而若傳入字串時，repr\(\)會多出兩個雙引號，若想要重新建置Object，應使用eval\(\)函式。

> eval函式的功用是接收字串格式，並將當作一段Python的程式碼執行產生內容。

```text
>>> str('Hello World')
'Hello World'
>>> repr('Hello World')
'"Hellow World"'
```

由下圖可發現，str\(\)函式會計算並回傳傳入值內容的字串格式，而repr\(\)函式則會回傳可以產生相應Object的Python程式碼之字串格式，需用eval\(\)函式來得到內容。

```text
>>> import datetime
>>> currentTime = datetime.datetime.now()
>>> str(currentTime)'
2018-05-11 17:31:53.557488'
>>> repr(currentTime)'
datetime.datetime(2018, 5, 11, 17, 31, 53, 557488)'
>>> eval(repr(currentTime))
datetime.datetime(2018, 5, 11, 17, 31, 53, 557488)
```

在Python3中，你會發現當傳入特定浮點數運算結果時，str\(\)與repr\(\)所產生出的結果會是一樣的，

```text
>>> 1.0-0.80.19999999999999996
>>> repr(1.0-0.8)
'0.19999999999999996'
>>> str(1.0-0.8)
'0.19999999999999996'
```

