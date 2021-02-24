# QBoxLayout

* 按垂直方向排列元件\(widget\)
* 按水平方向排列元件

```python
import sys
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *


def window():
    app = QApplication(sys.argv)
    win = QWidget()

    b1 = QPushButton("Button1")
    b2 = QPushButton("Button2")

    # 按垂直方向排列元件
    vbox = QVBoxLayout()
    vbox.addWidget(b1)
    vbox.addStretch()
    vbox.addWidget(b2)
    
    # 按水平方向排列元件
    hbox = QHBoxLayout()

    b3 = QPushButton("Button3")
    b4 = QPushButton("Button4")
    hbox.addWidget(b3)
    hbox.addStretch()
    hbox.addWidget(b4)

    vbox.addStretch()
    
    # hbox當作一個元件讓vbox可以add，且按照垂直方向排列
    vbox.addLayout(hbox)
    
    
    win.setLayout(vbox)

    win.setWindowTitle("PyQt")
    win.show()
    sys.exit(app.exec_())


if __name__ == '__main__':
    window()
```

## Ref.

{% embed url="https://www.tutorialspoint.com/pyqt5/pyqt5\_qboxlayout\_class.htm" %}



