# 日期與時間

顯示日期與時間在應用程序中是一個很常見的功能，其還可以用來計算處理時間等等，是一個不可不知的功能。

## time模塊

在time模塊中，表達時間的形式通常有  
\(1\) 時間戳   
\(2\) 格式化時間字串   
\(3\) 數組形式\(struct\_time\)：包含九大元素，如下表。

| 元素 | 範圍 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| year | 4個數字 |
| month | 1~12 |
| day | 1~31 |
| hour | 0~23 |
| minute | 0~59 |
| second | 0~59 |
| weekday | 0~6 \(0為星期一\) |
| Julian day | 1~366 |
| DST | -1, 0 or 1 \(是否為夏季令時\) |

### 常見函數

#### asctime\(\)

將一個struct\_time轉換為字串，預設為當前時間。

```text
import time
print(time.asctime())
執行結果：
Thu May 17 00:58:48 2018

import time
randomTime = '2018-02-10 0:12:12'
timeTuple = time.strptime(randomTime,'%Y-%m-%d %H:%M:%S')
print(time.asctime(timeTuple))
執行結果：
Sat Feb 10 00:12:12 2018
```

#### ctime\(\)

將一個時間戳轉換為字串，預設為當前時間。

```text
import time
print(time.ctime())
執行結果：
Thu May 17 01:04:41 2018

import time
print(time.ctime(1526482323))
執行結果：
Wed May 16 22:52:03 2018
```

