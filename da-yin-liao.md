# 打印資料

## Hello World!

學習程式語言一開始不免俗就是要來Hello World一下囉，基本上所有程式人一開始所學的就是要如何在結果輸出顯示Hello World。  
方法非常的簡單，如下：

```text
>>> 'Hello World'
```

如此一來，就可顯示出Hello World啦～  
其中用單引號或雙引號所圍住的內容會被以字串型態被Python建立，因此我們的'Hello World'物件的型態也會是字串囉。

## 打印

在Python中，將指定內容顯示在螢幕上的方法有以下幾種：  
1. sys.stdout.write\(\)：將指定內容打印於螢幕中，上面的Hello World的程式碼即是透過此方法來顯示出Hello World的。  
2. print\(\)：此方法其實是調動sys.stdout.write\(\)方法，並在指定內容最後加上換行符號'\n'。

print\(\)的函式架構為如下，可接收多個數值，而sep的是各數值間是以何種內容連結，end的則是顯示內容的最後以何種內容結束。

```text
print(value1, value2, value3, ..., sep=' ', end='\n', file=sys.stdout)
```

### 取得用戶所輸入的內容

有時我們需要取得用戶所輸入的內容並加以處理\(如帳號密碼等等\)，而當然用戶不會知道需要輸入什麼內容，因此需要給予提示訊息，這一切僅需使用input\(\)函式即可完成。

```text
# 以下程式代碼會先在螢幕中打印出「請輸入您的姓名」的內容，並等待接收用戶所輸入的資訊。
>>> input('請輸入您的姓名')
```

除此之外，你亦可使用sys.sdin來取得用戶所輸入的內容，如下：

```text
>>> import sys
>>> sys.stdin.readline()
Hello World
'Hello World\n'
```

可以發現上面的程式碼輸出最後是有換行符號\n的，這也是其與input\(\)函式的差別，input\(\)函式的輸出最後並無換行符號。

### 將打印內容轉至檔案中

我們可以將目標文檔的引用賦給sys.stdout，如此print\(\)函式所輸出的內容則會直接寫至該目標文檔中。

```text
>>> import sys
#下段程式碼為建立可寫入資料的檔案
>>> outputLog = open('outputLog','w')
>>> sys.sdout = outputLog
>>> print('Hello World')
#因此print()函式所輸出的內容並不會顯示於螢幕上，而是寫至目標文檔中。
```

此時，只要調動任何print\(\)函式，則都會將指定內容寫至目標文檔中。因此，若還想要輸出一些不想寫至檔案而顯示於螢幕上的內容時，最好將原始的console引用保存下來，當在途中要顯示於螢幕上時，即可恢復，如下。

```text
>>> __console__ = sys.stdout
#...
#輸出導向至目標檔案
#...
>>> sys.stdout = __console__
#此時已重新回復輸出預設
```

