# 標準數據形態

在Python中，標準數據形態有6種:

| 型態 | 可否改變 |
| --- | --- | --- | --- | --- | --- | --- |
| 數值\(Number\) | 不可變\(Immutable\) |
| 字串\(String\) | 不可變\(Immutable\) |
| 元組\(Tuple\) | 不可變\(Immutable\) |
| 集合\(Set\) | 不可變\(Immutable\) |
| 串列\(List\) | 可變\(Mutable\) |
| 字典\(Dictionary\) | 可變\(Mutable\) |

所謂的可變\(Mutable\)與不可變\(Immutable\)是指該數據可否被改變內部值。  
  
另一方面，在Python中，我們可以使用type\(\)與isinstance\(\)來查看類型。

```text
>>> type('Hello World')
<class 'str'>
#由上可看到其類型為str，代表的即是字串類型(String)。

>>> isinstance('Hello World',str)
True
# 亦可使用isinstance確認其型態。
```

在接下的章節，會分別講述這6種標準數據形態。

