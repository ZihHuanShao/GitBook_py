# QStackedWidget

類似`QTabWidget`，有別於`QTabWidget`是系統提供的，`QStackedWidget`則必須實作分頁的UI，以下範例用`QListWidget()`來達到選擇分頁的效果與畫面。

1. 建立**Left side** layot：使用`self.leftlist = QListWidget()`
2. 建立**Right side** layout：使用`self.Stack = QStackedWidget(self)`
3. **Left** **side** + **Right side** layout：使用`hbox = QHBoxLayout(self)`
4. Bind Left side to triger Right side：`self.leftlist.currentRowChanged.connect(self.display)`
5. 顯示對應的page\(Right side\)：`self.Stack.setCurrentIndex(i)`

```python
import sys
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *


class stackedExample(QWidget):
    def __init__(self):
        super(stackedExample, self).__init__()

        # LEFT SIDE

        self.leftlist = QListWidget()

        self.leftlist.insertItem(0, 'Contact')
        self.leftlist.insertItem(1, 'Personal')
        self.leftlist.insertItem(2, 'Educational')

        # RIGHT SIDE

        self.stack1 = QWidget()
        self.stack2 = QWidget()
        self.stack3 = QWidget()

        self.stack1UI()
        self.stack2UI()
        self.stack3UI()

        self.Stack = QStackedWidget(self)
        self.Stack.addWidget(self.stack1)
        self.Stack.addWidget(self.stack2)
        self.Stack.addWidget(self.stack3)

        # COMBINE LEFT SIDE + RIGHT SIDE

        hbox = QHBoxLayout(self)
        hbox.addWidget(self.leftlist)
        hbox.addWidget(self.Stack)

        self.setLayout(hbox)

        # 綁定 LEFT SIDE 觸發 RIGHT SIDE
        self.leftlist.currentRowChanged.connect(self.display)

        self.setGeometry(300, 50, 10, 10)
        self.setWindowTitle('StackedWidget demo')
        self.show()


    def stack1UI(self):
        layout = QFormLayout()
        layout.addRow("Name", QLineEdit())
        layout.addRow("Address", QLineEdit())
        # self.setTabText(0,"Contact Details")
        self.stack1.setLayout(layout)


    def stack2UI(self):
        layout = QFormLayout()
        sex = QHBoxLayout()
        sex.addWidget(QRadioButton("Male"))
        sex.addWidget(QRadioButton("Female"))
        layout.addRow(QLabel("Sex"), sex)
        layout.addRow("Date of Birth", QLineEdit())

        self.stack2.setLayout(layout)


    def stack3UI(self):
        layout = QHBoxLayout()
        layout.addWidget(QLabel("subjects"))
        layout.addWidget(QCheckBox("Physics"))
        layout.addWidget(QCheckBox("Maths"))
        self.stack3.setLayout(layout)


    def display(self, i):
        self.Stack.setCurrentIndex(i)


def main():
    app = QApplication(sys.argv)
    ex = stackedExample()
    sys.exit(app.exec_())


if __name__ == '__main__':
    main()
```

## Ref.

{% embed url="https://www.tutorialspoint.com/pyqt5/pyqt5\_qstackedwidget.htm" %}



