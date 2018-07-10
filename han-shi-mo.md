# 函式庫與模組

在前面幾個章節常會用到import語句來將其他外部程式導入，進而使用他們的函式，而在這個章節中，我們就要來細細談一下這個東西。

當時間的推移，系統一定會變越來越大、越來越複雜，這時如果所有東西都參雜在一塊，肯定是慘不忍睹，可讀性非常的低且很難進行維護。

這時模組化的概念就興起了，透過將系統程式打包、分割成好幾個檔案，再透過導入的語法來進行共用，如此就可以更好地進行維護。這些分割後的檔案可能包含類別、函式等等，稱為模組\(Module\)，而將多個模組合在一起則成為了套件\(Package\)。

## 導入模組

Python的導入模組語法有幾種如下：

模組\(Module\)其實就是一個\*.py檔，可透過以下語法將模組導入進來。  
另外我們亦可透過line 2的代碼將模組導入進來並給予代稱，以方便進行處理。

```text
import module1, module2, module3, ...
import module as 別名
```

但是，某些時候模組裡的所包含的函式、類別很多，但我們可能僅需使用裡面某幾樣東西時，這時就必須仰賴下方line 1的代碼。  
而line 2則代表著將模組裡的所有東西導入。 

```text
from module import object1, object2, ...
from module import *
```

> 但要注意的是，導入整個模組代表導入所有物件，但導入的物件可能會跟編寫的程式碼可能會產生衝突，因此要審慎使用。

## 名稱空間

名稱空間\(Namespace\)，其會隨著物件產生，加入不同的命名。  
Python可透過內建函式dir\(\)函式取得。

```text
print(dir()) #找出目前範圍已定義的名稱
a = {'1':2,'2':3}
print(dir())

執行結果：
['__annotations__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__']
['__annotations__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'a']
```

> 可看到當定義變數a後，dir\(\)函式所回傳的串列就會新增a的元素。

## 使用模組

當Python直譯器讀取到import語句時，會先以該模組名稱查找內建模組，接著再去查看sys模組的path屬性來看該路徑是否已被載入。

但若同一個模組被宣告多次要被載入，並不會重複不斷載入，因為Python直譯器會先去查看該模組是否有被載入過\(sys.path\)，若找不到才會透過路徑搜尋來找到要載入的模組進行載入動作，當載入後便會將其記錄至sys.path。另一方面，Python直譯器亦會去查看所產生的名稱空間，參照每個所指向的物件。

### sys.path

一般來說，sys模組的path屬性是一個串列型態，它包含：

1. 執行該\*.py檔的所在目錄\(若為空字串，則表示當前路徑尚未加入，這時需使用Python直譯器\)來解譯檔案便會自動加入。
2. 安裝Python的預設路徑
3. Python標準函式庫

```text
import sys
print(sys.path)
['', '/anaconda3/lib/python36.zip', '/anaconda3/lib/python3.6', '/anaconda3/lib/python3.6/lib-dynload', '/anaconda3/lib/python3.6/site-packages', '/anaconda3/lib/python3.6/site-packages/aeosa', '/anaconda3/lib/python3.6/site-packages/distribute-0.7.3-py3.6.egg']
# 第一個元素為空字串，代表當前路徑尚未加入。
```

而若要手動加入新路徑，也可以透過append\(\)方法來新增路徑至sys.path，但要注意所加入的路徑必須為絕對路徑。

### reload\(\)

剛才有提到說當某模組已被載入就不會再被載入了，但若我們想進行重載動作時，就可以透過reload\(\)函式。

```text
import math
from importlib import reload
print(reload(math))
執行結果：
<module 'math' from '/anaconda3/lib/python3.6/lib-dynload/math.cpython-36m-darwin.so'>
```

> 但要注意，若該模組沒有被載入過，就會產生錯誤。

```text
from importlib import reload
print(reload(math))
執行結果：
NameError: name 'math' is not defined
```

### \_\_name\_\_屬性

每個模組都有\_\_name\_\_屬性，若直接執行該\*.py檔，則\_\_name\_\_屬性會被設置為"\_\_main\_\_"的字串，表示為主模組。而若是以import語句來導入進去，則\_\_name\_\_會被設置為模組名稱。

## 標準函式庫

#### 命令列引數

有時我們需要取得使用者在Terminal打的指令，這時就可透過sys模組的argv得到。

```text
# test.py
import sys
print(sys.argv)
print(len(sys.argv))

#在Terminal執行
$ python test.py aaa bbb ccc
執行結果：
['test.py', 'aaa', 'bbb', 'ccc']
<class 'list'>
```

