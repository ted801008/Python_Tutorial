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

| 指令 | 說明 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| %% | 顯示%符號 |
| %d, %i | 輸出十進位整數形式 |
| %f | 將浮點數輸出為十進位浮點數形式 |
| %e, %E | 將浮點數輸出為以科學記號輸出 |
| %x, %X | 以16進位輸出 |
| %o, %O | 以8進位輸出 |
| %s | 以字串輸出 |
| %c | 以字元輸出 |
| %r | 使用repr\(\)函式輸出 |

而以%格式化字串還可藉由  
      1. 指定flag來加以輸出相關格式。  
      2. 設定欲輸出資料的寬度。  
      3. 以浮點數輸出時可指定其小數位數。 

```text
%[flag][width][.precision]
```

```text
範例：

print('%04d'%2)
輸出結果：
0002
#因為指定寬度為4且指定flag為0，所以會在前面補上0。

import math
print(' %-.3f'%math.pi)
輸出結果：
3.142
# 指定靠左對齊並指定最多取到小數位數第三位]
```

2. 使用format格式化字串

而一直到python3後，出現了format\(\)內建函式，而python也建議改使用format\(\)函式，%格式化字串方法可能會在未來廢掉了。

兩種方法所達到的效果目的皆一樣，但format\(\)函式感覺更為清楚。

下面為format\(\)函式的參數描述，  
value為欲被格式化的字串或數值  
format\_spec則為要格式化的規則，同樣是以flag、欄寬、精確度進行搭配。

```text
format(value,format_spec)
```

而可以使用哪些flag來指定相關格式呢？整理如下表

| flag | description |
| --- | --- | --- | --- | --- | --- | --- |
| '\#' | 配合16、8進位進行轉換時，可在前方補上0。 |
| '0' | 數值前補0 |
| '-' | 靠左對齊，若與0共同使用，會優先使用。 |
| ' ' | 保留一個空格 |
| &gt; | 向右靠齊 |
| &lt; | 向左靠齊 |

```text
print(format('Joey','>10s'))
輸出結果：
      Joey

print(format(123456.789,'012.2f'))
000123456.79
```

除了內建函式formtat\(\)以外，亦可使用字串的物件方法format\(\)來達到相同效果。

字串的format\(\)方法有幾種處理方式，但欲被格式化的字串皆須以{ }包圍  
第一種是以冒號  
2. 冒號：前的數字為指定位置或指定參數名\(須在format\(\)函式中指定\)  
3. 冒號：後的數字為指定該字串的相關規定，如寬度、格式等等。

```text
{欄名:format_rule}
# 其中欄名亦可是指定關鍵字引數，但必須於format()函式中以關鍵字名=關鍵字值傳入。
```

| format\_rule | description |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| fill | 可填補任何字元，但不包括大括號 |
| align | &gt;靠左, &gt;靠右, = 填滿, ^置中 |
| sign | 使用+, - , 空格，同%格式化字串 |
| \# | 配合16、8進位進行轉換時，可在前方補上0。 |
| 0 | 數值前補0 |
| width | 欄寬 |
| , | 千位符號，每3位加上逗點 |
| .precision | 指定小數位數。 |
| typecode | 就是前面提到s是字串、d代表數值等等 |

```text
print("{} {}".format("Hello","World"))
輸出結果：
Hello World
# 不指定順序，而是以默認相應值顯示。

print("{0} {1} {0}".format("Hello","World"))
輸出結果：
Hello World Hellow
# 指定位置

import math
print('圓周率為：{0.pi}'.format(math))
輸出結果：
圓周率為：3.141592653589793
#亦可使用傳入物件的屬性

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

print("{0:10}-->{1:10d}".format("數值",123))
輸出結果：
數值        -->       123

print('2進位表示={0:#b}'.format(10))
print('2進位表示={0:b}'.format(10))
輸出結果：
2進位表示=0b1010
2進位表示=1010

print('{0:+,.2f}'.format(1234.5678))
輸出結果：
+1,234.57

print('{0:*^10s}'.format('置中對齊'))
print('{0:*>10s}'.format('靠右對齊'))
print('{0:*= 10d}'.format(10)) # 不允許應用於字串
輸出結果：
***置中對齊***
******靠右對齊
 *******10
```

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

而除了以冒號:進行處理，還可使用!進行轉換

```text
{欄名!轉換指令}
```

```text
from decimal import Decimal
print('{0}, {0!s}, {0!r}, {0!a}'.format(Decimal(22.5)))
輸出結果：
22.5, 22.5, Decimal('22.5'), Decimal('22.5')
# !s為str()
# !r為repr()
# !a為轉換為ascii編碼的字串
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

