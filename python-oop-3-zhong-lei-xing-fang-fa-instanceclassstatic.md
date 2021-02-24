# Python OOP 3種類型方法\(Instance,Class,Static\)

* **實體方法\(Instance Method\)**
  * 沒有加任何裝飾詞\(Decorator\)的方法\(Method\)，至少要有一個self參數，於方法\(Method\)被呼叫時指向物件\(Object\)。透過`self`參數可以自由的存取物件\(Object\)的屬性\(Attribute\)及其他方法\(Method\)，藉此來改變物件\(Object\)的狀態
* **類別方法\(Class Method\)**
  * 有`@classmethod`裝飾詞\(Decorator\)的方法\(Method\)，被呼叫時，相較於實體方法\(Instance Method\)的self參數指向物件\(Object\)，類別方法\(Class Method\)為cls參數，指向類別\(Class\)。類別方法\(Class Method\)的`cls`參數指向類別\(Class\)，所以類別方法\(Class Method\)僅能改變類別的狀態，而無法改變物件\(Object\)的狀態，因為它沒有`self`參數可以存取物件的屬性\(Attribute\)及方法\(Method\)。
* **靜態方法\(Static Method\)**
  * 有`@staticmethod`裝飾詞\(Decorator\)的方法\(Method\)，可以接受任意的參數，也因為它沒有`self`及`cls`參數，所以靜態方法\(Static Method\)無法改變類別\(Class\)及物件\(Object\)的狀態。在類別\(Class\)中是一個獨立的方法\(Method\)，通常應用於方法\(Method\)中無需存取物件\(Object\)的屬性\(Attribute\)或方法\(Method\)，單純執行傳入參數或功能上運算的情況

## Ref.

{% embed url="https://www.learncodewithmike.com/2020/01/python-method.html" %}



