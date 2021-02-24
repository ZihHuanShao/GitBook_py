# Embeded GoogleMaps into PyQt5

要先另外安裝 `QtWebEngineWidgets` package

```python
import sys
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *
from PyQt5.QtWebEngineWidgets import QWebEngineView
import gmplot
from pathlib import Path

class window(QWidget):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):

        vbox = QVBoxLayout(self)
        
        apikey = 'XXXXXX'  # (your API key here)

        gmap = gmplot.GoogleMapPlotter(30.3164945, 78.03219179999999, 12, apikey=apikey)

        # 測試繪製座標
        latitude_list = [30.3358376, 30.307977, 30.3216419]
        longitude_list = [77.8701919, 78.048457, 78.0413095]

        # 畫點
        gmap.scatter(latitude_list, longitude_list, '#FF0000', size=40, marker=False)

        # 畫線
        gmap.plot(latitude_list, longitude_list, 'cornflowerblue', edge_width=2.5)

        # 產出的檔名
        filename = 'map.html'

        # Draw the map to an HTML file:
        gmap.draw(filename)

        # 取得當前路徑
        currentPath = Path(__file__).parent.absolute()

        # 完整的檔案路徑
        fullFilePath = "file://" + str(currentPath) + "/" + filename

        # 利用 QWebEngineView 讓 google map 顯示在畫面上
        view = QWebEngineView()
        view.load(QUrl(fullFilePath))

        vbox.addWidget(view)

if __name__ == '__main__':
    app = QApplication(sys.argv)
    w = window()
    w.show()

    sys.exit(app.exec_())
```

## Ref.

{% embed url="https://blog.csdn.net/qq\_38684480/article/details/85123777?utm\_medium=distribute.pc\_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-12.control&depth\_1-utm\_source=distribute.pc\_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-12.control" %}



