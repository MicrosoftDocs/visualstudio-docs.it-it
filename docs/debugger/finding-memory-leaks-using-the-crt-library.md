---
title: Ricerca di perdite di memoria tramite la libreria CRT | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d858b6c67893e49b4d4e9ec87c3b20fce56dd7c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Individuazione di perdite di memoria tramite la libreria CRT
Uno dei bug più gravi e difficili da rilevare nelle applicazioni C/C++ è rappresentato dalle perdite di memoria, ovvero dall'impossibilità di deallocare correttamente la memoria allocata in precedenza. Una piccola perdita di memoria potrebbe passare inosservata, ma nel tempo può causare problemi come un calo delle prestazioni o l'arresto anomalo in caso di completo esaurimento della memoria. Nel peggiore dei casi, un'applicazione che usa tutta la memoria disponibile può causare l'arresto di un'altra applicazione, rendendo più difficile l'individuazione dell'applicazione responsabile del problema. Anche le perdite di memoria apparentemente inoffensive possono essere indice di altri problemi che è necessario correggere.  
  
 Il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e le librerie di runtime C (CRT) offrono gli strumenti necessari per rilevare e identificare le perdite di memoria.  
  
## <a name="enabling-memory-leak-detection"></a>Attivazione del rilevamento di perdite di memoria  
 I principali strumenti per il rilevamento delle perdite di memoria sono il debugger e le funzioni degli heap di debug delle librerie di runtime del linguaggio C (CRT, C Run-Time Libraries).  
  
 Per attivare le funzioni degli heap di debug, includere le seguenti istruzioni nel programma:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Affinché le funzioni CRT funzionino correttamente, le istruzioni `#include` devono seguire l'ordine qui indicato.  
  
 Includendo crtdbg.h, si esegue il mapping delle funzioni `malloc` e [free](/cpp/c-runtime-library/reference/free) alle corrispondenti versioni di debug, [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) e `free`, che consentono di tenere traccia dell'allocazione e della deallocazione della memoria. Questa operazione di mapping viene eseguita solo nelle build di debug che presentano `_DEBUG`. Le build di rilascio usano le normali funzioni `malloc` e `free` .  
  
 L'istruzione `#define` esegue il mapping di una versione di base delle funzioni di heap CRT alla corrispondente versione di debug. Se si omette l'istruzione `#define` , il dump della perdita di memoria sarà meno dettagliato.  
  
 Dopo avere abilitato le funzioni heap di debug tramite queste istruzioni, è possibile effettuare una chiamata a `_CrtDumpMemoryLeaks` prima del punto di uscita dell'applicazione per visualizzare un report sulle perdite di memoria alla chiusura dell'applicazione:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Se l'applicazione presenta più uscite, non è necessario effettuare manualmente una chiamata a [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) a ogni punto di uscita. Una chiamata a `_CrtSetDbgFlag` all'inizio dell'applicazione determina una chiamata automatica a `_CrtDumpMemoryLeaks` a ogni punto di uscita. È necessario impostare i due campi di bit indicati di seguito:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Per impostazione predefinita, `_CrtDumpMemoryLeaks` genera il report delle perdite di memoria nel riquadro **Debug** della finestra **Output** . È possibile usare `_CrtSetReportMode` per reindirizzare il report in un'altra posizione.  
  
 Se si usa una libreria, è possibile che l'output venga indirizzato in un'altra posizione. In questo caso, è possibile reimpostare la posizione dell'output sulla finestra **Output** , come illustrato di seguito:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretazione del report delle perdite di memoria  
 Se `_CRTDBG_MAP_ALLOC`non viene definito, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) visualizza un report delle perdite di memoria simile al seguente:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Se `_CRTDBG_MAP_ALLOC`viene definito, il report delle perdite di memoria sarà simile al seguente:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 La differenza consiste nel fatto che il secondo report mostra il nome del file e il numero di riga in cui la memoria persa era stata allocata.  
  
 Che `_CRTDBG_MAP_ALLOC` sia stato o meno definito, nel report delle perdite di memoria verranno visualizzate le informazioni seguenti:  
  
-   Numero di allocazione della memoria, che in questo esempio è `18`  
  
-   [Tipo di blocco](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97)che in questo esempio è `normal` .  
  
-   Posizione esadecimale della memoria che in questo esempio è `0x00780E80` .  
  
-   Dimensioni del blocco, `64 bytes` in questo esempio.  
  
-   I primi 16 byte di dati nel blocco, in formato esadecimale.  
  
 Il report delle perdite di memoria identifica un blocco di memoria come normale, client o CRT. Un *blocco normale* è dato da memoria ordinaria allocata dal programma. Un *blocco client* è un tipo speciale di blocco di memoria usato dai programmi MFC per oggetti che richiedono un distruttore. L'operazione MFC `new` crea un blocco normale o un blocco client, a seconda dell'oggetto creato. Un *blocco CRT* è allocato dalla libreria CRT per il proprio uso. La deallocazione di questi blocchi è gestita dalla libreria CRT. È quindi improbabile che vengano indicati nel report delle perdite di memoria, a meno il problema non sia davvero serio, ad esempio la libreria CRT è danneggiata.  
  
 Esistono altri due tipi di blocchi di memoria che non compaiono mai nei report delle perdite di memoria. Un *blocco libero* è dato da memoria rilasciata. Per definizione non si tratta quindi di perdita. Un *blocco da ignorare* è dato da memoria che è stata esplicitamente contrassegnata per essere esclusa dal report delle perdite di memoria.  
  
 Queste tecniche sono appropriate per la memoria allocata tramite la funzione `malloc` CRT standard. Se il programma di memoria allocata tramite C++ `new` (operatore), tuttavia, è possibile visualizzare solo il numero di riga e file in cui l'implementazione di globale `operator new` chiamate `_malloc_dbg` nel report delle perdite di memoria. Poiché questo comportamento non è molto utile, è possibile modificare in modo da segnalare la riga che ha effettuato l'allocazione utilizzando una macro simile al seguente: 
 
```C++  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Ora è possibile sostituire il `new` operatore tramite il `DBG_NEW` (macro) nel codice. Nelle build di debug, utilizza un overload di globale `operator new` che accetta parametri aggiuntivi per il tipo di blocco, i file e numero di riga. Questo overload di `new` chiamate `_malloc_dbg` per registrare le informazioni aggiuntive. Quando si utilizza `DBG_NEW`, la perdita di memoria report mostra il nome di file e numero di riga in cui sono stati allocati gli oggetti persi. Nelle build di vendita al dettaglio, viene utilizzato il valore predefinito `new`. (Non è consigliabile creare una macro del preprocessore denominata `new`, o qualsiasi altra parola chiave del linguaggio.) Di seguito è riportato un esempio della tecnica:  
  
```C++  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  
  
Quando si esegue questo codice nel debugger di Visual Studio, la chiamata a `_CrtDumpMemoryLeaks` genera un report nel **Output** finestra simile al seguente:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Indica che l'allocazione persa era nella riga 20 di debug_new.cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Impostazione di punti di interruzione su un numero di allocazione della memoria  
 Il numero di allocazione della memoria indica quando è stato allocato un blocco di memoria di cui è stata registrata la perdita. Un blocco con un numero di allocazione della memoria pari a 18, ad esempio, corrisponde al diciottesimo blocco di memoria allocato durante l'esecuzione dell'applicazione. Il report CRT tiene conto di tutte le allocazioni di blocchi di memoria durante l'esecuzione. Sono incluse le allocazioni della libreria CRT e di altre librerie come MFC. Di conseguenza, un blocco con un numero di allocazione della memoria pari a 18 potrebbe non essere il diciottesimo blocco di memoria allocato dal codice. In genere, non lo è.  
  
 È possibile usare il numero di allocazione per impostare un punto di interruzione sull'allocazione di memoria.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Per impostare un punto di interruzione dell'allocazione di memoria usando la finestra Espressioni di controllo  
  
1.  Impostare un punto di interruzione in prossimità dell'inizio dell'applicazione, quindi avviare l'applicazione.  
  
2.  Quando l'applicazione si interrompe al punto di interruzione, viene visualizzata la finestra **Espressioni di controllo** .  
  
3.  Nella finestra **Espressioni di controllo** digitare `_crtBreakAlloc` nella colonna **Nome** .  
  
     Se si usa la versione DLL multithread della libreria CRT (opzione /MD), includere l'operatore di contesto `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4.  Premere **INVIO**.  
  
     Il debugger valuterà la chiamata e ne visualizzerà il risultato nella colonna **Valore** . Questo valore sarà -1 se non è stato impostato alcun punto di interruzione su allocazioni di memoria.  
  
5.  Nella colonna **Valore** sostituire il valore visualizzato con il numero di allocazione della memoria in corrispondenza del quale si vuole effettuare l'interruzione.  
  
 Dopo avere impostato un punto di interruzione su un numero di allocazione della memoria, è possibile continuare con il debug. Fare attenzione a eseguire il programma nelle stesse condizioni dell'esecuzione precedente, in modo che l'ordine di allocazione della memoria non venga modificato. Quando il programma si interrompe all'allocazione di memoria specificata, è possibile usare la finestra **Stack di chiamate** e altre finestre del debugger per determinare in quali condizioni è stata allocata la memoria. È quindi possibile continuare l'esecuzione per osservare ciò che accade all'oggetto e determinare perché la relativa deallocazione non avviene correttamente.  
  
 Anche l'impostazione di un punto di interruzione dei dati sull'oggetto può essere utile. Per altre informazioni, vedere [Using Breakpoints](../debugger/using-breakpoints.md).  
  
 È anche possibile impostare i punti di interruzione dell'allocazione di memoria nel codice. Questo risultato può essere raggiunto in due modi:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 oppure:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Confronto tra stati di memoria  
 Un'altra tecnica per l'individuazione delle perdite di memoria comporta l'esecuzione di snapshot dello stato della memoria dell'applicazione in corrispondenza di punti chiave. Per eseguire uno snapshot dello stato della memoria in un determinato punto dell'applicazione, creare una struttura **_CrtMemState** e passarla alla funzione `_CrtMemCheckpoint` . Questa funzione inserisce nella struttura uno snapshot dello stato corrente della memoria:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 La funzione`_CrtMemCheckpoint` inserisce nella struttura uno snapshot dello stato corrente della memoria.  
  
 Per generare il contenuto di una struttura **_CrtMemState** , passare la struttura alla funzione `_ CrtMemDumpStatistics` :  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` genera un dump dello stato di memoria simile al seguente:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Per verificare se si è verificata una perdita di memoria in una sezione di codice, è possibile eseguire snapshot dello stato della memoria prima e dopo la sezione, quindi usare `_ CrtMemDifference` per confrontare i due stati:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` confronta gli stati di memoria `s1` e `s2` e restituisce un risultato in (`s3`), ovvero la differenza tra `s1` e `s2`.  
  
 Una tecnica per l'individuazione delle perdite di memoria prevede chiamate `_CrtMemCheckpoint` all'inizio e alla fine dell'applicazione, quindi l'uso di `_CrtMemDifference` per confrontare i risultati. Se `_CrtMemDifference` individua una perdita di memoria, è possibile aggiungere altre chiamate `_CrtMemCheckpoint` per dividere il programma usando una ricerca binaria finché non viene isolata l'origine della perdita.  
  
## <a name="false-positives"></a>Falsi positivi  
 È possibile che, in alcuni casi, vengano date da `_CrtDumpMemoryLeaks` false indicazioni di perdite di memoria. Questa situazione può verificarsi quando si usa una libreria che contrassegna allocazioni interne come _NORMAL_BLOCK e non come `_CRT_BLOCK`o `_CLIENT_BLOCK`. In questo caso, `_CrtDumpMemoryLeaks` non è in grado di indicare la differenza tra allocazioni utente e allocazioni interne della libreria. Se i distruttori globali relativi alle allocazioni della libreria vengono eseguiti dopo il punto in cui viene chiamato `_CrtDumpMemoryLeaks`, ogni allocazione interna della libreria viene segnalata come perdita di memoria. Nelle versioni precedenti della libreria di modelli standard, prima di Visual Studio .NET, venivano segnalati falsi positivi da `_CrtDumpMemoryLeaks` . Nelle versioni più recenti il problema è stato risolto.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni dettagliate sull'Heap di Debug CRT](../debugger/crt-debug-heap-details.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
