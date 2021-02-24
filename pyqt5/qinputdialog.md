# QInputDialog

`QInputDialog`提供一簡易介面，包含一個輸入框\(text field\) 與 兩個按鈕\(**OK** and **Cancel**\)。有以下幾種類型：

* 整數**getInt\(\)**
* 浮點數**getDouble\(\)**
* 文字輸入**getText\(\)**
* 選項**getItem\(\)**

這些類型會回傳一個`tuple (item, status)`：

* `item`: user輸入\(或選擇\)的訊息
* `status`: 返回狀態，user若點擊**OK**則回傳`true`，點擊**Cancel**回傳`false`

## Ref.

{% embed url="https://www.tutorialspoint.com/pyqt5/pyqt5\_qinputdialog\_widget.htm" %}



