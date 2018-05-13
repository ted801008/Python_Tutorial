# 字串\(String\)

## 字串宣告

在Python中，字串資料可由雙引號或單引號宣告，如下

```
>>> "Hello World"
'Hello World'
>>> 'Hello World'
'Hello World'
#兩者型態皆為str
>>> len('Hello World')
11
#字串長度可透過len()函式來得到
```

> Note：Python使用反斜線\來轉譯特殊字符，例如\n即代表換行。  
> 若以雙引號建立字串，而內容亦有雙引號時，則必須在內容中的雙引號前加上\進行跳脫\(escape\)處理，亦此類推，單引號亦同樣處理之。  
> 另一方面，若字串內容有\則前面亦要加上\\，但若\後並無接特殊符號，則仍會呈現\。  
>   
> 當然，你亦可在字串的雙引號或單引號前加上r，來代表原始字串\(raw\)。

```text
>>> print("Hello \"World\"")
Hello "World"

>>> print('Hello \'World\'')
Hello 'World'

>>> print('Hello \World')
Hello \World

>>> print('Hello \\World')
Hello \World

>>> print(r'Hello \\World')
Hello \\World
```

> 除此之外，反斜線\亦可作為續行符號，表示下一行是上一行的延續。

```text
>>> print('xyz\
... abcd')
xyzabcd
```

## 字串運算

### 加法

字串間的加法，可將不同字串拼接在一起。

```text
>>> print("Hello "+"World")
Hello World
```

### 乘法

字串的乘法，能重複該字串。

```text
>>> print("*"*10)
**********
```

### 切片\(Slice\)

Python中的字串可用\[ \]來取得字串中範圍的字，索引是從0開始。

```text
String[start:end:gap]
start為起始索引位置
end為結束索引位置，但注意的是真正被索引到的結束索引位置為此數減去1。
gap為間隔，意味著每次跳幾個字，預設為1。
```

```text
>>> a = "Hello World"

#取第一個字
>>> a[0]
'H'

#取第3到第7個字
>>> a[2:7]
'llo W'
#這邊要注意的點是
# 1. :的前後數字代表著從那個索引到哪個索引，這邊例子代表從第2個索引到第6個索引。
# 2. 最後的索引值並不會被索引到，因此這邊例子的結束索引值為7，但實際上僅會索引到6。

#起始索引省略
>>> a[:5]
'Hello'
# 意味著從字串的一開始索引到第4個索引

#結束索引省略
>>> a[6:]
'World'
# 意味著從第六個索引到字串的最後。

>>> a[0:7:2]
'HloW'
# 意味著從0開始索引到第6個索引，每次跳兩個字。

>>> a[:]
'Hello World'
# 意味著從0開始索引到字串的最後

>>> a[::-1]
'dlroW olleH'
# 意味著倒過來索引
```

另外，索引的值亦可為負數，代表著從字串後面倒過來開始索引。

```text
>>> a = "Hello World"
>>> a[-1]
'd'
#-1索引代表字串最右邊的字。
```

### 不可改變的\(Immuable\)

在Python中，字串是不可改變的。

```text
>>> a = "Hello World"
>>> a[1] = "X"
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
# 由上例即可看出字串是不容許被改變的。
```

### Unicode字串

在Python2中，字串預設是以ASCII編碼儲存。  
在Python3中，字串預設皆為unicode編碼儲存。  
若想以unicode編碼來儲存字串，僅需在字串的引號前加上u。

```text
>>> u"Hello World"
```

在Python2中，因對unicode並無較好的支援，因此len\(\)函式所得到的字串長度代表著是該字串的位元組序列長度\(Byte sequence\)。

```text
#Python2
>>> text1 = '測試'
>>> len(text1)
6
# 原因在於其計算該字串的位元組序列長度，而'測試'這兩個字元以UTF-8編碼後，會使用6個位元組。

#Python3
>>> text2 = '測試'
>>> len(text2)
2
# Python3對於unicode編碼就有較好的支援

#Python2
>>> text3 = u'測試'
>>> len(text3)
2

#Python3
# 亦可使用bytes()方法來用位元組序列代表該字串。
>>> len(bytes('測試','utf-8'))
>>> len(text4)
6
```

## 格式化字串

在打印字串時，我們可以格式化字串來顯示，提升彈性，有兩種方式達成此效果。  
1. 使用%格式化字串

```text
>>> print("%d %.2f %s" % (1,0.2,'Joey'))
1 0.2 Joey
# 在此例子中，%d代表對應整數, %.2f對應浮點數, %s對應字串，在該字串後用%接一個元組tuple。
# 此tuple中所包含的值包括所要顯示的對應值。
```

2. 使用format格式化字串

```text
>>> print("{} {}".format("Hello","World"))
Hello World
# 不指定順序，而是以默認相應值顯示。

>>> print("{0} {1} {0}".format("Hello","World"))
Hello World Hellow
# 指定順序

>>> print("網站:{name},網址:{url}".format(name="火焰箭",url="www.xdxdxd.tw"))
網站:火焰箭,網址:www.xdxdxd.tw
# 指定參數

>>> siteDict = {name:"火焰箭",url:"www.xdxdxd.tw")}
>>> print("網站:{name},網址:{url}".format(**site))
# 使用字典傳遞

>>> siteList = ["火焰箭","www.xdxdxd.tw"]
>>> print("網站:{0[0]},網址:{0[1]}".format(siteList))
# 使用串列傳遞

>>> siteValue = Site("火焰箭")
# 假定以siteValue實例化Site類別，並指定其類別參數value為6。
>>> print("網站:{0.value}".format(siteValue))
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
>>> formatFunc = "{:.2f},{:s}".format
>>> print(formatFunc(0.2,"XDXD"))
0.20,XDXD
```

> 日期亦可使用format，在之後的章節會再討論日期的細節。

```text
>>> import datetime
>>> now = datetime.datetime.now()
#now為日期物件
>>> print("{:%Y-%m-%d}".format(now))
2018-05-13
```

