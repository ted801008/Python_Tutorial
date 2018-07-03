# 迭代器與生成器

## 迭代器

迭代器是一個可以記住遍歷位置的複合式資料型態，其可將反覆運算容器中的不同資料。他會從容器中的第一個元素開始訪問，直到所有元素都被訪問到才結束，注意迭代器僅能前進不能倒退。  
  
在迭代器中，有兩個處理方法：iter\(\)與next\(\)，實際運作情形如下。

```text
a = [1,2,3,4]
it = iter(a)
print(next(it))
print('下一個')
print(next(it))
輸出結果：
1
下一個
2

# 由上例可以看到:
# iter()方法可以對可遍歷Object(字串、串列、集合等等)建立迭代器。
# next()方法可以輸出迭代器下一個元素。
```

## 生成器

生成器\(Generator\)是一個返回迭代器的函數，且只能用於迭代。  
  
在調用生成器運行時，每次遇到yield時函數會暫停並保留當前所有運行的訊息，並返回yield值。  
當下次執行next\(\)時，便會從當前位置繼續運行。

```text
import sys

def fibnoacci(n):
    a,b,counter = 0,1,0
    while True:
        if(counter>n):
            return
        yield a
        a,b = b,a+b
        counter+=1

f = fibnoacci(10)

while True:
    try:
        print(next(f))
    except:
        print('END')
        sys.exit()

輸出結果:
0
1
1
2
3
5
8
13
21
34
55
# 以生成器來實現費伯納希數列。
```

