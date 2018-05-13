# 元組\(Tuple\)

## 元組宣告

元組宣告方式有兩種：

```text
>>> t1 = tuple('a')
>>> type(t1)
<class 'tuple'>

>>> t2 = ('a',123,tuple('a'))
>>> type(t2)
<class 'tuple'>
```

由上述例子可以看到元組可以容納好幾個元素，且每個元素的類型可不同。

> 當使用\( \)來宣告元組時，當僅宣告空元組或一個元組時需注意：

```text
>>> t3 = ()
>>> type(t3)
<class 'tuple'>
#宣告空元組

>>> t4 = (20,)
>>> type(t4)
<class 'tuple'>
#當要宣告一個元組時，需在元素後加上逗點，否則會變為宣告數值，如下例

>>> t5 = (20)
>>> type(t5)
<class 'int'>
```

## 操作元組

### Slice\(切片\)

與字串一樣，元組亦可透過Slice\(切片\)來取得其中的值。

```text
>>> t6 = (1,'Joey',3,4,5,'XDXD',7,8,9)
>>> print(t6[2:5])
(3,4,5)
```

同時，元組亦為不可變\(Immutable\)的資料型態。

```text
>>> t7 = (1,'Joey',3,4,5,'XDXD',7,8,9)
>>> t7[3] = 2
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment

# 由上例即可發現，元組是不容許被變更其內元素值的。
```

### 元組增添

雖然元組內容是不可變更的，但我們可以新增元素。

```text
>>> t8 = (1,'Joey',3,4,5,'XDXD',7,8,9)
>>> t8+(10,11,12)
(1,'Joey',3,4,5,'XDXD',7,8,9,10,11,12)

>>> t8*2
(1,'Joey',3,4,5,'XDXD',7,8,9,10,11,12,1,'Joey',3,4,5,'XDXD',7,8,9,10,11,12)
```

