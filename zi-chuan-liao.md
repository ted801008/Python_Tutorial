# 字串資料

## 字串宣告

在Python中，字串資料可由雙引號或單引號宣告，如下

```
>>> "Hello World"
'Hello World'
>>> 'Hello World'
'Hello World'
#兩者型態皆為str
```

> Note：若以雙引號建立字串，而內容亦有雙引號時，則必須在內容中的雙引號前加上\進行跳脫\(escape\)處理，亦此類推，單引號亦同樣處理之。  
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
>>> a = "Hello World"

#取第一個字
>>> a[0]
'H'

#取第3到第7個字
>>> a[2:7]
'llo W'
#這邊要注意的點是
# 1. :代表著從那個索引到哪個索引，這邊例子代表從第2個索引到第6個索引。
# 2. 最後的索引值並不會被索引到，因此這邊例子的結束索引值為7，但實際上僅會索引到6。
```

