# 輸出

## 輸出

在Python中，將指定內容顯示在螢幕上的方法有以下幾種：  
1. sys.stdout.write\(\)：將指定內容打印於螢幕中，上面的Hello World的程式碼即是透過此方法來顯示出Hello World的。  
2. print\(\)：此方法其實是調動sys.stdout.write\(\)方法，並在指定內容最後加上換行符號'\n'。

print\(\)的函式架構為如下，可接收多個數值，詳細參數描述如下：  
sep：各數值間是以何種內容連結  
end：顯示內容的最後以何種內容結束，預設為換行符號。  
file：預設為sys.stdout代表是一個標準輸出環境\(螢幕\)，亦可指向其他位置。  
flush：可決定資料先暫存於緩衝區或直接輸出。

```text
print(value1, value2, value3, ..., sep=' ', end='\n', file=sys.stdout, flush = False)
```

### 排版

| 函式 | 功用 |
| --- | --- | --- | --- | --- |
| rjust\(x\) | 向右靠齊，並在字串左邊補空格，總體\(字串+空格\)的長度為x+1。 |
| ljust\(x\) | 向左靠齊，並在字串右邊補空格，總體\(字串+空格\)的長度為x+1。 |
| center\(x\) | 置中對齊，在字串左右補空格，總體\(字串+空格\)的長度為x+1。 |
| zfill\(x\) | 在字串左邊補0，總體\(字串+空格\)的長度為x+1。 |

```text
a = '-3.14'
print(a.rjust(10))
輸出結果：
 ​    -3.14
 
print(a.ljust(10))
輸出結果：
-3.14     

print(a.center(10))
輸出結果：
  -3.14   

print(a.zfill(10))
輸出結果：
-000003.14
```

### \_\_repr\_\_ vs. \_\_str\_\_

在指令互動環境中，所使用的是來自於 \_\_repr\_\_物件的repr\(\)函式來顯示運算結果，其採用正式\(official\)的顯示方式，是對於解釋器較好解讀的方式，所回傳的是沒有歧義的字串表示\(Unambigous\)。

而print\(\)函式則使用來自於 \_\_str\_\_物件的str\(\)函式來顯示較非正式\(unofficial\)的顯示方式，是對於使用者較好解讀的方式，所回傳的是可讀式的字串表示\(Readable\)。



> 在Python中，底線開頭的是暗示說直接呼叫或直接使用。除此之外，其實可以自定義\_\_str\_\_與 \_\_repr\_\_，讓其客製化產生你所想要顯示的格式。

由下圖可以發現，當傳入整數時，str\(\)與repr\(\)並無差異，然而若傳入字串時，repr\(\)會多出兩個雙引號。

> eval函式的功用是接收字串格式，並將當作一段Python的程式碼執行產生內容。

```text
print(str('Hello World'))
輸出結果：
Hello World

print(repr('Hello World'))
輸出結果：
"Hellow World"
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

# 以上為互動式指令介面畫面
```

### 格式化字串

在輸出時，我們可以格式化字串來顯示，提升彈性，有兩種方式達成此效果。  
1. 使用%格式化字串

```text
print("%d %.2f %s" % (1,0.2,'Joey'))
輸出結果：
1 0.2 Joey
# 在此例子中，%d代表對應整數, %.2f對應浮點數, %s對應字串，在該字串後用%接一個元組tuple。
# 此tuple中所包含的值包括所要顯示的對應值。
```

2. 使用format格式化字串

```text
print("{} {}".format("Hello","World"))
輸出結果：
Hello World
# 不指定順序，而是以默認相應值顯示。

print("{0} {1} {0}".format("Hello","World"))
輸出結果：
Hello World Hellow
# 指定位置

print("網站:{name},網址:{url}".format(name="火焰箭",url="www.xdxdxd.tw"))
輸出結果：
網站:火焰箭,網址:www.xdxdxd.tw
# 指定參數

print("名字:{name},網址:{1}".format(name="火焰箭","www.xdxdxd.tw"))
輸出結果：
網站:火焰箭,網址:www.xdxdxd.tw
# 指定位置、參數

siteDict = {name:"火焰箭",url:"www.xdxdxd.tw")}
print("網站:{name},網址:{url}".format(**site))
輸出結果：
# 使用字典傳遞

siteList = ["火焰箭","www.xdxdxd.tw"]
print("網站:{0[0]},網址:{0[1]}".format(siteList))
輸出結果：
# 使用串列傳遞

siteValue = Site("火焰箭")
# 假定以siteValue實例化Site類別，並指定其類別參數value為6。
print("網站:{0.value}".format(siteValue))
輸出結果：
# 以Object傳入format，類別的相關細節在之後章節詳述
```

使用%格式化字串是過去使用的方式，而format格式化字串的方式則是在Python2中所創立的，其可讓開發人員更方便的使用。以下為format格式化字串方式的相關資訊整理。

| format格式化 | 功用 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| {:.2f} | 取到小數點第二位 |
| {:+.2f} | 指定符號+取到小數點第二位 |
| {:.0f} | 不帶小數 |
| {:0&gt;3d} | 補零，填充左邊，此例字串輸出結果長度須為3 |
| {:x&lt;5d} | 補x，填充右邊，此例字串輸出結果長度須為5 |
| {:,} | 以逗號分隔的數字格式，每三位加個逗點 |
| {.2f%} | 百分比 |
| {.2fe} | 科學記號標記法 |
| {:5d} | 右對齊，此例總長度須為5 |
| {:&lt;10d} | 左對齊，此例總長度須為10 |
| {:^4d} | 置中對齊，此例總長度須為4 |
| {:b} | 以二進制表示 |
| {:d} | 以十進制表示 |
| {:o} | 以八進制表示 |
| {:x} | 以十六進制表示 |
| {:\#x} | 以十六進制表示，並在文字前加上0x |
| {:\#X} | 以十六進制表示，並在文字前加上0Xfr |
| {{}} | 若想在字串中顯示{}，則僅需再多加一個{}即可。 |
| {!s} | 使用str\(\)函式顯示 |
| {!r} | 使用repr\(\)函式顯示 |
| {!a} | 使用ascii編碼顯示 |
| {s} | 字串 |

> format亦可作為函式來進行處理，如下

```text
formatFunc = "{:.2f},{:s}".format
print(formatFunc(0.2,"XDXD"))
輸出結果：
0.20,XDXD
```

> 日期亦可使用format，在之後的章節會再討論日期的細節。

```text
import datetime
now = datetime.datetime.now()
#now為日期物件
print("{:%Y-%m-%d}".format(now))
輸出結果：
2018-05-13
```

> 字典亦可作為傳入值

```text
formatDict = {"Joey":1,"Kobe":2}
print("Joey:{0[Joey]:d},Kobe:{0[Kobe]:d}".format(formatDict))
輸出結果：
Joey:1,Kobe:2

print("Joey:{Joey:d},Kobe:{Kobe:d}".format(**formatDict))
輸出結果：
Joey:1,Kobe:2
```

總而言之  
1. 要格式化的字串應以{ }包圍  
2. 冒號：前的數字為指定位置  
3. 冒號：後的數字為指定該字串的總長度為多少

```text
print("{0:10}-->{1:10d}".format("數值",123))
輸出結果：
數值        -->       123
```

## 輸入

### 取得用戶所輸入的內容

有時我們需要取得用戶所輸入的內容並加以處理\(如帳號密碼等等\)，而當然用戶不會知道需要輸入什麼內容，因此需要給予提示訊息，這一切僅需使用input\(\)函式即可完成。

```text
# 以下程式代碼會先在螢幕中打印出「請輸入您的姓名」的內容，並等待接收用戶所輸入的資訊。
input('請輸入您的姓名')
```

除此之外，你亦可使用sys.sdin來取得用戶所輸入的內容，如下：

```text
>>> import sys
>>> sys.stdin.readline()
Hello World # 此為使用者輸入的
'Hello World\n'

# 以上為互動式指令介面畫面
```

可以發現上面的程式碼輸出最後是有換行符號\n的，這也是其與input\(\)函式的差別，input\(\)函式的輸出最後並無換行符號。

### 將輸入內容轉至檔案中

我們可以將目標文檔的引用賦給sys.stdout，如此print\(\)函式所輸出的內容則會直接寫至該目標文檔中。

```text
import sys
#下段程式碼為建立可寫入資料的檔案
outputLog = open('outputLog','w')
sys.sdout = outputLog
print('Hello World')
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

# 以上為互動式指令介面畫面
```

