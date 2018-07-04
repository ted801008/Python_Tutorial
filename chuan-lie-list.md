# 串列\(List\)

## 串列\(List\)宣告

串列\(List\)在Python中是最常被使用到的資料型態，其可容納各種型態的數據，並可進行迭代操作。  
宣告的方式非常簡單，如下：

```text
l1 = [1,2,'XD']
print(l1)
輸出結果：
[1,2,'XD']

l2 = list((1,2,'XD'))
l3 = list({1,2,'XD'})
l4 = list((10,))
print(l2,l3,l4)
輸出結果：
[1,2,'XD'] [1,2,'XD'] [10]
# list()函式傳入值可為其他數據形態

l5 = []
l6 = list()
# 以上為宣告空串列的方式
```

除此之外，在這邊也要介紹一些比較常用的方法，如下：

| function | description |
| --- | --- | --- | --- | --- | --- |
| len\(x\) | 取得長度 |
| max\(x\) | 取得x中最大的元素 |
| min\(x\) | 取得x中最小的元素 |
| x.count\(y\) | 物件方法，從x串列中計算元素y出現的次數 |
| x.index\(y\) | 物件方法，從x串列中找出元素y第一次出現的位置索引 |

```text
a = [1,2,3,1,2,1]
print(len(a))
print(max(a))
print(min(a))
print(a.count(1))
print(a.index(1))

輸出結果：
6
3
1
3
0
```

## 串列\(List\)操作

### 新增元素

```text
l7 = [1,2,3]
l7.append([4,5])
print(l7)
輸出結果：
[1,2,3,[4,5]]
# append()方法是增添元素至尾端，如此例就是將傳入的串列作為新元素增添至尾端。

l7.extend([6,7])
print(l7)
輸出結果：
[1,2,3,[4,5],6,7]
# extend是將輸入值拆分出來後再分別增添至該列表的尾端，如此例就是將傳入的串列拆分出多個元素增添至尾端，注意這點是與append()方法不同的。

l7.insert(1,8)
print(l7)
輸出結果：
[1,8,2,3,[4,5],6,7]
# insert()方法是指定特定索引值，並在該索引位置中插入指定值。

l8 = ['q','w','e']
print(l7+l8)
輸出結果：
[1,8,2,3,[4,5],6,7,'q','w','e']
# 串列可用加號來拼接其他串列

l8*2
print(l8)
輸出結果：
['q','w','e','q','w','e']
# 使用*可以重複該串列元素。
```

### 刪除元素

```text
l9 = [1,2,3,4,5]
popValue = l9.pop()
print(popValue,l9)
輸出結果：
5 [1,2,3,4]
# pop()函式是會回傳被刪除的值的，而被刪除的會是原始串列中的最後一個元素。

l10 = [1,1,1,2,2]
l10.remove(1)
print(l10)
輸出結果：
[1,1,2,2]
# remove()函式會刪除指定值，但若有多個指定值於串列中，僅會刪除第一個發現的指定值。
```

### Slice\(切片\)

串列\(List\)同樣也可以被Slice\(切片\)來取得特定位置的元素。

```text
l11 = [1,2,3,4,5,6,7,8,9]
print(l11[0:2]) 
輸出結果：
[1,2]

print(l11[:])
輸出結果：
[1,2,3,4,5,6,7,8,9]

print(l11[6:-1])
輸出結果：
[7,8]

print(l11[2:7:2])
輸出結果：
[3,5,7]

print(l11[::-1])
輸出結果：
[9,8,7,6,5,4,3,2,1]
```

> 串列\(List\)是一種可變的\(Mutable\)的數據形態，可改變其內的元素。

```text
l12 = [1,2,3,4,5]
l12[0] = 0
print(l12)
輸出結果：
[0,2,3,4,5]

l12[2:4] = []
print(l12)
輸出結果：
[0,2,5]
# 將索引2、3的元素設為空。
```

### 組合/拆解

串列可將其內元素以特定值進行拼接為字串，另外亦可將字串以特定值作為基準進行切割成串列。

```text
list2String = ['I','am','Joey']
print(' '.join(list2String))
輸出結果：
I am Joey
# 將串列元素以空格進行拼接。

string2List = "I am Joey"
print(string2List.split(' '))
輸出結果：
['I','am','Joey']
# 以空格作為基準進行切割，並儲存於串列。
```

> 注意：join\(\)方法所傳入的是可迭代的資料型態便皆可處理，而非僅限於串列。

### 排序

實現串列排序有兩種方法  
1. 內建函數sorted\(\)

```text
sorted(iterable,key = None, reverse = False)

iterable為欲被排序的資料
key為排序的基準，預設為無
reverse預設為False，代表遞增排序。若要實現遞減僅須將其設為True。
```

> 事實上，sorted\(\)方法可實施的對象僅要是能夠迭代的皆可，如元組、字串等等

2. 串列物件方法sort\(\)

```text
list.sort(key = None, reverse = False)
```

```text
a = [1,3,2,6,4]
print(sorted(a))
print(a)
print("-"*10)
a.sort(reverse = True)
print(a)

輸出結果：
[1, 2, 3, 4, 6]
[1, 3, 2, 6, 4]
--------------------
[6, 4, 3, 2, 1]
```

由上述代碼可以看出：  
內建函數sorted\(\)採用的是複製排序\(copied sorting\)，排序後原串列並不會改變。  
串列物件函數sort\(\)採用的是就地排序\(in-place sorting\)，排序後原串列便改變了。

## 串列方法

串列有許多物件方法，整理如下表：

| function | description |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| list.append\(x\) | 將x元素加至list的最後 |
| list.extend\(t\) | 將可迭代物件t拆分後分別加至list |
| list.insert\(i,x\) | 將元素x插入至list的位置i |
| list.remove\(x\) | 將一個元素x從list中刪除，與del s\[i\]相同 |
| list.pop\(i\) | 將位置i的元素刪除並回傳，若未給予則預設刪除最後一個 |
| list.clear\(\) | 將list清空，與del list\[:\] 相同 |
| list.reverse\(\) | 將list倒轉 |
| list.count\(x\) | 計算元素x在list出現的次數 |
| list.index\(x\) | 回傳元素x在串列第一次出現的位置 |

## 串列生成式

Python有提供生成式\(Comprehension\)方法，他可將多個迭代器合在一起，再以for迴圈實現。而也因串列是一種較為自由的資料儲存形式，因此Python也有特別為其提供特別的方法-串列生成式\(List Comprehension\)。  
具體實現的如下代碼

```text
[item for item in iterable]
[item for item in iterable if item condition]
```

```text
a = [i for i in range(10)]
b = [i**2 for i in range(10) if i%2==0]
print(a)
print(b)
輸出結果：
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
[0, 4, 16, 36, 64]
```

看起來跟過去我們用if-else、迴圈等來建立目標串列差不多啊，那為何我們還需要用串列生成式呢？  
原因為較為效率、代碼較簡潔。

```text
score = [[65,77,84],[46,99,27,50],[88,87,65,67,68]]
average = [sum(i)/len(i) for i in score]
print(average)
輸出結果：
[75.33333333333333, 55.5, 75.0]
# 如此可以一行解決

average = []
for i in score:
    average.append(sum(i)/len(i))
print(average)
輸出結果：
[75.33333333333333, 55.5, 75.0]
# 這是不使用串列生成式的做法，達到的效果皆是一樣的
```

```text
# 亦可搭配格式化字串
name = ['joey','kobe','michael','lebron']
print('\n'.join(["{0:9s}{1:9d}".format(item,len(item)) for item in name]))
輸出結果：
joey             4 
kobe             4 
michael          7 
lebron           6
```

#### 兩個串列併以串列生成式

```text
name = ['joey','kobe']
cake = ['chocolate','strawberry','banana','watermelon']
allocate = [(i,j) for i in name for j in cake]
print(allocate)
輸出結果：
[('joey', 'chocolate'), ('joey', 'strawberry'), ('joey', 'banana'), ('joey', 'watermelon'), ('kobe', 'chocolate'), ('kobe', 'strawberry'), ('kobe', 'banana'), ('kobe', 'watermelon')]
```

## 二維串列

所謂的二維串列指的就是串列中還有其他串列，不多說，直接帶例子

```text
a = [[11,12,13],[21,22,23],[31,32,33]]
# a即是一個二維串列
```

上述的二維串列其實就是等同於下表

|  | 欄\[0\] | 欄\[1\] | 欄\[2\] |
| --- | --- | --- | --- |
| 列\[0\] | 11 | 12 | 13 |
| 列\[1\] | 21 | 22 | 23 |
| 列\[2\] | 31 | 32 | 33 |

```text
list[列索引][欄索引]
```

```text
# 取得第2列第0個元素
a[2][0]
```

### 讀取二維串列

讀取方式非常簡單，只要用兩層迴圈即可

```text
a = [[11,12,13],[21,22,23],[31,32,33]]
for index,i in enumerate(a):
    print('第',index,'列')
    for j in i:
        print(j,end = ' ')
    print()
輸出結果：
第 0 列
11 12 13

第 1 列
21 22 23

第 2 列
31 32 33


```

亦可使用串列生成式來處理二維串列

```text
a = [[i for i in range(1,x+1)] for x in range(0,4)]
print(a)
輸出結果：
[[], [1], [1, 2], [1, 2, 3]]

b = [[j, i] for i in a for j in i]

```

## zip\(\)壓縮

透過內建函數zip\(\)能將可迭代的資料進行壓縮或解壓縮，產生一個迭代器，會由左至右。

```text
zip(*iterable)
```

```text
a = [12,33,56,78]
b = ['aa','bb']
for i in zip(a,b):
    print(i)
輸出結果：
(12, 'aa')
(33, 'bb')

```

## 複製

Python萬物皆物件，只有物件\(Object\)和物件參照\(Object reference\)，所以在複製物件與物件參照並進行操作時也會可能產生不同的結果。  
以此為基準，Python的複製可分為  
1. 淺複製\(Shallow copy\)：只複製物件參照，而不複製物件本身。  
2. 深複製\(Deep copy\)：複製物件本身，需透過導入copy模組的deepcopy執行。  
  
而其實在變數章節就有提到=有賦值的效果

```text
a = [1,2,3]
b = a
# 上面的代碼其實就是將物件參照a指向一連串的數值，b指向物件參照a

b[0] = 2
a[2] = 10
輸出結果：
[2, 2, 10]
[2, 2, 10]

# 所以當我們改變其中一個值時，其他其實也會被改變
```

### 淺複製

對於串列物件來說，達到淺複製的方法有：  
1. \*運算子  
2. 切片slice  
3. 串列物件方法copy\(\)方法，等同於切片的\[:\]

#### \*運算子

```text
a = [1,2,3]
#變數a指向值為1,2,3的物件

b = a*2
print(b)
輸出結果：
[1, 2, 3, 1, 2, 3]

# 上面為使用*運算子的結果，其原理其實就是將串列b的索引0和3指向原串列a的索引0的位置，以此類推。
```

#### 切片

切片的原理並不會複製元素，而是建立一個新串列，讓新串列的索引參照原串列的每個元素。

```text
a = [[i,j] for i in range(3) for j in range(5,2,-1)]
b = a[0:4]
print(a)
print(b)
輸出結果：
[[0, 5], [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]
[[0, 5], [0, 4], [0, 3], [1, 5]]

a[0][1] = 10
print(a)
print(b)
輸出結果：
[[0, 10], [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]
[[0, 10], [0, 4], [0, 3], [1, 5]]
# 改變一個值，皆會改變

b[0][1] = 5
print(a)
print(b)
輸出結果：
[[0, 5], [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]
[[0, 5], [0, 4], [0, 3], [1, 5]]
# 改變b也一樣

b[0] = 10
print(a)
print(b)
輸出結果：
[10, [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]
[[0, 5], [0, 4], [0, 3], [1, 5]]

#因為直接塞給他新的物件，所以就不會影響了
```

#### 物件方法copy\(\)

```text
a = [[i,j] for i in range(3) for j in range(5,2,-1)]
b = a.copy()
a[0][1] = 10
print(a)
print(b)
輸出結果：
[[0, 10], [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]
[[0, 10], [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]

#也是採用淺複製
```

#### copy\(\)模組

```text
import copy
a = [[i,j] for i in range(3) for j in range(5,2,-1)]
b = copy.copy(a)
a[0][1] = 10
print(a)
print(b)
輸出結果：
[[0, 10], [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]
[[0, 10], [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]

#也是採用淺複製
```

### 深複製

深複製會直接複製物件本身，實現的方式是透過copy模組的deepcopy\(\)方法

```text
import copy
a = [[i,j] for i in range(3) for j in range(5,2,-1)]
b = copy.deepcopy(a)
a[0][1] = 10
print(a)
print(b)
輸出結果：
[[0, 10], [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]
[[0, 5], [0, 4], [0, 3], [1, 5], [1, 4], [1, 3], [2, 5], [2, 4], [2, 3]]

#其他不會受到改變
```

