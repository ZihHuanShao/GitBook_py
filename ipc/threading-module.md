# 內建 threading module

文章重點：

* 建立子執行緒
* 建立多個子執行緒與參數
* 使用物件導向
* Queue
  * **允許多個**子執行緒同時處理同一個queue裡的任務
* Lock
  * **僅允許一次一個**子執行緒處理queue裡的任務，且不允許此執行緒重複取得`lock`\(鎖定權\)，亦即這次`release`後就會釋放`lock`，讓其他執行緒有機會可以取得`lock`
* RLock
  * **僅允許一次一個**子執行緒處理queue裡的任務，但允許此執行緒重複取得`lock`\(鎖定權\)，亦即若某執行緒重複執行`acquire`兩次，就會等到此執行緒`release`兩次後才會釋放`lock`，讓其他執行緒有機會可以取得`lock`
* Semaphore
  * **允許有限個**子執行緒同時處理同一個queue裡的任務

## Ref.

{% embed url="https://blog.gtwang.org/programming/python-threading-multithreaded-programming-tutorial/" %}

{% embed url="https://www.runoob.com/python3/python3-multithreading.html" %}



