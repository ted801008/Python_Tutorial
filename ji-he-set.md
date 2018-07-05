# 集合\(Set\)

集合屬於一種無序資料型別，其會直接刪除重複的項目，因此不支援索引、切片等運算。Python的集合\(set\)提供兩個類別：set與fronzenset。

| set | fronzenset |
| --- | --- | --- | --- | --- |
| 可變Mutable | 不可變Immutable，大小為固定的 |
| 無雜湊 | 可雜湊  |
| 不能作為字典的key | 能作為字典的key |
| 不可當作另一個集合的元素 | 可當作另一個集合的元素 |

## 集合\(Set\)宣告

集合\(Set\)一個無序、不重複的序列，其宣告方式有兩種：

```text
s1 = {1,2,3}
print(type(s1))
輸出結果：
<class 'set'>

s2 = set([1,2,3,34,5])
print(type(s1))
輸出結果：
<class 'set'>

a = {1,'kobe',[1,2,3]}
輸出結果：
TypeError: unhashable type: 'list'
# 因為list為可變的Mutable，因此不能作為集合的元素。
```

> Note：  
> 1. 以set\(\)函式創建集合時，要注意其僅能輸入一個值，你可傳入一個包含多個值的元組、字串或串列等等，創建出的集合對象會自動將重複的元素值去掉留下無序的不重複元素。  
> 2. 使用{ }宣告集合時，要注意當你想宣告一個空集合時，不能使用，因為會變成宣告字典。若你想要宣告空集合，需使用set\(\)

```text
s3 = set((1,2,3,34,5))
print(s3)
輸出結果：
{1, 2, 3, 34, 5}

s4 = {}
print(type(s4))
輸出結果：
<class 'dict'>
# 並非集合型態，而是字典型態。

s5 = set()
print(type(s5))
輸出結果：
<class 'set'>
# 使用set()函式才可創建空集合。
```

## 集合\(Set\)操作

集合\(Set\)可進行集合運算，包括聯集、交集、差集等等。

| function | description |
| --- | --- | --- | --- | --- |
| \| | 聯集 |
| & | 交集 |
| - | 差集，可看作兩集合相減 |
| ^ | XOR，相對差集，可看做兩集合相減再做聯集 |

```text
s6 = set('abcdefg')
s7 = {'c','d','e'}

print(s6 - s7)
輸出結果：
{'f', 'g', 'b', 'a'}
# 差集

print(s6 | s7)
輸出結果：
{'d', 'f', 'a', 'c', 'b', 'g', 'e'}
# 聯集

print(s6 & s7)
輸出結果：
{'d', 'e', 'c'}
# 交集

print(s6 ^ s7)
輸出結果：
{'f', 'a', 'b', 'g'}
# s6集合與s7集合中不同時存在的元素
```

## 集合\(Set\)內建函式

集合\(Set\)有提供許多物件內建函式，下表為一些新增刪除元素的方法：

| function | description |
| --- | --- | --- | --- | --- | --- | --- |
| set.add\(x\) | 將元素x加入集合 |
| set.clear\(\) | 清空集合 |
| set.copy\(\) |  淺複製集合 |
| set.discard\(x\) | 從集合中去除元素x，若無元素x不會出現錯誤。 |
| set.pop\(\) | 從集合中隨機去除元素並回傳，但若該集合為空則會出現錯誤。 |
| set.remove\(x\) | 從集合中移除元素x，但若無元素x則會出現錯誤。 |



而下表則提供一些集合運算的方法

| function | description |
| --- | --- | --- | --- | --- | --- | --- | --- |
| set.union\(iterable,...\) | 集合會與傳入的可迭代對象進行「OR運算」，並回傳運算後之新集合。 |
| set.intersection\(iterable,...\) | 集合會與傳入的可迭代對象進行「AND運算」，並回傳運算後之新集合。 |
| set.difference\(iterable,...\) | 集合會與傳入的可迭代對象進行「差集運算」，並回傳運算後之新集合。 |
| set.symmetric\_difference\(iterable\) | 集合會與傳入的可迭代對象進行「XOR運算」，並回傳運算後新集合。 |
| set.update\(iterable,...\) | 將傳入可迭代對象加入集合，等同於set \|= iterable運算，就地更改 |
| set.intersection\_update\(iterable,...\) | set &= iterable，就地更改 |
| set.symmetric\_difference\_update\(iterable,...\) | set ^= iterable，就地更改 |

  
集合可作為另個集合的父集合或子集合，對此Python亦有提供一些函式，如下：

| function | description |
| --- | --- | --- | --- | --- | --- |
| set &gt; otherset | 檢測集合set是否為otherset的父集合 |
| set &lt; otherset | 檢測集合set是否為otherset的子集合 |
| set.issuperset\(otherset\) | 檢測集合set是否為otherset的父集合，等同於 set &gt;= otherset |
| set.issubset\(otherset\) | 檢測集合set是否為otherset的子集合，等同於  set &lt;= otherset |
| set.isdisjoint\(otherset\) | set與otherset若無共同元素時則回傳True，反之則回傳False。 |

## 集合生成式

Python亦有為集合提供集合生成式，實作方式跟串列生成式等其實大同小異，但要注意的是集合是無序的，所以有時可以搭配字典、串列、元組來產生字典生成式。

```text
{運算式 for item in iterable}
{運算式 for item in iterable if 條件式}
```

