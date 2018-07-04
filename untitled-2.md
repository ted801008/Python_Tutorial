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

### 檢查是否存在

檢查字典中是否存在特定鍵

```text
d9 = {"a":1,"b":2,"c":3}
print('a' in d9)
輸出結果：
True
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

