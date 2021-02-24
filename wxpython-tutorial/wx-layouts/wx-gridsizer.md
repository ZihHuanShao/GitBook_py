# wx: GridSizer

```python
import wx

class Example(wx.Frame):

    def __init__(self, parent, title):
        super(Example, self).__init__(parent, title=title, size=(300, 200))

        self.InitUI()
        self.Centre()
        self.Show()

    def InitUI(self):
        p = wx.Panel(self)

        gs = wx.GridSizer(4, 4, 5, 10)

        for i in range(1, 17):
            subp = wx.Panel(p)
            subp.SetBackgroundColour("red")
            gs.Add(subp, 0, wx.EXPAND)

            p.SetSizer(gs)


app = wx.App()
Example(None, title='Grid Demo')
app.MainLoop()
```

`gs = wx.GridSizer(4, 4, 5, 10)`，其中間距大小`5`為vgap，`10`為hgap

![](../../.gitbook/assets/image%20%2820%29.png)

## Ref.

{% embed url="http://www.tw511.com/3/48/1636.html" %}



