# 迴圈

## 迴圈

循環在程式語言也是一個非常重要而且非常常用的部分，而這節就要來揭開他的神秘面紗。

### For Loop

有許多語法能達到迴圈的效果，首先先讓我們來討論第一種：for loop。  
我們可以使用for語法來逐一取得數據中的各元素，

```text
for i in [1,2,3]:
    print(i)
輸出結果：
1
2
3
# 可逐一取得串列中的各元素。

for i in {'a':1,'b':2}:
    print(i)
輸出結果：
a
b
# 將迴圈使用於字典中，會逐一取得該字典的鍵值。

a = {'a':1,'b':2}
for i,j in a.items():
    print(str(i)+":"+str(j))
輸出結果：
a:1
b:2
# 使用迴圈逐次的取得鍵值對。

for i in 'abc':
    print(i)
輸出結果：
a
b
c
# 亦可應用於字串中。

for i in range(10):
    print(i,end=',')
輸出結果：
0,1,2,3,4,5,6,7,8,9,
# range()函式可以生成0~指定數-1的數字，如此就可以透過range()函式來選擇要迴圈幾次了。

print(list(range(10)))
輸出結果：
[0,1,2,3,4,5,6,7,8,9]
# 將這些數字轉換為串列形式。
```

更進一步，我們還可else判斷句加在For迴圈中，使用方法如下。

```text
for i in range(10):
    print(i)
else:
    print('END')
輸出結果：
0
1
2
3
4
END
# 由上例可看出，當迴圈結束後便會執行else內的程式碼。
```

### While

第二種迴圈方式是使用while，其意義就是當指定的條件滿足時便會不斷地執行其內的程式碼。

```text
a = 10
sum = 0
while(a>0):
    sum+=a
    a-=1
print(sum)
輸出結果：
55
# 上述代碼的意思是當a大於0時便會執行其內的程式碼，當a不大於0時，便會終止，停止迴圈。
```

同樣地，我們也可將else 加在While迴圈中，使用方法如下。

```text
a = 0
while(a<3):
    print(a)
    a+=1
else:
    print('END')
輸出結果：
0
1
2
END
# 上例概念就是當a小於3時，執行其內程式碼，否則打印出END。
```

### break

當你想強制跳出迴圈時，只需宣告break。

```text
for i in range(100):
    if(i==1):
        print('END')
        break
    else:
        print(i)
輸出結果：
0
END
# 由上例可看到，並不會迴圈100次，而是當i等於1時即跳出迴圈，原因就在於宣告了break。
```

### continue

當你想跳過此次迴圈，只需宣告Continue。

```text
for i in range(5):
    if(i==1):
        print('PASS')
        continue
    print(i)
輸出結果：
0
PASS
2
3
4
# 由上例可以看到，當迴圈到i等於1時，就會打印出PASS字串並跳過此次迴圈。
```

### Range\(\)函數

在上面幾個例子中，我們有使用到一個很好用的函式--Range\(\)，其可以自動遍歷順序的數字序列，函式的詳細細節如下。

```text
range(start,end,step)
```

start指的是起始數字。  
end指的是結束數字，注意真正結束的數字為指定數-1。  
step指的是每次迴圈的步長。

```text
for i in range(1,9,2):
    print(i)
輸出結果：
1
3
5
7

for i in range(2,5):
    print(i)
輸出結果：
2
3
4

for i in range(3):
    print(i)
輸出結果：
0
1
2
```

由上面幾個代碼可以看出，當不指定步長時，預設為1。  
而當僅輸入一個數字時，則為指定結束數字，起始數字預設為0，步長預設為1。

### enumerate\(\)方法

當我們在對可迭代序列資料\(list, tuple, string等\)進行迭代時，若想對個別元素建立對應索引時，就可使用到enumerate\(\)方法。

```text
enumerate(iterable, start = 0)
```

```text
a = [1,2,3,'joey']
for i,j in enumerate(a,1):
    print(i,j)
輸出結果：
1 1
2 2
3 3
4 joey
```

