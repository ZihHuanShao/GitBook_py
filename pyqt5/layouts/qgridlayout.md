# QGridLayout

<table>
  <thead>
    <tr>
      <th style="text-align:left">&lt;code&gt;&lt;/code&gt;</th>
      <th style="text-align:left">&lt;code&gt;&lt;/code&gt;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b><code>addWidget(QWidget, int r, int c)</code></b>
      </td>
      <td style="text-align:left">&#x52A0;&#x5165;&#x4E00;&#x500B;&#x5143;&#x4EF6;&#x65BC;<code>(r, c)</code>&#x76F8;&#x5C0D;&#x4F4D;&#x7F6E;&#x4E0A;</td>
    </tr>
    <tr>
      <td style="text-align:left"><b><code>addWidget(QWidget, int r, int c, int rowspan, int columnspan)</code></b>
      </td>
      <td style="text-align:left">
        <p>&#x52A0;&#x5165;&#x4E00;&#x500B;&#x5143;&#x4EF6;&#x65BC;<code>(r, c)</code>&#x76F8;&#x5C0D;&#x4F4D;&#x4F4D;&#x7F6E;&#x4E0A;&#xFF0C;</p>
        <p>&#x4E14;&#x53EF;&#x4EE5;&#x5C0D;&#x6B64;&#x5143;&#x4EF6;&#x505A;&#x7E2E;&#x6392;&#x3002;</p>
        <p><code>rowspan</code>&#x70BA;&#x8CA0;&#x6578;&#x4EE3;&#x8868;&#x8DE8;&#x5217;
          (<code>columnspa</code>&#x5247;&#x8DE8;&#x884C;)&#xFF0C;&#x8ACB;&#x53C3;&#x8003;&#x4E0B;&#x9762;&#x7BC4;&#x4F8B;</p>
      </td>
    </tr>
  </tbody>
</table>

```python
import sys
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *


def window():
    app = QApplication(sys.argv)
    win = QWidget()
    grid = QGridLayout()

    grid.addWidget(QPushButton("0,0"), 0, 0)
    grid.addWidget(QPushButton("0,1"), 0, 1)
    grid.addWidget(QPushButton("0,2"), 0, 2)
    
    # 第三個參數1: 維持一列
    # 第四個參數3: 延伸三行
    grid.addWidget(QPushButton("1,3"), 1, 0, 1, 3)    
    
    # 第三個參數-1: 橫跨列
    # 第四個參數 1: 維持一行
    grid.addWidget(QPushButton("2,0"), 2, 0, -1, 1)
    
    grid.addWidget(QPushButton("2,1"), 2, 1)
    grid.addWidget(QPushButton("2,2"), 2, 2)
    
    # 第三個參數-1: 橫跨列
    # 第四個參數-1: 橫跨行    
    grid.addWidget(QPushButton("3,1"), 3, 1, -1, -1)

    win.setLayout(grid)
    win.setWindowTitle("PyQt")
    win.show()
    sys.exit(app.exec_())


if __name__ == '__main__':
    window()
```

![](../../.gitbook/assets/image%20%287%29.png)

## Ref.

{% embed url="https://www.tutorialspoint.com/pyqt5/pyqt5\_qgridlayout\_class.htm" %}

{% embed url="https://www.delftstack.com/zh-tw/tutorial/pyqt5/pyqt-grid-layout/" %}





