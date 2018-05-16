# 函式

在往後編寫複雜的程式時，若都是無結構的直接寫，會造成日後維護的複雜性與困難度。因此，需妥善地運用函式這玩意兒。

函式是一個可以包覆代碼塊的東東，當被呼叫時，便會執行其內的代碼。如此一來，我們可以提高程式碼的結構性與重用性。  
  
在先前的章節中，我們有多次使用到內建的函式，如print\(\)、list\(\)等等，這是系統預設的不用自行編寫。  
當然，你也可以自己建立屬於你的函式，稱為用戶自定義函式。

## 函式宣告

函式的宣告需使用def關鍵字，由於怕講得抽象，因此我們直接帶例子來看吧。

```text
def firstFunc():
    print('XD')
    return
result = firstFunc()
print(result)
輸出結果：
XD
None

#函式名稱為fiestFunc，沒有指定參數。
# 不帶表達式的return或者根本不宣告return代表回傳None。


def secondFunc(a,b):
    print(a,end=' ')
    print(b)
    return 'END'

result = joey('I am','Joey')
print(result)
輸出結果：
I am Joey
END

# 函式名為secondFunc，參數為a,b可在呼叫時給予值。
# 使用return來回傳END字串，並賦值給名為result的變數。
```

由上例可以看到，函式的宣告規則有：  
1. 使用def 關鍵字來宣告。  
2. 在def後的為該函式的名稱。  
3. 在函式名稱後需接\( \):若要使用參數\(可在呼叫時給予值\)，則在括號內宣告，若沒有要使用參數，則讓此括號為空就好，而其實參數就是變量而並無型態，你可以任意將其作串列、字典等使用。  
4. 可使用return關鍵字來回傳值，並在執行return後即跳出函式。  
5. 呼叫函式僅需寫上該函式名稱與對應參數，你可在程式碼中任一地方呼叫，甚至在另一個函數中呼叫。

## 參數

### 可變更\(Mutable\) vs. 不可變更\(Immutable\)

或許你會想問，將參數在函式內操作完後，其值會不會改變呢？  
答案就是，依傳入值的型態而定。  
1. 若傳入資料的型態為不可變更的\(Immutable\)，則其所傳遞的僅是值，並非該傳入物件本身，此概念類似於值傳遞\(pass by value\)。  
  
2. 而若傳入資料的型態為可變更的\(Mutable\)，則所傳遞為該物件本身，在函式中作的改動會直接改變傳入物件，此概念類似於引用傳遞\(pass by reference\)。

```text
def func1(param):
    param = 'XD'

a = 'Immutable'
print(a)
執行結果：
Immutable
# 因傳入參數的型態為字串(String)，字串屬於不可變更的(Immutable)，因此原物件並不會被改變。

def func2(param):
    param.append('XD')
a = [1,2,3]
func2(a)
print(a)
執行結果：
[1,2,3,'XD']
# 因傳入參數的型態為串列(List)，串列屬於可變更的(Mutable)，因此原物件會被改變。
```

### 參數類型

#### 必選參數

必選參數必須傳入與宣告函式一樣相應順序的物件，多一個、少一個或順序不對皆不行。

```text
def func1(a,b,c):
    print(a+b,c)
func1(1,2,3)
執行結果：
6

func1(1,2)
執行結果：
TypeError: func1() missing 1 required positional argument: 'c'
# 此例出現錯誤的原因即在於少給一個參數。
```

#### 關鍵字參數

使用關鍵字參數允許傳入的順序與宣告的不一致，因為Python的解釋器可以根據參數名自動匹配參數值。

```text
def func1(name,title):
    print('name:',name)
    print('title:',title)

func1(title='龍',name='Joey')
執行結果：
name:Joey
title:龍
# 可以看到即便是傳入的順序不一樣，還是可以匹配的到。
```

#### 默認參數

可在宣告函式時，給予參數默認值，當呼叫函式而未給該參數值，則會使用默認參數。

```text
def func1(name='Joey',title='哈哈'):
    print('name:',name)
    print('title:',title)
    
func1(title='龍')
執行結果：
name:Joey
title:龍
# 可以看到當未給參數值時，則會使用默認的值。
```

