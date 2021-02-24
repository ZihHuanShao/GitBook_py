# QFormLayout

```python
import sys
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *


def window():
    app = QApplication(sys.argv)
    win = QWidget()
    fbox = QFormLayout()

    # First fbox

    fbox.addRow(QLabel("Name"), QLineEdit())

    # Second fbox

    vbox = QVBoxLayout()
    vbox.addWidget(QLineEdit())
    vbox.addWidget(QLineEdit())
    fbox.addRow(QLabel("Address"), vbox)

    # Third fbox

    hbox = QHBoxLayout()
    hbox.addWidget(QRadioButton("Male"))
    hbox.addWidget(QRadioButton("Female"))
    hbox.addStretch()
    fbox.addRow(QLabel("sex"), hbox)

    # Last fbox

    hbox = QHBoxLayout()
    hbox.addWidget(QPushButton("Submit"))
    hbox.addWidget(QPushButton("Cancel"))
    fbox.addRow(hbox)


    win.setLayout(fbox)
    win.setWindowTitle("PyQt")
    win.show()
    sys.exit(app.exec_())


if __name__ == '__main__':
    window()
```

![](../../.gitbook/assets/image%20%2821%29.png)

## Ref.

{% embed url="https://www.tutorialspoint.com/pyqt5/pyqt5\_qformlayout\_class.htm" %}



