# 內建 multiprocessing module

* Pool 提供同時多個平行處理的 Processes 數，例如 Pool\(4\) 則代表會有 4 個平行處理的 Processes 。
* Exchanging objects
  * Queues
  * Pipes
* Shared memory
  * 兩種方式：Data can be stored in a shared memory map using **`Value`** or **`Array`**
* Synchronization機制 使用`lock`確保一次只能有一個process對共享資料存取，否則，若同時多個processes對同一個共享的資料寫入，會造成資料混淆。
* Manager 提供一種可以在不同processes之間共享的數據的方法。 相比Shared memory的方式更彈性，支援更多類型：A manager returned by `Manager()` will support types `list`, `dict`, `Namespace`, `Lock`, `RLock`, `Semaphore`, `BoundedSemaphore`, `Condition`, `Event`, `Barrier`, `Queue`, `Value` and `Array`其中也已包含Synchronization機制。 

## Ref.

{% embed url="https://myapollo.com.tw/zh-tw/python-multiprocessing/" %}

{% embed url="https://docs.python.org/3/library/multiprocessing.html\#module-multiprocessing" %}

{% embed url="https://www.maxlist.xyz/2020/03/20/multi-processing-pool/" %}





