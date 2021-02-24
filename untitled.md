# PyCharm 安裝 PyQt5

### 前言

目的是期待能統一管理檔案，可以在PyCharm上使用

1. Qt Designer
2. 編譯Qt Designer產生的`.ui`檔，自動產出相對應的`.py`檔

免去傳統方式花費多餘的時間與精神。

主要參考下方 _連結1_ 的步驟，不過我忽略`pyqt5-tools`的安裝，因為有error，另外一個 _連結2_ 教學也沒有提到需要安裝，也不知是否OS不同的關係，不過不影響目前的操作。

### 執行環境

macOS

### 需要工具

1. \*\*\*\*[**PyCharm**](https://www.jetbrains.com/pycharm/) IDE：撰寫程式碼的介面
2. **PyQt5** 套件：就像**wxPython**是一種開發UI的框架，有兩種安裝方式：

   1. 透過指令列輸入**`pip install PyQt5`**
   2. 使用PyCharm IDE的既有功能來新增：於上方選單的 **PyCharm** &gt; **Preferences** &gt; **Project: myTutorial** \(myTutotial為自訂的專案名稱\) &gt; **Python Interpretor** &gt; 點選 **+** &gt; 搜尋"**PyQt5**"並選擇 &gt; 點選下方"**Install Package**"安裝 

   因第二種方式是跟專案綁在一起，也就是移除專案時會一併刪除。故採用第一種方式，然後再利用PyChram External的設定， 讓PyCharm可以直接使用PyQt5，也不用擔心專案移除時要再重複動作。  

3. \*\*\*\*[**Qt Designer**](https://build-system.fman.io/qt-designer-download) ****：為一個圖形介面，讓user易於設計版面

### 設定PyCharm External連結：可以直接使用PyQt5與Qt Designer

#### Qt Designer setting

**PyCharm** &gt; **Preferences** &gt; **Tools** &gt; **External Tools** &gt; 點選 **+** &gt; 填入以下資訊

![](.gitbook/assets/image%20%2828%29.png)

**`Name`**：可以取任意名稱

**`Program`**：填入**Qt Designer**安裝路徑底下的`/Applications/Qt Designer.app/Contents/MacOS/Designer.exe`

**`Working directory`**：之後開啟操作**Qt Designer** IDE時，存檔時的路徑。以我為例目前是設定在我PyCharm的專案底下，如`/Users/`_`user 名稱`_`/PycharmProjects/myTutorial`，或是填入`$ProjectFileDir$`也是一樣效果。

#### PyQt5 setting

**PyCharm** &gt; **Preferences** &gt; **Tools** &gt; **External Tools** &gt; 點選 **+** &gt; 填入以下資訊

![](.gitbook/assets/image%20%2829%29.png)

**`Name`**：可以取任意名稱

**`Program`**：安裝**PyQt5**後會產生**`pyuic5`**這個工具，我們需要`pyuic5`這個工具來幫忙編譯`.ui`檔並產出對應的`.py`檔。這裏填入**PyQt5**安裝路徑底下的`/Library/Frameworks/Python.framework/Versions/3.8/bin/pyuic5`

{% hint style="info" %}
安裝路徑可以在指令列下`which pip`，然後再尋找`pyuic5`的位置在哪
{% endhint %}

**`Arguments`**：填入`$FileName$ -o $FileNameWithoutExtension$.py`，編譯`.ui`檔並產出`.py`檔

**`Working directory`**：產出的`.py`檔要存在哪裡。以我為例目前是設定在我PyCharm的專案底下，如`/Users/`_`user 名稱`_`/PycharmProjects/myTutorial`，或是填入`$ProjectFileDir$`也是一樣效果。

### 執行External Tools

上述步驟完成後，可以看到**Tools**多出了**External Tools**，裡面包含剛剛所新增的兩個外部工具。

![](.gitbook/assets/image%20%282%29.png)

執行**Qt Designer**就可以看到其操作介面，預設 **Main Window** &gt; **Create** &gt; 試著拖曳一個Label元件 &gt; 存檔命名`Label.ui`

![](.gitbook/assets/image%20%2812%29.png)

![](.gitbook/assets/image%20%2823%29.png)

存檔之後回到PyCharm會發現多了`Label.ui`檔，對它按**右鍵** &gt; **External Tools** &gt; **PyUIC**，就會產出對應的`Label.py`檔。

![](.gitbook/assets/image%20%2832%29.png)

![](.gitbook/assets/image%20%2830%29.png)

### Final test

然後，在專案底下建立一個新的 Python 檔案，這是為了讓程式與界面分離。複製以下程式碼：

```python
from PyQt5 import QtWidgets, QtGui, QtCore
from Label import Ui_MainWindow
import sys


class MainWindow(QtWidgets.QMainWindow):
     def __init__(self):
         super(MainWindow, self).__init__()
         self.ui = Ui_MainWindow()
         self.ui.setupUi(self)
         self.ui.label.setText('Hello World!')


if __name__ == '__main__':
     app = QtWidgets.QApplication([])
     window = MainWindow()
     window.show()
     sys.exit(app.exec_())
```

第二行`Label` 是剛產生檔案\(`Label.py`\)的路徑，匯入它裡面定義的 `class Ui_MainWindow`。

當然您也可以將`Label.py`放入不同的資料夾\(如_`UI`_\)做分類，如下方 _連結1_ 的介紹，但第二行就要改成`from UI.Label import Ui_MainWindow`

執行結果：

![](.gitbook/assets/image%20%283%29.png)

## Ref.

{% embed url="https://clay-atlas.com/blog/2019/08/26/python-chinese-pyqt5-tutorial-install/" caption="連結1" %}

{% embed url="https://zhung.com.tw/article/pyqt%E5%85%A5%E9%96%80%E7%94%A8python%E5%AF%AB%E7%AC%AC%E4%B8%80%E6%94%AFgui/" caption="連結2" %}



