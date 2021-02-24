# wx: StaticBoxSizer

```python
import wx

class Mywin(wx.Frame):

   def __init__(self, parent, title):
      super(Mywin, self).__init__(parent, title = title)

      panel = wx.Panel(self)

      vBoxSizer = wx.BoxSizer(wx.VERTICAL)

      # Name 包裝兩個StaticText與TextCtrl，並填入標題"Name:"

      nameStaticBoxSizer = wx.StaticBoxSizer(wx.StaticBox(panel, -1, 'Name:'), wx.VERTICAL)

      nmbox = wx.BoxSizer(wx.HORIZONTAL)
      nmbox.Add(wx.StaticText(panel, -1, "First Name"), 0, wx.ALL|wx.CENTER, 5)
      nmbox.Add(wx.TextCtrl(panel, -1, style = wx.ALIGN_LEFT), 0, wx.ALL|wx.CENTER, 5)
      nmbox.Add(wx.StaticText(panel, -1, "Last Name"), 0, wx.ALL|wx.CENTER, 5)
      nmbox.Add(wx.TextCtrl(panel, -1, style = wx.ALIGN_LEFT), 0, wx.ALL|wx.CENTER, 5)

      nameStaticBoxSizer.Add(nmbox, 0, wx.ALL|wx.CENTER, 0)

      # Buttons 包裝兩個Button，並填入"Buttons:"

      buttonsStaticBoxSizer = wx.StaticBoxSizer(wx.StaticBox(panel, -1, 'Buttons:'), wx.VERTICAL)

      hbox = wx.BoxSizer(wx.HORIZONTAL)
      hbox.Add(wx.Button(panel, -1, 'ok'), 0, wx.ALL|wx.LEFT, 10)
      hbox.Add(wx.Button(panel, -1, 'cancel'), 0, wx.ALL|wx.LEFT, 10)

      buttonsStaticBoxSizer.Add(hbox, 0, wx.ALL|wx.LEFT, 10)

      vBoxSizer.Add(nameStaticBoxSizer,0, wx.ALL|wx.CENTER, 5)
      vBoxSizer.Add(buttonsStaticBoxSizer,0, wx.ALL|wx.CENTER, 5)

      # Set sizer to frame

      panel.SetSizer(vBoxSizer)

      self.Centre()
      panel.Fit()
      self.Show()

app = wx.App()
Mywin(None,  'staticboxsizer demo')
app.MainLoop()
```

## Ref.

{% embed url="https://iowiki.com/wxpython/wx\_staticboxsizer.html" caption="ch" %}

{% embed url="https://www.tutorialspoint.com/wxpython/wx\_staticboxsizer.htm" caption="en" %}



