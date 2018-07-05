# 字典\(Dictionary\)

字典屬於一種「映射型別」\(Mapping Types\)，Python有提供兩種映射型別：  
1. 有序映射型別：collections模組的OrderedDict，是dict的子類別，因此一樣有字 典的屬性與方法。  
  
2. 無序映射型別：即字典\(Dictionary\)，為內建物件。另一種則是collections模組的defaultdict，同樣是dict的子類別，但可以設置預設值。  
  
字典屬於可變\(Mutable\)物件，且支援迭代，其主要概念即是「鍵-值」對\(key-value pairs\)，可透過「鍵」來取得對應的「值」。  
  
另外，由於字典屬於無序，並無索引的概念，因此並不能進行切片\(Slice\)運算。

## 字典\(Dictionary\)宣告

字典\(Dictionary\)是一個擁有鍵-值對的容器類型，其內元素可透過相應的鍵取得。  
字典的宣告方式有兩種：

#### 大括號

```text
{key1:value1,key2:value2,...}
```

key為鍵，value為相應值。  
鍵\(key\)並不具有順序且不可變，所能使用的資料型別可以是整數、浮點數、字串、元組、frozenset，其他如字典、串列、集合皆不能作為鍵。  
值\(value\)可以是任何資料型別的物件，如串列、字典、數值甚至是函式。

```text
d1 = {'a':1,'b':2}
print(type(d1))
輸出結果：
<class 'dict'>

d2 = {} #建立空字典
print(type(d2))
輸出結果：
<class 'dict'>
```

#### dict\(\)函式

```text
dict(**kwarg)
dict(mapping,**kwarg)
dict(iterable,**kwarg)
```

kwarg代表關鍵字引數，以「變數=值」來指定鍵-值  
mapping為映射物件  
iterable為可迭代者

```text
d2 = dict([('a',1),('b',2)]) #使用可迭代者建立
print(type(d2))
輸出結果：
<class 'dict'>
# 同樣地，使用dict()函式僅接受一個傳入值，因此需使用一個擁有鍵值對的序列。

d3 = dict(a=1,b=2) #使用關鍵字引數建立
print(type(d3))
輸出結果：
<class 'dict'>
# 或使用以上的方式使用dict()函式宣告，要注意的是關鍵字引數的指定鍵值不能是表達式，否則會出現下例宣告失敗的情形。

d4 = dict('a'=1,'b'=2)
輸出結果：
    File "<stdin>", line 1
SyntaxError: keyword can't be an expression  

d4 = dict(zip(['a','b','c'],[1,2,3])) #搭配zip()函式建立
print(d4)
輸出結果：
{'a':1,'b':2,'c':3}
# 使用兩個串列來建立字典
```

> 搭配zip\(iter1, iter2\)來建立dict時，先指定key再指定相應value。

## 字典\(Dictionary\)操作

### 改變/新增值

字典屬於可變\(Mutable\)的資料型態，想要取得特定值，僅需透過其相應的鍵值即可取得。

```text
d5 = {"a":1,"b":2,"c":3}
d5["a"] = 0
print(d5)
輸出結果：
{"a":0,"b":2,"c":3}

d5["d"] = 4
print(d5)
輸出結果：
{"a":0,"b":2,"c":3,"d":4}
```

由上例可看到我們是可以對字典的值進行變更的，取得特定值的方式如第二行，是使用對應的鍵值取得的。  
  
至於新增或改變值的方法其實是一樣的，差別只在於所使用的鍵是否存在於該字典中，若存在則會改變相應值，若不存在則新增該鍵值對。  
  
除此之外，我們亦可使用update\(\)函式來達到以上相同的效果。

```text
d6 = {"a":1,"b":2,"c":3}
d6.update({"a":0})
#or
d6.update(dict(a=0))
#or
d6.update(a=0)
print(d6)
輸出結果：
{"a":0,"b":2,"c":3}
# 更新單一值，以上幾種方法皆可進行更新。

d6.update({"a":1,"b":10})
#or
d6.update(a=1,b=10)
#or
d6.update(dict(a=1,b=10))
print(d6)
輸出結果：
{"a":1,"b":10,"c":3}
# 一次更新多值，以上幾種方法皆可進行更新。

d7 = {}
d7.update(d6)
print(d7==d6)
輸出結果：
True
# 亦可直接傳入一個字典進行更新
```

> Note：  
> 1. 字典的鍵屬於不可變\(Immutable\)的，且不可重複。  
> 2. 創建空字典的方法非常簡單，僅需打{}或dict\(\)即可。

當然，你也可以使用魔術方法\_\_setitem\_\_來增添/改變值，然而不建議使用這種方法，因為其處理速度較慢。

```text
setDict = {}
setDict.__setitem__('d',100)
print(setDict)
輸出結果：
{'d':100}
```

### 刪除值

```text
d8 = {"a":1,"b":2,"c":3}
del d8['a']
print(d8)
輸出結果：
{'b': 2, 'c': 3}
# 使用del刪除特定值

popValue = d8.pop('b')
print(popValue)
print(d8)
輸出結果：
2
{"c":3}
# 使用pop()函式會回傳被刪除的值。

d8.clear()
print(d8)
輸出結果：
{}
# 使用clear()函式，會直接清空該字典。
```

### 找不到key怎摸辦？

當我們依某特定鍵來從字典取得值時，但卻找不到時會發生什麼狀況呢？ 

```text
a = {"a":1,"b":2,"c":3}
print(a['d'])
輸出結果：
KeyError: 'd'
```

紅明顯就會出現KeyError的錯誤導致程式終止。  
很顯然，我們並不希望有這等事發生，這時候該如何防止呢？  
以下提供幾種方式：

1. 檢查字典中是否存在特定鍵

    使用成員運算子判斷。

```text
# in, not in
d9 = {"a":1,"b":2,"c":3}
print('a' in d9)
print('d' not in d9)
輸出結果：
True
True
```

    使用字典物件方法get\(\)，當找不到鍵值時會回傳None，而不會引發錯誤。

```text
#get()方法
a = {"a":1,"b":2,"c":3}
print(a.get('a'))
print(a.get('d'))
輸出結果：
1
None
```

    使用字典物件方法setdefault\(\)方法，若存在該鍵，則回傳該對應值。無該鍵時，  
    會自動新增該鍵，對應值則以None儲存。

```text
a = {"a":1,"b":2,"c":3}
print(a.setdefault('a'))
print(a.setdefault('d'))
print(a)
輸出結果：
1
None
{'a': 1, 'b': 2, 'c': 3, 'd': None}
```

### 取得所有鍵值對/鍵/值

```text
d10 = {"a":1,"b":2,"c":3}
print(d10.keys())
輸出結果：
dict_keys(['a', 'b', 'c'])
# 得到所有鍵

print(d10.values())
輸出結果：
dict_values([1, 2, 3])
# 得到所有值

print(d10.items())
輸出結果：
dict_items([('a', 1), ('b', 2), ('c', 3)])
# 得到所有鍵值對
```

## 內建函式

| function | description |
| --- | --- | --- | --- | --- | --- | --- |
| dict.get\(key,default\) | 回傳指定key的相應值，若找不到則回傳default值，預設為None  |
| dict.setdefault\(key,default\) | 回傳指定key的相應值，若找不到則新增該鍵，新增預設為default，預設為None |
| dict.pop\(key, default\) | 依鍵所對應的值作刪除並回傳，若無該鍵，則回傳None |
| dict.update\(x\) | 以新的鍵值對x來新增至字典 |
| dict.clear\(\) | 清空字典 |
| dict.copy\(\) | 以淺複製來複製字典 |

### fromkeys\(\)

fromkeys\(\)是Python字典所提供的類別方法，主要功用是先將序列型資料拆分成key，再以\[ \]運算子填入相應值。

```text
fromkeys(seq,[, value])
```

seq為傳入的序列型資料  
value為選擇性參數，若未傳入，則預設以None

```text
a = {}.fromkeys('Joey','haha')
b = {}.fromkeys([1,2,3])
print(a)
print(b)
輸出結果：
{'J': 'haha', 'o': 'haha', 'e': 'haha', 'y': 'haha'}
{1: None, 2: None, 3: None}
```

### locals\(\)

Python所提供的內建函式locals\(\)會確認目前有效範圍的區域變數，並將這些變數以字典形式回傳，變數名稱會以「鍵」儲存，變數值則會以相應「值」儲存。

```text
name = 'Joey'; age = 25; job = 'soldier'
print(locals())
輸出結果：
{'name': 'Joey', 'age': 25, 'job': 'soldier', '__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>}
```

可以看到除了我們所建立的變數外，還有許多其他內建預設的變數等等。  
  
但所回傳的變數真的太多了，若我們只想取出我們所建立的變數該如何是好呢？  
這時就得依靠format\(\)和拆解映射「\*\*」\(Mapping unpacking\)了，具體如下：

```text
name = 'Joey'; age = 25; job = 'soldier'
print("name:{name}\nage:{age}\njob:{job}".format(**locals()))
輸出結果：
name:Joey
age:25
job:soldier
```

> 「拆解映射」即是將映射型別轉換為關鍵字引數\(key=value\)形式。

## 字典生成式

生為一個常常被使用的資料型態，Python亦有為其提供生成式，稱為字典生成式\(Dictionary Comprehension\)。

大致的使用方式如下定義：

```text
{key運算式:value運算式 for key,value in iterable}
{key運算式:value運算式 for key,value in iterable if 條件式}
```

```text
a = {'a':1,'b':2,'c':3}
reverse_a = {value:key for key,value in a.items()}
print(reverse_a)
輸出結果：
{1: 'a', 2: 'b', 3: 'c'}
# 可透過字典生成式來反轉鍵-值對。

b = {key:value for key,value in enumerate(['我','喜歡','吃','飯'])}
print(b)
輸出結果：
{0: '我', 1: '喜歡', 2: '吃', 3: '飯'}
# 搭配enumerate和字典生成式建立字典
```

```text
key = ['key1','key2','key3']
value = [1,2,3]
a = {i:j for i,j in zip(key,value)}
print(a)
輸出結果：
{'key1': 1, 'key2': 2, 'key3': 3}
# 搭配zip()和字典生成式來建立字典
```

```text
grade = {'joey':54,'kobe':89,'lebron':76,'michael':66,'jane':99}
print('留下分數同時為2和3的倍數：')
print({k:v for k,v in grade.items() if(v%2==0 and v%3==0)})
輸出結果：
留下分數同時為2和3的倍數：
{'joey': 54, 'michael': 66}
# 搭配條件式
```

## collections模組

collections模組有提供許多字典的子類別的其他種類字典，這邊要介紹兩種常用的字典：預設字典\(defaultdict\)、順序字典\(OrderedDict\)。

### 預設字典\(defaultdict\)

預設字典是一種自動配鍵的字典，定義如下：

```text
defaultdict([default_factory])
```

default\_factory為預設工廠函式。  
「工廠函式」\(factory function\)指的是當函式被呼叫後，會以特定型別的物件回傳，Python的內建資料型別\(Built-in Function\)皆可視為工廠函式。

```text
import collections
a = collections.defaultdict(list) #預設以空串列儲存
a['1'] = 1
a['2'] = 2
print(a['1'])
print(a['3'])
輸出結果：
1
[]
```

### 有序字典\(OrderedDict\)

標準字典是無順序性的，有序字典\(OrderedDict\)會記住插入項目的順序。

```text
OrderedDict([items])
# items為欲插入的項目
```

```text
import collections
a = collections.OrderedDict()
a['a'] = 1
a[0] = 2
print(a)
輸出結果：
OrderedDict([('a', 1), (0, 2)])
# OrderedDict會記住插入項目的順序

b = collections.OrderedDict(zip(['a',0],[1,2]))
print(b)
輸出結果：
OrderedDict([('a', 1), (0, 2)])
#可搭配zip()函式

c = collections.OrderedDict({'a':1,0:2})
print(c)
輸出結果：
OrderedDict([('a', 1), (0, 2)])
```

#### OrderedDict內建函式

OrderedDict屬於字典的子類別，所以字典的方法函式也都可以用。而除此之外，OrdereDict還有提供其他方法，如下介紹：

| function | description |
| --- | --- | --- |
| popitem\( last = True\) | 刪除項目並回傳，若last指定為True則刪除最後一個元素\(鍵-值\);若指定為False則刪除第一個元素。 |
| move\_to\_end\(key, last = True\) | 將指定鍵值對進行移動，若last指定為True，則將其移動至最後;若指定為False，則移動至第一個。 |

```text
import collections
a = collections.OrderedDict()
a['A'] = 0
a['B'] = 1
a['C'] = 2
a['D'] = 3

a.move_to_end('A')
print(a)
輸出結果：
OrderedDict([('B', 1), ('C', 2), ('D', 3), ('A', 0)])

a.move_to_end('A',last = False)
print(a)
輸出結果：
OrderedDict([('A', 0), ('B', 1), ('C', 2), ('D', 3)])

print('刪除最後一個：',a.popitem())
print(a)
輸出結果：
刪除最後一個： ('D', 3)
OrderedDict([('A', 0), ('B', 1), ('C', 2)])

print('刪除第一個：',a.popitem(last = False))
print(a)
輸出結果：
刪除第一個： ('A', 0)
OrderedDict([('B', 1), ('C', 2)])
```

## 字典排序

字典屬於無序型資料型態，但有時我們還是希望他能夠排序一下，而所能排序的基準也有兩種選擇，分別是「鍵」與「值」。

```text
from collections import OrderedDict
a = {'Joey':65,'Kobe':88,'Jordan':76,'Lebron':90,'Jane':79}
print('以鍵排序：')
print(OrderedDict(sorted(a.items(),key = lambda item: item[0])))
輸出結果：
以鍵排序：
OrderedDict([('Jane', 79), ('Joey', 65), ('Jordan', 76), ('Kobe', 88), ('Lebron', 90)])

print('以值排序：')
print(OrderedDict(sorted(a.items(),key = lambda item: item[1])))
輸出結果：
以值排序：
OrderedDict([('Joey', 65), ('Jordan', 76), ('Jane', 79), ('Kobe', 88), ('Lebron', 90)])
```

