# GIL \(Global Interpreter Lock\)

GIL為了達到\(偽\)同步的效果，都會先鎖住自己的thread，阻止別的thread執行，然後每隔一段時間，Python Interpretor 就會強制目前正在執行的thread去釋放鎖GIL，這樣別的thread才能有執行的機會。不斷交錯執行，來模擬真正thread的同步。

![](../.gitbook/assets/image%20%281%29.png)

以文中範例：

```python
import threading 

n = 0 
def foo(): 
    global n 
    n += 1 

threads = [] 
for i in range(100): 
    t = threading.Thread(target=foo) 
    threads.append(t) 
    
for t in threads: 
    t.start() 
    
for t in threads: 
    t.join() 
    
print(n)

```

如果執行的話，就會發現，儘管大部分時候它能夠列印100，但有時侯也會列印99或者98。

這是因為Python Interpretor檢查時間的機制，是以`bytecode`為單位，而`bytecode`這種單位是基於機器語言（類似可想成組合語言，一列指令為一個`bytecode`），下面範例是python語言`n+=1`在機器語言上的四行`bycode`指令

```python
LOAD_GLOBAL 0 (n) 
LOAD_CONST 1 (1) 
INPLACE_ADD 
STORE_GLOBAL 0 (n)
```

所以當執行緒在執行時，在這四行`bytecode`當中可能會因為Python Interpretor檢查的機制，覺得應該被切換了，而造成原應該要被執行的步驟被中斷，導致非預期的結果。

GIL的設計，主要是為了方便CPython解釋器層面的編寫者，而不是Python應用層面。

也因此才有其他lock的機制產生。

## Ref.

{% embed url="https://kknews.cc/code/2ngmeay.html" %}



