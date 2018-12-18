---
title: Personalizzare gli eventi dell'heap ETW nativo | Microsoft Docs
ms.custom: 
ms.date: 02/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs: C++
ms.workload: cplusplus
ms.openlocfilehash: 7d55fdb061b9cb2fcd0497b7dde8e5c4255cf5e3
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="custom-native-etw-heap-events"></a>Personalizzare gli eventi dell'heap ETW nativo

Visual Studio contiene un'ampia gamma di [strumenti di profilatura e diagnostica](../profiling/profiling-tools.md), tra cui un profiler nativo della memoria.  Il profiler esegue l'hook degli [eventi ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) dal provider di heap e offre un'analisi delle modalità di allocazione e uso della memoria.  Per impostazione predefinita, questo strumento consente di analizzare solo le allocazioni effettuate dall'heap standard di Windows ed eventuali allocazioni esterne all'heap nativo non vengono visualizzate.

Vi sono molti i casi in cui può essere utile usare il proprio heap personalizzato ed evitare il sovraccarico di allocazioni dall'heap standard.  Ad esempio, è possibile usare [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) per allocare una grande quantità di memoria all'avvio dell'app o del gioco e quindi gestire i propri blocchi all'interno di tale elenco.  In questo scenario lo strumento profiler della memoria vedrà solo l'allocazione iniziale e non la gestione personalizzata eseguita all'interno del blocco di memoria.  Tuttavia, se si usa utilizza il provider ETW dell'heap nativo personalizzato, è possibile consentire allo strumento di sapere quali allocazioni vengono create all'esterno dell'heap standard.

Ad esempio, in un progetto simile al seguente in cui `MemoryPool` è un heap personalizzato, si vedrà solo una singola allocazione nell'heap di Windows:

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes 
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

Uno snapshot dello strumento [Utilizzo memoria](../profiling/memory-usage.md) senza rilevamento dell'heap personalizzato indicherebbe semplicemente la singola allocazione di 8192 byte e nessuna delle allocazioni personalizzate create dal pool:

![Allocazione di heap di Windows](media/heap-example-windows-heap.png)

La procedura riportata di seguito consente di usare questo strumento per verificare l'uso della memoria nell'heap personalizzato.

## <a name="how-to-use"></a>Uso

Questa libreria può essere usata facilmente in C e C++.

1. Includere l'intestazione per il provider ETW dell'heap personalizzato:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Aggiungere l'elemento Decorator `__declspec(allocator)` a qualsiasi funzione di gestione dell'heap personalizzato che restituisca un puntatore alla memoria heap appena allocata.  Questo elemento Decorator consente allo strumento di identificare correttamente il tipo di memoria da restituire.  Ad esempio:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```
   
   > [!NOTE]
   > L'elemento decorator indicherà al compilatore che questa funzione è una chiamata a un allocatore.  Ogni chiamata alla funzione restituirà l'indirizzo del sito di chiamata, la dimensione dell'istruzione di chiamata e il typeId del nuovo oggetto a un nuovo simbolo `S_HEAPALLOCSITE`.  Quando viene allocato uno stack di chiamate, Windows genera un evento ETW con queste informazioni.  Lo strumento profiler della memoria analizza lo stack di chiamate cercando un indirizzo mittente corrispondente a un simbolo `S_HEAPALLOCSITE` e le informazioni del typeId nel simbolo vengono usate per visualizzare il tipo di runtime dell'allocazione.
   >
   > In breve, questo significa che una chiamata simile a `(B*)(A*)MyMalloc(sizeof(B))` apparirà nello strumento come tipo `B`, non `void` o `A`.

1. Per C++, creare l'oggetto `VSHeapTracker::CHeapTracker` specificando un nome per l'heap, che verrà visualizzato nello strumento di profilatura:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Se si usa C, usare la funzione `OpenHeapTracker`.  Questa funzione restituirà un handle da usare quando si chiamano altre funzioni di rilevamento:
  
   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Per allocare la memoria con la funzione personalizzata, chiamare il metodo `AllocateEvent` (C++) o `VSHeapTrackerAllocateEvent` (C), passando il puntatore alla memoria e alle relative dimensioni, per verificare l'allocazione:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   oppure

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Non dimenticare di contrassegnare la funzione allocatore personalizzata con l'elemento Decorator `__declspec(allocator)` descritto in precedenza.

1. Per deallocare la memoria con la funzione personalizzata, chiamare la funzione `DeallocateEvent` (C++) o `VSHeapTracerDeallocateEvent` (C), passando il puntatore alla memoria, per verificare la deallocazione:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   oppure:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Per riallocare la memoria con la funzione personalizzata, chiamare il metodo `ReallocateEvent` (C++) o `VSHeapReallocateEvent` (C), passando un puntatore alla nuova memoria, la dimensione dell'allocazione e un puntatore alla memoria precedente:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   oppure:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Infine, per chiudere e pulire lo strumento di rilevamento dell'heap personalizzato in C++, usare il distruttore `CHeapTracker`, manualmente o con le regole di ambito standard, oppure la funzione `CloseHeapTracker` in C:

   ```cpp
   delete pHeapTracker;
   ```

   oppure:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="tracking-memory-usage"></a>Verificare l'uso della memoria
Dopo aver definito le chiamate, è possibile verificare l'uso dell'heap personalizzato con lo strumento **Utilizzo memoria** standard di Visual Studio.  Per altre informazioni sull'uso di questo strumento, vedere la documentazione relativa a [Utilizzo memoria](../profiling/memory-usage.md). Verificare di avere abilitato la profilatura dell'heap con gli snapshot, poiché altrimenti non verrà visualizzato l'uso dell'heap personalizzato. 

![Abilitare la profilatura dell'heap](media/heap-enable-heap.png)

Per visualizzare la verifica dell'heap personalizzato, usare l'elenco a discesa **Heap** situato in alto a destra nella finestra **Snapshot** e modificare la visualizzazione da *Heap NT* al proprio heap denominato in precedenza.

![Selezione dell'heap](media/heap-example-custom-heap.png)

Usando l'esempio di codice precedente, con `MemoryPool` che crea un oggetto `VSHeapTracker::CHeapTracker` e il metodo `allocate` che ora chiama il metodo `AllocateEvent`, ora appare il risultato dell'allocazione personalizzata, che indica 3 istanze per un totale di 24 byte, tutti di tipo `Foo`.

L'*heap NT* predefinito ha lo stesso aspetto di prima, con l'aggiunta dell'oggetto `CHeapTracker`.

![Heap NT con strumento di rilevamento](media/heap-example-windows-heap.png)

Come con l'heap standard di Windows, è possibile usare questo strumento per confrontare gli snapshot e verificare la presenza di spazi inutilizzati ed errori nell'heap personalizzato, descritto nella documentazione principale di [Utilizzo memoria](../profiling/memory-usage.md).

> [!TIP]
> Visual Studio contiene anche uno strumento **Utilizzo memoria** nel set di strumenti di **profilatura delle prestazioni** set di strumenti, che viene abilitato dall'opzione di menu **Debug > Profiler prestazioni** o dalla combinazione di tasti **Alt+F2**.  Questa funzionalità non include la verifica dell'heap e non visualizza l'heap personalizzato come descritto in questo documento.  Solo la finestra **Strumenti di diagnostica**, che può essere abilitata con il menu **Debug > Windows > Mostra strumenti di diagnostica** o la combinazione di tasti **Ctrl+Alt+F2**, contiene questa funzionalità.

## <a name="see-also"></a>Vedere anche
[Profiling Tools](../profiling/profiling-tools.md) (Strumenti di profilatura)  
[Utilizzo memoria](../profiling/memory-usage.md)
