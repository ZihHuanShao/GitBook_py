# event機制

## 一般的event binding

### Example

示範了三種綁定的方式

```python
import wx

class MyFrame(wx.Frame):
    def __init__(self):
        super().__init__(None, title='事件绑定')
        self.count = 0
        self.btn_add_counter = wx.Button(self, label='点击了0次')
        self.btn_reset_counter = wx.Button(self, label='重置计数器')
        self.btn_show_counter = wx.Button(self, label='显示计数器')

        self.sizer = wx.BoxSizer(wx.VERTICAL)
        self.sizer.AddStretchSpacer()
        self.sizer.Add(self.btn_add_counter, flag=wx.ALIGN_CENTER_HORIZONTAL|wx.BOTTOM, border=10)
        self.sizer.Add(self.btn_reset_counter, flag=wx.ALIGN_CENTER_HORIZONTAL|wx.BOTTOM, border=10)
        self.sizer.Add(self.btn_show_counter, flag=wx.ALIGN_CENTER_HORIZONTAL)
        self.sizer.AddStretchSpacer()
        self.SetSizer(self.sizer)

        self.Bind(wx.EVT_BUTTON, self._add_counter, self.btn_add_counter)
        self.Bind(wx.EVT_BUTTON, self._reset_counter, id=self.btn_reset_counter.Id)
        self.btn_show_counter.Bind(wx.EVT_BUTTON, self._show_counter)

    def _add_counter(self, e):
        print(e.Id == self.btn_add_counter.Id)
        self.count += 1
        self.btn_add_counter.SetLabel(f'点击了{self.count}次')

    def _reset_counter(self, e):
        print(e.Id == self.btn_reset_counter.Id)
        self.count = 0
        self.btn_add_counter.SetLabel('点击了0次')

    def _show_counter(self, e):
        print(e.Id == self.btn_show_counter.Id)
        wx.MessageBox(f'当前计数器：{self.count}', '提示')

app = wx.App()
MyFrame().Show()
app.MainLoop()
```

* **`AddStretchSpacer(prop=int)`**  
  `self.sizer.AddStretchSpacer()`意義類似`Box.Add(control, proportion, flag, border)`的`proportion`，只是這邊是預留多少比例的空白大小。  
  以此範例，若：

  `self.sizer.AddStretchSpacer(5)`

  `self.sizer.AddStretchSpacer(2)`  
  表示視窗畫面扣掉添加的三個按鈕的高度，剩餘的空白高度按比例分配留白的大小要多少。  
  上：佔了剩餘空白高度的5/7  
  下：佔了剩餘空白高度的2/7  
  若無參數則平均分配-&gt; 置中

此外，還有另一個`AddSpacer(50)`則是依照參數中的像素來留白，就不是按比例了。

## 自定義的event binding

### Example

1. **引入lib** `import wx.lib.newevent`
2. **建立自定義`event`** `GuessResultEvent, EVT_GUESS_RESULT = wx.lib.newevent.NewCommandEvent()` 
3. **產生`event`實例** `event = self.GuessResultEvent(self.Id, is_correct=correct, message=message)`
4. **發送`event`** `wx.PostEvent(self.GetEventHandler(), event)`
5. **接收並處理自定義`event`** `self.Bind(self.guess_panel.EVT_GUESS_RESULT, self._handle_result)`

```python
import wx
import random
import wx.lib.newevent

class GuessNumberPanel(wx.Panel):
    GuessResultEvent, EVT_GUESS_RESULT = wx.lib.newevent.NewCommandEvent()

    def __init__(self, parent):
        super().__init__(parent)
        self.number = random.randint(1, 100)

        self.sizer = wx.BoxSizer(wx.VERTICAL)
        self.sizer.Add(wx.StaticText(self, label='猜一个1到100之间的整数'), flag=wx.ALIGN_CENTER_HORIZONTAL|wx.TOP, border=20)

        self.btn_reset = wx.Button(self, label='重新开始')
        self.sizer.Add(self.btn_reset, flag=wx.ALIGN_CENTER_HORIZONTAL|wx.TOP, border=20)

        self.tc_guess = wx.TextCtrl(self)
        self.sizer.Add(self.tc_guess, flag=wx.ALIGN_CENTER_HORIZONTAL|wx.TOP, border=20)

        self.btn_guess = wx.Button(self, label='试一试')
        self.sizer.Add(self.btn_guess, flag=wx.ALIGN_CENTER_HORIZONTAL|wx.TOP|wx.BOTTOM, border=20)

        self.btn_reset.Bind(wx.EVT_BUTTON, self._reset)
        self.btn_guess.Bind(wx.EVT_BUTTON, self._check_result)

        self.SetSizer(self.sizer)
        self.SetBackgroundColour('#0099CC')

    def _reset(self, _):
        self.tc_guess.Clear()
        self.number = random.randint(1, 100)
        print(self.number)

    def _check_result(self, _):
        correct = False
        message = ''

        try:
            guessed_number = int(self.tc_guess.Value)
            if guessed_number < 1 or guessed_number > 100:
                message = '数字需要在1到100之间'
            elif guessed_number < self.number:
                message = '小了'
            elif guessed_number == self.number:
                message = '正确'
                correct = True
            else:
                message = '大了'
        except:
            message = '请输入数字'
        finally:
            event = self.GuessResultEvent(self.Id, is_correct=correct, message=message)
            print(self.Id)
            wx.PostEvent(self.GetEventHandler(), event)

class GuessNumberFrame(wx.Frame):
    def __init__(self):
        super().__init__(None, title='猜数字')
        self.guess_panel = GuessNumberPanel(self)
        self.st_guess_result = wx.StaticText(self)

        self.sizer = wx.BoxSizer()
        self.sizer.Add(self.guess_panel, proportion=1, flag=wx.EXPAND)
        self.sizer.Add(self.st_guess_result, proportion=1, flag=wx.TOP|wx.LEFT, border=30)
        self.SetSizer(self.sizer)

        self.Bind(self.guess_panel.EVT_GUESS_RESULT, self._handle_result)

    def _handle_result(self, e):
        print(e.message)
        if e.is_correct:
            self.st_guess_result.SetLabel('猜对了！')
        else:
            self.st_guess_result.SetLabel(e.message)

app = wx.App()
GuessNumberFrame().Show()
app.MainLoop()
```

## Ref.

{% embed url="https://zhuanlan.zhihu.com/p/107267271" %}

{% embed url="https://wxpython.org/Phoenix/docs/html/wx.CommandEvent.html" caption="wx提供的event類型" %}



