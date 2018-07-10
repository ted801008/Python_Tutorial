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

