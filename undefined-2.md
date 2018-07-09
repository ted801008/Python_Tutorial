# 遞迴

遞迴\(Recursive\)的概念就是..利用函式不斷地呼叫自己直到目標完成。但要注意的是，使用遞迴會很耗資源，因此要審慎使用。

在思考遞迴時，一般要考慮兩種狀況：  
1. 基本狀況\(Base case\)：在此狀況發生時，終止遞迴。  
2. 遞迴狀況\(Recursive base\)：在此狀況發生時，呼叫自己。

以下幾個例子，可以幫助我們了解一下遞迴在幹嘛。

第一個例子： 階層  
階層! 相信大家都有學過，如5! = 5\*4\*3\*2\*1  
以迴圈的方式，很直觀，如下：

```text
def fact(x):
    result = 1
    for i in range(x,0,-1):
        result*=i
    return result
print(fact(5))
執行結果：
120
```

而以遞迴的方式則如下，思考為5! = 5\*4! = 5\*4\*3! = ...：

```text
def fact(x):
    if(x<=1):
        # Base case，因為0! = 1! = 1
        return 1
    else:
        # Recursive case
        return x*fact(x-1)

print(fact(5))
執行結果：
120
```



第二個例子則為鼎鼎大名的費伯納西數列，此數列在0與1後，其後數便會由前兩個數相加而成：0,1,1,2,3,5,8...

以迴圈方式進行：

```text
def fib(x):
    result = []
    a,b = 0,1
    while(b<x):
        result.append(b)
        a,b = b,a+b
    return result
print(fib(10))

執行結果：
[1, 1, 2, 3, 5, 8]
```

以遞迴方式進行：

```text
def fib(x):
    if(x<=1):
        # Base case，因為第0個與第一個數並不是由前兩個數相加而成，而分別為0與1
        return x
    else:
        # Recursive case
        return fib(x-1)+fib(x-2)

result = []
for i in range(10):
    result.append(fib(i))
print(result)
執行結果：
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

