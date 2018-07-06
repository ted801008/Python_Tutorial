# 字串\(String\)

## 字串宣告

在Python中，字串資料可由雙引號或單引號宣告如下

```
print("Hello World")
輸出結果：
Hello World

print('Hello World')
輸出結果：
'Hello World'
#兩者型態皆為str

print(len('Hello World'))
輸出結果：
11
#字串長度可透過len()函式來得到

print('''
H
e
l
l
o World''')
輸出結果：
H
e
l
l
o World
# 使用三個單引號或三個雙引號達成多行字串。
```

> Note：Python使用反斜線\來轉譯特殊字符，例如\n即代表換行。  
> 若以雙引號建立字串，而內容亦有雙引號時，則必須在內容中的雙引號前加上\進行跳脫\(escape\)處理，亦此類推，單引號亦同樣處理之。  
> 另一方面，若字串內容有\則前面亦要加上\\，但若\後並無接特殊符號，則仍會呈現\。  
>   
> 當然，你亦可在字串的雙引號或單引號前加上r，來代表原始字串\(raw\)。

```text
print("Hello \"World\"")
輸出結果：
Hello "World"

print('Hello \'World\'')
輸出結果：
Hello 'World'

print('Hello \World')
輸出結果：
Hello \World

print('Hello \\World')
輸出結果：
Hello \World

print(r'Hello \\World')
輸出結果：
Hello \\World
```

## 字串運算

### 加法

字串間的加法，可將不同字串拼接在一起。

```text
print("Hello "+"World")
輸出結果：
Hello World
```

### 乘法

字串的乘法，能重複該字串。

```text
print("*"*10)
輸出結果：
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
a = "Hello World"

#取第一個字
print(a[0])
輸出結果：
H

#取第3到第7個字
print(a[2:7])
輸出結果：
llo W
#這邊要注意的點是
# 1. :的前後數字代表著從那個索引到哪個索引，這邊例子代表從第2個索引到第6個索引。
# 2. 最後的索引值並不會被索引到，因此這邊例子的結束索引值為7，但實際上僅會索引到6。

#起始索引省略
print(a[:5])
輸出結果：
Hello
# 意味著從字串的一開始索引到第4個索引

#結束索引省略
print(a[6:])
輸出結果：
World
# 意味著從第六個索引到字串的最後。

print(a[0:7:2])
輸出結果：
HloW
# 意味著從0開始索引到第6個索引，每次跳兩個字。

print(a[:])
輸出結果：
Hello World
# 意味著從0開始索引到字串的最後

print(a[::-1])
輸出結果：
dlroW olleH
# 意味著倒過來索引
```

另外，索引的值亦可為負數，代表著從字串後面倒過來開始索引。

```text
a = "Hello World"
print(a[-1])
輸出結果：
d
#-1索引代表字串最右邊的字。
```

> 另一方面，在Python中，字串\(String\)是不可變的\(Immutable\)。

```text
a = "Hello World"
a[1] = "X"
輸出結果：
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
# 由上例即可看出字串是不容許被改變的。
```

#### 切片slice\(\)方法

為何要特別介紹這個方法呢？  
因為在我們之後要維護很大型的系統時，若總是在那邊切片到某個特定的索引值，程式碼就會看起來很亂，而後面維護的人也會很難看懂你的代碼。  
這時若想達到切片的效果而又要避免這種狀況時，就得使用slice\(\)方法了。

```text
slice(start,stop,step=1)
```

```text
officer_info = ['joey',12,'student',82]
name = slice(0,1,1)
print(officer_info[name])
輸出結果：
['joey']
```

由上面代碼就可以看到，即便我現在使用切片，但後續維護的人就會看到我建立的切片變數name，就可以了解我這邊是想取得姓名資訊了。

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
text1 = '測試'
print(len(text1))
輸出結果：
6
# 原因在於其計算該字串的位元組序列長度，而'測試'這兩個字元以UTF-8編碼後，會使用6個位元組。

#Python3
text2 = '測試'
print(len(text2))
輸出結果：
2
# Python3對於unicode編碼就有較好的支援

#Python2
text3 = u'測試'
print(len(text3))
輸出結果：
2

#Python3
# 亦可使用bytes()方法來用位元組序列代表該字串。
print(len(bytes('測試','utf-8')))
輸出結果：
6
```

## 字串常用方法

| function | description |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| str.find\(sub,start,end\) | 從str字串的start位置到end位置中找到目標字串sub第一次出現的位置，若找不到會回傳-1。 |
| str.rfind\(sub,start,end\) | 與上相同，但會從字串的右邊開始找。 |
| str.index\(sub,start,end\) | 與find作用相同，但若找不到會出現錯誤並終止程式。 |
| str.rindex\(sub,start,end\) | 與上相同，但會從字串的右邊開始找。 |
| str.count\(sub,start,end\) | 從str字串的start位置到end位置計算目標字串sub的出現次數。 |
| str.replace\(old,new,count\) | 將str字串的old子字串以new字串取代，但目標取代字串可能會出現很多次，因此count為指定要取代幾次。 |
| str.startswith\(prefix,start,end\) | 查看從str字串的start位置到end位置是否是以prefix子字串開頭。 |
| str.endswith\(suffix,start,end\) | 查看從str字串的start位置到end位置是否是以suffix子字串結尾。 |
| str.split\(sep = None, maxsplit = -1\) | 將str字串以sep進行切割，預設為空白。maxsplit數是指定最多要切幾次，預設為全部切完。 |
| str.joint\(iterable\) | 將可迭代對象iterable以str字串將其中各元素進行連接，輸出連接後的字串。 |
| str.capitalize\(\) | 將字串str的首字轉換為大寫。 |
| str.lower\(\) | 將字串str全轉換為小寫。 |
| str.upper\(\) | 將字串str全轉換為大寫。 |
| str.title\(\) | 將字串str中的每個詞的首字轉換為大寫。 |
| str.islower\(\) | 判斷是否所有字元皆是小寫。 |
| str.isupper\(\) | 判斷是否所有字元皆是大寫。 |
| str.istitle\(\) | 判斷字串str的每個詞的首字是否皆為大寫。 |

字串也有提供一些格式對齊的方法，整理如下表

| function | description |
| --- | --- | --- | --- | --- | --- | --- | --- |
| str.center\(width,fillchar\) | 將str字串的總長度限制為width長度+1，其他非str字串之處補上fillchar，將str字串置中，fillchar預設為空白。 |
| str.ljust\(width,fillchar\) | 與上相同，但是是將str字串靠左。 |
| str.rjust\(width,fillchar\) | 與上相同，但是是將str字串靠右。 |
| str.zfill\(wdith\) | 將字串str的左側補上0，而總長度為width+1。 |
| str.expandtabs\(tabsize\) | 將字串str中的tab轉換為tabsize長度的空白。 |
| str.partition\(sep\) | 將字串str切割為sep前、sep、sep後。 |
| str.splitlines\(keepends = False\) | 將字串str以\n換行符號進行切割，以串列輸出。當keepends設為True時，則保留換行符號。 |

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

## 逃脫字元

若想表達一些特殊的字元時，可透過反斜線\來表示逃脫字元，下表為常用的逃脫字元。

| 字元 | 說明 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| \ | 續行號 |
| \\ | 倒斜線 |
| \' | 單引號 |
| \" | 雙引號 |
| \t | Tab鍵 |
| \n | 換行 |
| \a | 響鈴 |
| \b | 退一格 |
| \r | 游標返回 |

