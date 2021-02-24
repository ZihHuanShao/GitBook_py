# wx: grid.Grid

```python
import wx
import wx.grid

class GridFrame(wx.Frame):
    def __init__(self, parent):
        wx.Frame.__init__(self, parent)

        # Create a wxGrid object
        grid = wx.grid.Grid(self, -1)

        # 建立 10 rows 與 5 cols
        grid.CreateGrid(10, 5)

        # 設定 row 0 標題
        # grid.SetRowLabelValue(0, "item 0")

        # 設定 col 0~4 標題
        grid.SetColLabelValue(0, "授權編號")
        grid.SetColLabelValue(1, "IMEI碼")
        grid.SetColLabelValue(2, "生效日")
        grid.SetColLabelValue(3, "到期日")
        grid.SetColLabelValue(4, "狀態")

        # 設定 row 3 高度60
        grid.SetRowSize(3, 60)

        # 設定 col 0~4 寬度
        grid.SetColSize(0, 350)
        grid.SetColSize(1, 150)
        grid.SetColSize(2, 150)
        grid.SetColSize(3, 150)
        grid.SetColSize(4, 50)

        # 設定(0, 0)~(0, 4) value
        grid.SetCellValue(0, 0, 'POC-00000000-0000-0000-0000-000000000000')
        grid.SetCellValue(0, 1, '000000000000000')
        grid.SetCellValue(0, 2, '2020-12-11 00:00')
        grid.SetCellValue(0, 3, '2021-12-11 00:00')
        grid.SetCellValue(0, 4, '使用中')

        # 設定(0, 3) value 唯讀
        grid.SetReadOnly(0, 3)

        # 設定(3, 3) value
        grid.SetCellValue(3, 3, 'hello')
        # 設定(3, 3) value color
        grid.SetCellTextColour(3, 3, wx.GREEN)
        # 設定(3, 3) background color
        grid.SetCellBackgroundColour(3, 3, wx.LIGHT_GREY)

        # 設定 col 5 value, 寬度大小6, 小數點精度2位
        grid.SetColFormatFloat(5, 6, 2)

        # binding event: 點擊任意cell印出位置
        self.Bind(wx.grid.EVT_GRID_SELECT_CELL, self.cellChanged, grid)

        self.Show()

    def cellChanged(self, event):
        print(str(event.Row) + "," + str(event.Col))

if __name__ == '__main__':

    app = wx.App(0)
    frame = GridFrame(None)
    app.MainLoop()
```

上面示範點擊某個cell就會印出對應的位置。但下方連結中範例的`wx.EVT_GRID_SELECT_CELL`必須改成`wx.grid.EVT_GRID_SELECT_CELL`，要加上**`grid`**否則抓不到`EVT_GRID_SELECT_CELL`變數。

grid還有其他類型的事件可以運用，參考[這裏](https://wxpython.org/Phoenix/docs/html/wx.grid.GridEvent.html)。

![](../.gitbook/assets/image%20%2811%29.png)

## Ref.

{% embed url="https://blog.csdn.net/soslinken/article/details/79024938" %}



