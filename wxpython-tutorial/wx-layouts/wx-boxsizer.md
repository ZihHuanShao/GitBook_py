---
description: BoxSizer可以將元件一起排列在同一列或者同一行
---

# wx: BoxSizer

### 範例Error

範例中有一行會造成無法執行：

```python
vbox.Add(l1, 0,  wx.ALL|wx.EXPAND|wx.ALIGN_CENTER_HORIZONTAL, 20)
```

**`wx.ALL`**`|`**`wx.EXPAND`**`|`**`wx.ALIGN_CENTER_HORIZONTAL`**這三種組合無法同時存在

* **`wx.ALL`**
  * 相對所有\(包含上`wx.TOP`, 下`wx.BOTTOM`, 左`wx.LEFT`, 右`wx.RIGHT`\)的邊界距離，最右邊參數則是要距離多遠
* **`wx.EXPAND`**
  * **水平方向建立box**`wx.BoxSizer(wx.HORIZONTAL)`，延伸填滿視窗**高度**
  * **垂直方向建立box**`wx.BoxSizer(wx.VERTICAL)`，延伸填滿視窗**寬度**
* **`wx.ALIGN_CENTER_HORIZONTAL`**
  * 水平置中

無效組合：`wx.EXPAND|wx.ALIGN_CENTER_HORIZONTAL`

### 參數解釋

```python
Box.Add(control, proportion, flag, border)
```

* 第一個參數
  * wx widget instance，如：
    * `lb = wx.StaticText(..)` 或
    * `panel = wx.Panel(self) subPanel = wx.Panel(panel)` ，注意此instance為巢狀式`Panel()`的instance
* 第二個參數

  一個縮放的比例值。佔根據建立的BoxSizer instance其所有widget的`proportion`總和的比例。即`比例值/proportion總和`。如：

```python
import wx

class Example(wx.Frame):

    def __init__(self, parent, title):
        super(Example, self).__init__(parent, title=title)

        self.InitUI()
        self.Centre()
        self.Show()

    def InitUI(self):
        vbox = wx.BoxSizer(wx.HORIZONTAL)

        panel = wx.Panel(self)
        panel.SetBackgroundColour('black')
        
        p1 = wx.Panel(panel)
        p1.SetBackgroundColour('yellow')

        p2 = wx.Panel(panel)
        p2.SetBackgroundColour('red')

        vbox.Add(p1, 1, wx.EXPAND, 0)
        vbox.Add(p2, 2, wx.EXPAND, 0)

        panel.SetSizer(vbox)

app = wx.App()
Example(None, title='Demo')
app.MainLoop()
```

`p1`佔了總畫面的1/3，`p2`佔了總畫面的2/3：

![](../../.gitbook/assets/image%20%288%29.png)

若將`vbox = wx.BoxSizer(wx.HORIZONTAL)`改為`vbox = wx.BoxSizer(wx.VERTICAL)`：

![](../../.gitbook/assets/image%20%2814%29.png)

* 第三個參數 調整此widget的排版。如：距離邊界多遠、填滿畫面、置中等等
* 第四個參數 相對於第三個參數，若第三個參數是有需要帶參數的，則此參數就有意義。如 把上述範例的12行、13行 改成： `vbox.Add(p1, 1, wx.EXPAND|wx.ALL , 10)  vbox.Add(p2, 2, wx.EXPAND|wx.TOP, 50)`

![](../../.gitbook/assets/image%20%2833%29.png)



## Ref.

{% embed url="https://www.tutorialspoint.com/wxpython/wx\_boxsizer.htm" caption="en" %}

{% embed url="http://www.tw511.com/3/48/1635.html" caption="ch" %}

{% embed url="https://wxpython.org/Phoenix/docs/html/sizers\_overview.html" %}



