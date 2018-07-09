# 函式

在往後編寫複雜的程式時，若都是無結構的直接寫，會造成日後維護的複雜性與困難度。因此，需妥善地運用「函式」\(Function\)這玩意兒，或稱為「方法」\(Method\)。那麼函式\(Function\)與方法\(Method\)之間的差異為何呢？差別在於  
函式是結構化程式設計的用語，而方法則是來自於物件導向程式設計。

簡單來說，函式是一個可以包覆代碼塊的東東，當被呼叫時，便會執行其內的代碼。如此一來，我們可以提高程式碼的結構性與重用性。  
  
在先前的章節中，我們有多次使用到內建的函式，如print\(\)、list\(\)等等，這是系統預設的不用自行編寫。當然，你也可以自己建立屬於你的函式，稱為用戶自定義函式。而其實Python中的函式大概可以分為三種：

* 內建函式\(Built-in Function\)：如type\(\)、int\(\)
* 標準函式庫\(Standard Library\)：如字串物件方法
* 自行定義函式：使用def定義

```text
print(type(len))

print(type(str.split))

def self_definition():
    print('haha')

print(type(self_definition))

輸出結果：
<class 'builtin_function_or_method'> #BIF內建函式
<class 'method_descriptor'> #物件方法
<class 'function'> #自訂函式
# 可使用type()函式看屬於哪種類型函式
```

那麼到底為何要使用函式這種東東呢？使用他有什麼好處呢？這邊為各位整理一下

1. 模組結構化
2. 可重複使用，方便維護
3. 資料隱藏\(物件導向觀點\)

## 函式宣告

函式的宣告需注意：  
1. 使用def關鍵字  
2. 函式名稱須符合命名規範  
3. 參數串列\(形式參數串列, format argument list\)：可有可無  
4. 函式代碼塊需縮排，可單行或多行

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
3. 在函式名稱後需接\( \):若要使用參數\(可在呼叫時給予值\)，則在括號內宣告，若沒有要使用參數，則讓此括號為空就好，而其實參數就是變量而並無型態，你可以任意將其作串列、字典、字串等使用，此稱為「形式參數」\(Formal parameter\)。  
4. 可使用return關鍵字來回傳值，並在執行return後即跳出函式。  
5. 呼叫函式僅需寫上該函式名稱與對應參數，這些參數稱為「實際引數」\(Actual arguments\)，你可在程式碼中任一地方呼叫，甚至在另一個函數中呼叫。

## 參數

函式的參數大致可分為  
1. 形式參數\(Formal parameter\)：函式中所定義的參數，會在函式代碼塊執行運算，預設為位置參數。  
2. 實際參數\(Actual argument\)：呼叫函式所傳遞給函式指定形式參數值，預設為位置參數。

### 可變更\(Mutable\) vs. 不可變更\(Immutable\)

或許你會想問，將參數在函式內操作完後，其值會不會改變呢？  
答案就是，依傳入值的型態而定。  
1. 若傳入資料的型態為不可變更的\(Immutable\)，則其所傳遞的僅是值，並非該傳入物件本身，此概念類似於值傳遞\(pass by value\)。  
  
2. 而若傳入資料的型態為可變更的\(Mutable\)，則所傳遞為該物件本身，在函式中作的改動會直接改變傳入物件，此概念類似於引用傳遞\(pass by reference\)。

```text
def func1(param):
    param = 'XD'

a = 'Immutable'
func(a)
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

#### 必選\(位置\)參數

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

#### 關鍵字引數

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

但要注意的是與位置參數的搭配

```text
def func1(name,title):
    print('name:',name)
    print('title:',title)

func1('龍',title='Joey')
執行結果：
name: 龍
title: Joey
# 第一個位置參數'龍'，會對應到名為name的形式參數。

func1('Joey',name = '龍')
執行結果：
-bash: syntax error near unexpected token `'Joey',name'
# 這樣就會產生錯誤，因為第一個位置參數'Joey'會對應到name的形式參數，但後面又給予一次name形式參數的值。
```

#### 默認參數

可在宣告函式時，給予參數默認值，當呼叫函式而未給值，則會使用默認參數。

> 注意：必選\(位置\)參數必須在默認參數前

```text
def func1(name='Joey',title='哈哈'):
    print('name:',name)
    print('title:',title)
    
func1(title='龍')
執行結果：
name:Joey
title:龍
# 可以看到當未給參數值時，則會使用默認的值。

def func2(name = 'Joey',title):
    print('name',name)
    print('title',title)
func2(title = '龍')
執行結果：
SyntaxError: non-default argument follows default argument
#默認參數須在必選參數後
```

剛才有提到，若形式參數為不可變資料類型，則會以傳值的方式進行，會將傳入物複製一份並執行一次的函式; 而若為可變資料類型，則會以傳址的方式進行。  
  
基於這樣的概念，若默認參數指定為不可變資料類型，若在呼叫函式給予實際引數，則一樣會以傳值的方式進行，將默認值取代。  
但若是指定為可變資料類型，則若在不給予實際引數，則會累積內容。

```text
def func2(name,nameList = []):
    nameList.append(name)
    print(nameList)
func2('Joey')
func2('Kobe')
執行結果：
['Joey']
['Joey', 'Kobe']
# 可以發現當指定為可變的資料型態-串列時，則會累積結果。
```

#### 不定長參數

當所傳入的參數數量是不定時，則可使用不定長參數。不定長參數有兩種：

1. \*星號運算式：配合元組tuple物件來蒐集不定長的實際引數，主要就是利用元組的unpacking運算。註：而在Python3後，還可將關鍵字引數置於\*星號參數之後。

```text
def func(name,email,*other):
    print('Name:',name)
    sum = 0
    for i in other:
        sum+=i
    print('Total_Score:',sum/len(other))
    print('Eamil:',email)

func('Joey','joey@gmail.com',90,70,80)
print()
func('Kobe','kobe@gmail.com',99,96,92,97,94)
執行結果：
Name: Joey
Total_Score: 80.0
Eamil: joey@gmail.com

Name: Kobe
Total_Score: 95.6
Eamil: kobe@gmail.com

# 可以看到在定義參數時，僅需在該參數前加上星號*，即可將其定義。
# 在每次呼叫函式時，可給予不同數量的值。

def func2(name,email,*star,additional):
    print(name,email,star,additional)

func2('joey','joey@gmail.com',90,20,30,additional = 50)
執行結果：
joey joey@gmail.com (90, 20, 30) 50

func2('joey','joey@gmail.com',90,20,30,50)
執行結果：
TypeError: func2() missing 1 required keyword-only argument: 'additional'
#但注意在其後的參數必須以關鍵字引數傳入，否則會產生錯誤。
```

\*運算子還可用於拆解可迭代物件，應用於實際引數。

```text
def func3(n1,n2,n3,n4,n5):
    print(n1,n2,n3,n4,n5)
    
func3(1,2,*range(3,10))
執行結果：
1 2 3 4 5
```

    2. \*\*雙星運算式：搭配字典物件來蒐集關鍵字引數。

```text
def func3(name,email,**star):
    print(name,email,star)

func3('joey','joey@gmail.com',a = 1,b = 2,c = 3)
執行結果：
joey joey@gmail.com {'a': 1, 'b': 2, 'c': 3}
```

同樣地，\*\*運算子亦可用於拆解映射物件，應用於實際引數，鍵\(key\)作為形式參數名，用其接收對應的映射物件的值。

```text
def func4(a,b,c,x,y,z):
    print(a,b,c)
    print(x,y,z)

data = dict(x=4,y=5,z=6)
func4(1,2,3,**data)
執行結果：
1 2 3
4 5 6

data = dict(a=4,b=5,c=6)
func4(1,2,3,**data)
執行結果：
TypeError: func4() got multiple values for argument 'a'
# 但要記得參數名與鍵名必須一樣，否則會對應不到。
```

\*與\*\*運算式可以兩個一起搭配使用

```text
def func4(*star,**dstar):
    print(star,'\n',dstar)

func4(1,2,3,4,a=1,b=2,c=3)
執行結果：
(1, 2, 3, 4) 
 {'a': 1, 'b': 2, 'c': 3}
```

## 匿名函式

匿名函式在Python中是一個很特別的函式，其不用以def來建構標準的函式，僅需使用lambda來建構表達式，相較於建構標準的def函式，較為簡潔。

def函式的主體為代碼塊，而匿名函式的主體則只是一個包含有限邏輯的表達式，其擁有自己的命名空間，而不能使用自己參數列表以外的參數，全局參數亦不行。

建立方式如下：

```text
lambda arg1,arg2,arg3... : expression
```

```text
average = lambda arg1,arg2,arg3:(arg1+arg2+arg3)/3
print('平均:',average(1,2,3))
執行結果：
平均:2.0

a = [(lambda x:x*x)(x) for x in range(10)]
print(a)
執行結果：
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

## 變數作用域

在Python中，並不是所有變數都可以供你在任意位置使用，有些變數哪裡都可以用，有些變數只能在某地方用。以此邏輯，Python的作用域可以被分為：  
1. 局部作用域：Local\(L\)  
2. 嵌套函式\(閉包\)作用域：Enclosing\(E\)  
3. 全局作用域：Global\(G\)  
4. 內建作用域：Built-in\(B\)

Python會以LEGB的規則去查找變數，一開始會到局部作用域\(Local\)找，找不到時，便到局部的局部作用域\(Enclosing\)找，接著才到全局作用域找，最後是到內建作用域找。

在Python中，只有模塊\(module\)、類別\(class\)、函式\(def,lambda\)才會建立新的作用域，其於代碼則不會引入新的作用域。

依這種概念去想以下代碼

```text
name = 'joey'
def func():
    print(name)
    name = 'kobe' #改變全域變數

func()
執行結果：
UnboundLocalError: local variable 'name' referenced before assignment
#因為python會以LEGB的方式去找變數，區域變數name在指派前已給值，因此產生混亂。

name = 'joey'
def func2():
    name = 'kobe' #區域變數
    print(name)
print(name)
執行結果：
kobe
joey


name = 'joey'
def func3():
    global name #以global關鍵字宣告其為全域變數
    print(name)
    name = 'kobe'
    print(name)
func3()
print(name)
執行結果：
joey
kobe
kobe
```

#### 局部作用域\(Local\)

適用於所宣告的函式或流程控制的代碼塊，離開範圍即會結束生命週期。

```text
def func():
    a = '1'
print(a)
執行結果：
NameError: name 'a' is not defined
# 在函式內宣告的變數a屬於局部作用域，僅能在該函式內使用。
```

#### 嵌套函式\(閉包\)作用域\(Enclosing\)

```text
def funcOutter():
    print('嵌套函數作用域')
    def funcInner():
        print('局部作用域')

# 如上例，funcInner()函式內為局部作用域，而funcOutter()函式則為嵌套函式作用域。
```

#### 全局作用域

適用於整個程式檔\(\*.py\)

```text
a = 1
def func():
    print(a)
func()
執行結果：
1
# 在外部宣告的變數a屬於全局作用域，可在該程式任一地方使用。
```

#### 內建作用域

```text
a = int(2.9)
```

### global & nonlocal 關鍵字

當你想在局部作用域改變全局作用域的變數時，便須使用到global關鍵字了。

```text
a = 1
def func():
    global a
    a = 0
func()
print(a)
執行結果：
0
```

若想在局部作用域修改嵌套函式作用域\(enclosing\)的變數時，則須使用到nonlocal關鍵字。

```text
def func1():
    a = 0
    def func2():
        nonlocal a
        a = 1
    func2()
    print(a)
func1()
執行結果：
1
```

