# wx: splitterwindows

```python
import wx


class Mywin(wx.Frame):

    def __init__(self, parent, title):
        super(Mywin, self).__init__(parent, title=title, size=(350, 300))

        splitter = wx.SplitterWindow(self, -1)

        l_panel = wx.Panel(splitter, -1)
        r_panel = wx.Panel(splitter, -1)

        # left panel

        lst = wx.ListBox(
            l_panel,
            size=(100, 300),
            choices=['C', 'C++', 'Java', 'Python', 'Perl', 'JavaScript', 'PHP', 'VB.NET', 'C#'],
            style=wx.LB_SINGLE
        )
        l_hbox = wx.BoxSizer(wx.HORIZONTAL)
        l_hbox.Add(lst, 1)
        l_panel.SetSizer(l_hbox)
        
        # right panel

        self.text = wx.TextCtrl(r_panel, style=wx.TE_MULTILINE)
        r_hbox = wx.BoxSizer(wx.HORIZONTAL)
        r_hbox.Add(self.text, 1, wx.EXPAND)
        r_panel.SetSizerAndFit(r_hbox)


        splitter.SplitVertically(l_panel, r_panel)
        self.Centre()
        self.Bind(wx.EVT_LISTBOX, self.onListBox, lst)
        self.Show(True)

    def onListBox(self, event):
        self.text.AppendText("Current selection: " + event.GetEventObject().GetStringSelection() + "\n")

ex = wx.App()
Mywin(None, 'Splitter Demo - www.tw511.com')
ex.MainLoop()
```

## 執行wxSplitterwindow.SplitVertically，左側總是被收合？

{% embed url="https://stackoverflow.com/questions/32195823/wxpython-wxsplitterwindow-splitvertically-always-shows-uneven-split" %}

* `splitter.SplitVertically(l_panel, r_panel, 100)`

  第三個參數為正數，從左側開始預留的大小  
  第三個參數為負數，從右側開始預留的大小

若為`wxSplitterwindow.SplitHorizontally(l_panel, r_panel, 100)`，則  
第三個參數為正數，從底部開始預留的大小  
第三個參數為負數，從頂部開始預留的大小

## Ref.

{% embed url="http://www.tw511.com/3/48/1631.html" %}



{% embed url="https://www.blog.pythonlibrary.org/2013/10/18/wxpython-an-introduction-to-splitterwindows/" %}

{% embed url="https://wxpython.org/Phoenix/docs/html/wx.lib.agw.fourwaysplitter.html" caption="四格 fourwayspliter" %}









