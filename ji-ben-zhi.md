# 基本知識

## Basic

本節會大概講述Python的基本知識。

### 縮排

Python是使用縮排來取代其他程式語言中使用{ }區分代碼塊的，但要注意同一區塊的代碼其縮排必須一樣，如下例。

```text
if True:
    print('ok')
    print('ok2')
else:
    print('no')
    print('no2')
輸出結果：
ok
ok2
# 由上面代碼可看到，Python是使用縮排來區分代碼塊的。

if True:
   print('ok')
   print('ok2')
else:
    print('no')
   print('no2')
輸出結果：
IndentationError: unindent does not match any outer indentation level
# 上面代碼就會引發錯誤，原因是縮排不一。
```

### 註釋

註釋是一段不會被執行的語句，主要功能是說明你的程式碼，是一個很重要的功能，因為程式往往會是多個人一同維護，透過註釋可以讓其他人更容易了解你的程式，進而增加協作效率。  
  
在Python中，你可以用以下的方式達到註釋的效果。

```text
# 你好，我是註釋1
print('ok') # 你好，我是註釋2，但前面的print('ok')仍會被執行喔。

'''
多
行
註
釋
'''

"""
多
行
註
釋
2
"""
輸出結果：
ok
```

### 多行

通常，程式語句可以分行書寫，但仍會出現一些情況導致程式法太長而若塞進一行會太難看。  
但Python提供反斜線\來實現了多行書寫。

```text
print('你'+\
      '好'+\
      '阿')
輸出結果：你好阿
```

### 同行多句

若想在一句中表達多個需換行的程式，需以分號；連接。

```text
print('你好啊');print('我很好')
輸出結果：
你好阿
我很好
```



