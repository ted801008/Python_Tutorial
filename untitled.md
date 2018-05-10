# 開發環境建置

## Anaconda

1. Anaconda是一個集眾多科學運算、數據分析、資料視覺化的Python資源包。
2. 支援Mac, Window, Linux。
3. 支援Python2 與 Python3
4. 自帶jupyter notebook編譯器
5. 闔家歡樂的必備良藥

### 安裝方法

安裝方法很簡單，請前往[Anaconda](https://www.anaconda.com/download/#macos)官方網站，並選擇你電腦的作業系統\(Mac OSX, Windows, Linux\)，接著直接下載你所想要的Python版本即可。

### 環境變數

一般來說，Anaconda的Installer應會直接幫忙新增環境變數，但還是稍微來談論一下環境變數的設置吧。由於筆者的系統是MacOSX，因此會以MacOSX進行介紹。  
  
MacOSX環境變數依生命週期可分為：  
1. 永久型：在配置文檔中進行修改，變數永久生效。  
2. 暫時型：在Terminal中以export進行宣告，變數在該Shell關閉後即會失效，建立的格式如下：

若有多個路經須以冒號：連接，尾端需加入${PATH}，代表支援系統環境變數。

MacOSX環境變數的配置文檔有三個：  
1. /etc/profile  
2. /etc/bashrc  
3. ~/.bash\_profile  
  
其中，前兩個檔屬於系統級別，變數配置對所有使用者皆有效，而.bash\_profile檔則屬於使用者級別，變數配置僅會對該登入使用者生效。

> Note：預設情況下，.bash\_profile檔是不存在的，需透過nano編輯器進行創建。創建方法請開啟Terminal並輸入以下代碼：

```text
nano ~/.bash_profile
```

而環境變數的建立格式則如下，若有多個路徑則以冒號:進行連接，句尾需加上${PATH}，代表支援系統環境變數。

```text
export PATH = path1:path2:path3:${PATH}
```

若已編寫完畢後，按_command+O _即可儲存\(_command+C _為取消\)，並按 _command+X _退出。

> Note：此時環境變數並不會立即生效，可退出Terminal後再另啟一個Terminal即會生效。或是輸入source 指令\(source + 環境變數文件\)，其中 source指令已可被稱為「點命令」，因此也可以以 . 作為代替\(如：. /etc/profile\)。

