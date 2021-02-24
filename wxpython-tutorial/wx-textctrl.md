# wx: TextCtrl

```python
import wx


class Mywin(wx.Frame):
    def __init__(self, parent, title):
        super(Mywin, self).__init__(parent, title=title, size=(350, 250))

        panel = wx.Panel(self)
        vbox = wx.BoxSizer(wx.VERTICAL)

        hbox1 = wx.BoxSizer(wx.HORIZONTAL)
        hbox1.Add(wx.StaticText(panel, -1, "Text Field"), 1, wx.ALL, 5)
        t1 = wx.TextCtrl(panel)
        hbox1.Add(t1, 1,  wx.ALL, 5)
        t1.Bind(wx.EVT_TEXT, self.OnKeyTyped)
        vbox.Add(hbox1)

        hbox2 = wx.BoxSizer(wx.HORIZONTAL)
        hbox2.Add(wx.StaticText(panel, -1, "password field"), 1, wx.ALL, 5)
        t2 = wx.TextCtrl(panel, style=wx.TE_PASSWORD)
        hbox2.Add(t2, 1, wx.ALL, 5)
        vbox.Add(hbox2)
        t2.SetMaxLength(5)
        t2.Bind(wx.EVT_TEXT_MAXLEN, self.OnMaxLen)

        hbox3 = wx.BoxSizer(wx.HORIZONTAL)
        hbox3.Add(wx.StaticText(panel, -1, "Multiline Text"), 1, wx.ALL, 5)
        t3 = wx.TextCtrl(panel, size=(-1, 100), style=wx.TE_MULTILINE)
        hbox3.Add(t3, 1, wx.ALL, 5)
        vbox.Add(hbox3)
        # self.t3.Bind(wx.EVT_TEXT_ENTER, self.OnEnterPressed)

        hbox4 = wx.BoxSizer(wx.HORIZONTAL)
        hbox4.Add(wx.StaticText(panel, -1, "Read only text"), 1, wx.ALL, 5)
        self.t4 = wx.TextCtrl(panel, value="ReadOnly Text",style = wx.TE_READONLY|wx.TE_CENTER)
        hbox4.Add(self.t4, 1, wx.ALL, 5)
        vbox.Add(hbox4)

        panel.SetSizer(vbox)

        self.Centre()
        self.Show()
        self.Fit()

    def OnKeyTyped(self, event):
        print(event.GetString())

    def OnEnterPressed(self, event):
        print("Enter pressed")

    def OnMaxLen(self, event):
        print("Maximum length reached")


app = wx.App()
Mywin(None, 'TextCtrl demo')
app.MainLoop()
```

## Ref.

{% embed url="https://www.tutorialspoint.com/wxpython/wx\_textctrl\_class.htm" caption="en" %}

{% embed url="http://www.tw511.com/3/48/1622.html" caption="ch" %}





