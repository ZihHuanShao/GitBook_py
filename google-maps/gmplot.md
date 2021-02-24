# gmplot

**gmplot** is a matplotlib-like interface to generate the HTML and javascript to render all the data user would like on top of Google Maps.

總之，就是將GoogleMaps的圖資訊息轉成`.html`檔

### [申請 GoogleMaps API 服務](https://cloud.google.com/maps-platform/)

申請完帳號，現在都必須提供信用卡資訊，才能允許建立專案。一般的服務google也會提供每個月折抵金額，若是練習用不太需要擔心會再額外付費。自訂專案名稱後，需要**建立憑證**與**啟用Maps JavaScript API服務**

![](../.gitbook/assets/image%20%2813%29.png)

![](../.gitbook/assets/image%20%2818%29.png)

![](../.gitbook/assets/image%20%2837%29.png)

![](../.gitbook/assets/image%20%284%29.png)

### EX

```python
import wx
import gmplot
import webbrowser
from pathlib import Path

class GMFrame(wx.Frame):
    def __init__(self, parent):
        wx.Frame.__init__(self, parent, title = "MyGoogleMap")

        panel = wx.Panel(self)

        # Create the map plotter:
        apikey = 'XXXXX'  # (your API key here)
        gmap = gmplot.GoogleMapPlotter(30.3164945, 78.03219179999999, 12, apikey=apikey)

        latitude_list = [30.3358376, 30.307977, 30.3216419]
        longitude_list = [77.8701919, 78.048457, 78.0413095]
        
        # 畫點
        gmap.scatter(latitude_list, longitude_list, '#FF0000', size=40, marker=False)
        
        # 畫線
        gmap.plot(latitude_list, longitude_list, 'cornflowerblue', edge_width=2.5)

        # 產出的檔名
        filename = 'map.html'
        
        # Draw the map to an HTML file:
        gmap.draw(filename)
        
        # 取得當前路徑
        currentPath = Path(__file__).parent.absolute()
        
        # 完整的檔案路徑
        fullFilePath = "file:///" + str(currentPath) + "/" + filename

        # 開啟瀏覽器瀏覽 google maps
        webbrowser.open_new_tab(fullFilePath)
        
        self.Show()

if __name__ == '__main__':

    app = wx.App(0)
    frame = GMFrame(None)
    app.MainLoop()
```

目前此方式是直接從瀏覽器開啟預覽，因網上也找不太到GoogleMaps embeded wxPython的資源，目標是希望能embeded python環境中，而**Pyqt**也是相當熱門的另一套python GUI 框架，且網上有使用googlemap相關的資源，考量後將重心轉移至Pyqt的學習。

## Ref.

{% embed url="https://github.com/gmplot/gmplot" %}



{% embed url="https://www.geeksforgeeks.org/python-plotting-google-map-using-gmplot-package/" caption="plotting on googlemap" %}







