# 設定背景

### 背景圖片

```python
        # Pixmap
        image = QtGui.QPixmap()
        image.load('pic/Python_PyQt5.png')
        image = image.scaled(self.width(), self.height())

        # Palette
        palette = QtGui.QPalette()
        palette.setBrush(self.backgroundRole(), QtGui.QBrush(image))
        self.setPalette(palette)
```

### 背景顏色

```python
        # Pixmap
        # image = QtGui.QPixmap()
        # image.load('pic/Python_PyQt5.png')
        # image = image.scaled(self.width(), self.height())
        #
        # Palette
        palette = QtGui.QPalette()
        palette.setBrush(self.backgroundRole(), QtGui.QColor(150, 200, 100))
        self.setPalette(palette)
```

### 隱藏上方title bar

```python
        # Hide Window Title
        self.setWindowFlag(QtCore.Qt.FramelessWindowHint)
```

## Ref.

{% embed url="https://clay-atlas.com/blog/2019/08/28/python-chinese-pyqt5-tutorial-mainwindow-icon-pixmap-palette/" %}



