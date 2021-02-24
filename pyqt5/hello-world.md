# Hello world!

```python
import sys

from PyQt5 import QtWidgets, QtGui, QtCore

def window():
   app = QtWidgets.QApplication(sys.argv)

   window = QtWidgets.QWidget()
   window.setGeometry(100, 100, 200, 50)
   window.setWindowTitle("PyQt5")

   label = QtWidgets.QLabel(w)
   label.setText("Hello World!")
   label.move(50,20)

   window.show()
   
   sys.exit(app.exec_())
   
if __name__ == '__main__':
   window()
```

in oop:

```python
import sys

from PyQt5 import QtWidgets, QtGui, QtCore

class window(QtWidgets.QWidget):
    def __init__(self, parent = None):
        super(window, self).__init__(parent)
        self.resize(200,50)
        self.setWindowTitle("PyQt5")
        self.label = QtWidgets.QLabel(self)
        self.label.setText("Hello World")
        font = QtGui.QFont()
        font.setFamily("Arial")
        font.setPointSize(16)
        self.label.setFont(font)
        self.label.move(50,20)

def main():
    app = QtWidgets.QApplication(sys.argv)
    ex = window()
    ex.show()
    sys.exit(app.exec_())

if __name__ == '__main__':
    main()
```

## Ref.

{% embed url="https://www.tutorialspoint.com/pyqt5/pyqt5\_hello\_world.htm" %}



