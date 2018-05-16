# 條件控制

## if...else

If...else條件控制句在程式語言中是一個非常重要的一部分，使用方法非常簡單。  
由下例來看，此程式碼聲明當a變數的值為0時就打印出ok的字串，若為1則打印出no的字串，如果不是0也不是1的話，那就打印出haha的字串，非常的直觀。

```text
a = 0
if(a==0):
    print('ok')
elif(a==1):
    print('no')
else:
    print('haha')
輸出結果：
ok
```

在數值的章節有提到，在Python中只要是空的數據形態都是為False，依此邏輯亦可將程式碼寫成如下：

```text
a = {}
if a:
    print('ok')
else:
    print('no')

輸出結果：
no
```

## Pass

Pass語句在Python中是代表不會做任何事的表示，以確保程式碼結構的完整性。

```text
if 1==True:
    print('ok')
else:

輸出結果：
SyntaxError: unexpected EOF while parsing

# 如果想寫不做任何事的程式碼，直接留空白是不允許的。

if 1==True:
    print('ok')
else:
    pass

輸出結果：
ok

# 使用pass語句即可表達不做任何事。
```

