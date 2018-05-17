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
輸出結果：
Thu May 17 00:58:48 2018

import time
randomTime = '2018-02-10 0:12:12'
timeTuple = time.strptime(randomTime,'%Y-%m-%d %H:%M:%S')
print(time.asctime(timeTuple))
輸出結果：
Sat Feb 10 00:12:12 2018
```

#### ctime\(\)

將一個時間戳轉換為字串，預設為當前時間。

```text
import time
print(time.ctime())
輸出結果：
Thu May 17 01:04:41 2018

import time
print(time.ctime(1526482323))
輸出結果：
Wed May 16 22:52:03 2018
```

#### gmtime\(\)

將一個時間戳轉換成一個UTC時區\(0時區\)的struct\_time，預設為當前時間。

```text
import time
print(time.gmtime())
輸出結果：
time.struct_time(tm_year=2018, tm_mon=5, tm_mday=16, tm_hour=17, tm_min=14, tm_sec=57, tm_wday=2, tm_yday=136, tm_isdst=0)

import time
print(time.gmtime(1526482323))
輸出結果：
time.struct_time(tm_year=2018, tm_mon=5, tm_mday=16, tm_hour=14, tm_min=52, tm_sec=3, tm_wday=2, tm_yday=136, tm_isdst=0)
```

#### localtime\(\)

將一個時間戳轉換成當前時區的struct\_time，預設為當前時間。

```text
import time
print(time.localtime())
輸出結果：
time.struct_time(tm_year=2018, tm_mon=5, tm_mday=17, tm_hour=1, tm_min=17, tm_sec=43, tm_wday=3, tm_yday=137, tm_isdst=0)

import time
print(time.localtime(1526482323))
輸出結果：
time.struct_time(tm_year=2018, tm_mon=5, tm_mday=16, tm_hour=22, tm_min=52, tm_sec=3, tm_wday=2, tm_yday=136, tm_isdst=0)
```

#### mktime\(\)

將一個struct\_time轉換為時間戳。

```text
import time
randomTime = '2018-02-10 0:12:12'
timeTuple = time.strptime(randomTime,'%Y-%m-%d %H:%M:%S')
print(time.mktime(timeTuple))
輸出結果：
1518192732.0
```

#### strftime\(\)

將一個struct\_time轉換為指定的格式化字串輸出，預設為當前時間。

```text
import time
print(time.strftime("%Y-%m-%d %H:%M:%S"))
輸出結果：
2018-05-17 01:28:51

import time
randomTime = '2018-02-10 0:12:12'
timeTuple = time.strptime(randomTime,'%Y-%m-%d %H:%M:%S')
print(time.strftime('%Y-%m-%d %H:%M:%S',timeTuple))
輸出結果：
2018-02-10 00:12:12
```

#### strptime\(\)

將字串根據指定的格式轉換為struct\_time。

```text
import time
randomTime = '2018-02-10 0:12:12'
timeTuple = time.strptime(randomTime,'%Y-%m-%d %H:%M:%S')
print(timeTuple)
輸出結果：
time.struct_time(tm_year=2018, tm_mon=2, tm_mday=10, tm_hour=0, tm_min=12, tm_sec=12, tm_wday=5, tm_yday=41, tm_isdst=-1)
```

