# 字典\(Dictionary\)

## 字典\(Dictionary\)宣告

字典\(Dictionary\)是一個擁有鍵-值對的容器類型，其內元素可透過相應的鍵取得。  
字典的宣告方式有兩種：

```text
>>> d1 = {'a':1,'b':2}
>>> print(type(d1))
<class 'dict'>

>>> d2 = dict([('a',1),('b',2)])
>>> print(type(d2))
<class 'dict'>
# 同樣地，使用dict()函式僅接受一個傳入值，因此需使用一個擁有鍵值對的序列。

>>> d3 = dict(a=1,b=2)
>>> print(type(d3))
<class 'dict'>
# 或使用以上的方式使用dict()函式宣告，要注意的是鍵值不能是表達式，否則會出現下例宣告失敗的情形。

>>> d4 = dict('a'=1,'b'=2)
    File "<stdin>", line 1
SyntaxError: keyword can't be an expression  

>>> d4 = dict(zip(['a','b','c'],[1,2,3]))
>>> print(d4)
{'a':1,'b':2,'c':3}
# 使用兩個串列來建立字典
```

> Note：字典\(Dictionary\)的鍵值是不可變\(Immutable\)的，且不得重複。

## 字典\(Dictionary\)操作

### 改變/新增值

字典屬於可變\(mutable\)的資料型態，想要取得特定值，僅需透過其相應的鍵值即可取得。

```text
>>> d5 = {"a":1,"b":2,"c":3}
>>> d5["a"] = 0
>>> print(d5)
{"a":0,"b":2,"c":3}

>>> d5["d"] = 4
>>> print(d5)
{"a":0,"b":2,"c":3,"d":4}
```

由上例可看到我們是可以對字典的值進行變更的，取得特定值的方式如第二行，是使用對應的鍵值取得的。  
  
至於新增或改變值的方法其實是一樣的，差別只在於所使用的鍵是否存在於該字典中，若存在則會改變相應值，若不存在則新增該鍵值對。  
  
除此之外，我們亦可使用update\(\)函式來達到以上相同的效果。

```text
>>> d6 = {"a":1,"b":2,"c":3}
>>> d6.update({"a":0})
#or
>>> d6.update(dict(a=0))
#or
>>> d6.update(a=0)
>>> print(d6)
{"a":0,"b":2,"c":3}
# 更新單一值

>>> d6.update({"a":1,"b":10})
#or
>>> d6.update(a=1,b=10)
#or
>>> d6.update(dict(a=1,b=10))
>>> print(d6)
{"a":1,"b":10,"c":3}
# 一次更新多值

>>> d7 = {}
>>> d7.update(d6)
>>> d7==d6
True
# 亦可直接傳入一個字典進行更新
```

> Note：  
> 1. 字典的鍵屬於不可變\(Immutable\)的，且不可重複。  
> 2. 創建空字典的方法非常簡單，僅需打{}或dict\(\)即可。

當然，你也可以使用魔術方法\_\_setitem\_\_來增添/改變值，然而不建議使用這種方法，因為其處理速度較慢。

```text
>>> setDict = {}
>>> setDict.__setitem__('d',100)
>>> print(setDict)
{'d':100}
```

### 刪除值

```text
>>> d8 = {"a":1,"b":2,"c":3}
>>> del d8['a']
>>> print(d8)
{'b': 2, 'c': 3}
# 使用del刪除特定值

>>> popValue = d8.pop('b')
>>> print(popValue)
2
>>> print(d8)
{"c":3}
# 使用pop()函式會回傳被刪除的值。

>>> d8.clear()
>>> print(d8)
{}
# 使用clear()函式，會直接清空該字典。
```

### 檢查是否存在

檢查字典中是否存在特定鍵

```text
>>> d9 = {"a":1,"b":2,"c":3}
>>> 'a' in d9
True
```

### 取得所有鍵值對/鍵/值

```text
>>> d10 = {"a":1,"b":2,"c":3}
>>> print(d10.keys())
dict_keys(['a', 'b', 'c'])
# 得到所有鍵

>>> print(d10.values())
dict_values([1, 2, 3])
# 得到所有值

>>> print(d10.items())
dict_items([('a', 1), ('b', 2), ('c', 3)])
# 得到所有鍵值對
```

