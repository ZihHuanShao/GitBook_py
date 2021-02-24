# wx: GridBagSizer

```python
import wx
class Example(wx.Frame):
   def __init__(self, parent, title):
      super(Example, self).__init__(parent, title = title)
      self.InitUI()
      self.Centre()
      self.Show()

   def InitUI(self):
      panel = wx.Panel(self)

      sizer = wx.GridBagSizer(0,0)

      sizer.Add(wx.StaticText(panel, label = "Name:"), pos = (0, 0), flag = wx.ALL, border = 5)
      sizer.Add(wx.TextCtrl(panel), pos = (0, 1), span = (1, 2), flag = wx.EXPAND|wx.ALL, border = 5)

      sizer.Add(wx.StaticText(panel, label = "address"), pos = (1, 0), flag = wx.ALL, border = 5)
      sizer.Add(wx.TextCtrl(panel,style = wx.TE_MULTILINE), pos = (1,1), span = (1, 3), flag = wx.EXPAND|wx.ALL, border = 5)

      sizer.Add(wx.StaticText(panel,label = "age"), pos = (2, 0), flag = wx.ALL, border = 5)
      sizer.Add(wx.TextCtrl(panel), pos = (2,1), flag = wx.ALL, border = 5)
      sizer.Add(wx.StaticText(panel,label = "Mob.No"), pos = (2, 2), flag = wx.ALIGN_CENTER|wx.ALL, border = 5)
      sizer.Add(wx.TextCtrl(panel), pos = (2,3),flag = wx.EXPAND|wx.ALL, border = 5)

      sizer.Add(wx.StaticText(panel, label = "Description"), pos = (3, 0), flag = wx.ALL, border = 5)
      sizer.Add(wx.TextCtrl(panel,style =  wx.TE_MULTILINE), pos = (3,1), span = (1,3), flag = wx.EXPAND|wx.ALL, border = 5)
      sizer.AddGrowableRow(3)

      sizer.Add(wx.Button(panel, label = "Ok"), pos = (4, 2),flag = wx.ALL, border = 5)
      sizer.Add(wx.Button(panel, label = "Close" ), pos = (4, 3), flag = wx.ALL, border = 5)

      panel.SetSizerAndFit(sizer)

app = wx.App()
Example(None, title = 'GridBag Demo')
app.MainLoop()
```

## Ref.

{% embed url="https://iowiki.com/wxpython/wx\_gridbagsizer.html" %}



