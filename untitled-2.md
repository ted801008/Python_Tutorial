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
```

> Note：字典\(Dictionary\)的鍵值是不可變\(Immutable\)的，且不得重複。

## 字典\(Dictionary\)操作

字典屬於可變\(mutable\)的資料型態，想要取得特定值，僅需透過其相應的鍵值即可取得。

```text
>>> d5 = {"a":1,"b":2,"c":3}
>>> d5["a"] = 0
>>> print(d5)
{"a":0,"b":2,"c":3}
#由上例可看到我們是可以對字典的值進行變更的，另外取得特定值的方式如第二行，是使用對應的鍵值取得的。
```

