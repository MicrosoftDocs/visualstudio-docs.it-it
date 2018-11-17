---
title: Tecniche di debug MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1e7a1ea69da1cafa38ae2a7bfa4551d3d40a8d4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745118"
---
# <a name="mfc-debugging-techniques"></a>Tecniche di debug MFC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si effettua il debug di un programma MFC, possono essere utili le seguenti tecniche di debug.  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 [AfxDebugBreak](#BKMK_AfxDebugBreak)  
  
 [Utilizzo della macro TRACE](#BKMK_The_TRACE_macro)  
  
 [Rilevamento di perdite di memoria in MFC](#BKMK_Memory_leak_detection_in_MFC)  
  
- [Gestione delle allocazioni di memoria](#BKMK_Tracking_memory_allocations)  
  
- [Abilitazione della diagnostica di memoria](#BKMK_Enabling_memory_diagnostics)  
  
- [Creazione di snapshot di memoria](#BKMK_Taking_memory_snapshots)  
  
- [Visualizzazione delle statistiche di memoria](#BKMK_Viewing_memory_statistics)  
  
- [Creazione di dump di oggetti](#BKMK_Taking_object_dumps)  
  
  - [Interpretazione dei dump di memoria](#BKMK_Interpreting_memory_dumps)  
  
  - [Personalizzazione di dump di oggetti](#BKMK_Customizing_object_dumps)  
  
    [Riduzione delle dimensioni di una build di debug di MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)  
  
  - [Compilazione di un'app MFC con informazioni di debug per i moduli selezionati](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)  
  
##  <a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak  
 MFC offre una speciale funzione [AfxDebugBreak](http://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) per programmare i punti di interruzione nel codice sorgente:  
  
```  
AfxDebugBreak( );  
  
```  
  
 Su piattaforme Intel `AfxDebugBreak` genera il seguente codice, che interrompe il codice sorgente anziché il codice kernel:  
  
```  
_asm int 3  
```  
  
 Su altre piattaforme, `AfxDebugBreak` richiama semplicemente `DebugBreak`.  
  
 Accertarsi di rimuovere le istruzioni `AfxDebugBreak` quando si crea una build di rilascio o si utilizza `#ifdef _DEBUG` per racchiuderle.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_TRACE_macro"></a> Utilizzo della macro TRACE  
 Per visualizzare i messaggi generati dal programma nella [finestra di output](../ide/reference/output-window.md)del debugger è possibile usare la macro [ATLTRACE](http://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e) oppure la macro [TRACE](http://msdn.microsoft.com/library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) MFC. Analogamente alle [asserzioni](../debugger/c-cpp-assertions.md)le macro di traccia sono attive solo nella versione di debug del programma e vengono annullate quando ne viene effettuata la compilazione nella versione di rilascio.  
  
 Gli esempi che seguono illustrano alcuni metodi di utilizzo della macro **TRACE** . Analogamente a `printf`la macro **TRACE** è in grado di gestire svariati argomenti.  
  
```  
int x = 1;  
int y = 16;  
float z = 32.0;  
TRACE( "This is a TRACE statement\n" );  
  
TRACE( "The value of x is %d\n", x );  
  
TRACE( "x = %d and y = %d\n", x, y );  
  
TRACE( "x = %d and y = %x and z = %f\n", x, y, z );  
```  
  
 Utilizzo della macro TRACE gestisce in modo appropriato char * e wchar_t\* parametri. Negli esempi seguenti viene illustrato l'utilizzo della macro TRACE, insieme ai diversi tipi di parametri di stringa.  
  
```  
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);  
  
TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);  
  
TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);  
  
```  
  
 Per altre informazioni sulla macro **TRACE** , vedere [Servizi diagnostici](http://msdn.microsoft.com/library/8d78454f-9fae-49c2-88c9-d3fabd5393e8).  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Memory_leak_detection_in_MFC"></a> Rilevamento di perdite di memoria in MFC  
 MFC offre classi e funzioni per il rilevamento della memoria allocata ma mai disallocata.  
  
###  <a name="BKMK_Tracking_memory_allocations"></a> Gestione delle allocazioni di memoria  
 In MFC è possibile usare la macro [DEBUG_NEW](http://msdn.microsoft.com/library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) anziché l'operatore **new** per un supporto nella ricerca di perdite di memoria. Nella versione di debug del programma, `DEBUG_NEW` tiene traccia del nome file e del numero di riga di ciascun oggetto da esso allocato. Quando si compila una versione di rilascio del programma, `DEBUG_NEW` si traduce in una semplice operazione **new** senza informazioni relative a nome file e numero di riga. La velocità non viene pertanto in alcun modo compromessa nella versione di rilascio del programma.  
  
 Se non si desidera riscrivere l'intero programma in modo da utilizzare `DEBUG_NEW` anziché **new**, sarà possibile definire questa macro nei file sorgente:  
  
```  
#define new DEBUG_NEW  
```  
  
 Quando si esegue un [dump di oggetti](#BKMK_Taking_object_dumps), ciascun oggetto allocato con `DEBUG_NEW` indicherà il file e il numero di riga in cui è stato allocato, consentendo di risalire all'origine delle perdite di memoria.  
  
 La versione di debug del framework MFC utilizza `DEBUG_NEW` automaticamente, a differenza del codice. Se si desidera godere dei vantaggi di `DEBUG_NEW`, sarà necessario utilizzare `DEBUG_NEW` esplicitamente oppure **#define new** come illustrato in precedenza.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Enabling_memory_diagnostics"></a> Abilitazione della diagnostica di memoria  
 Per poter utilizzare le utilità di diagnostica della memoria è necessario attivare la traccia diagnostica.  
  
 **Per abilitare o disabilitare la diagnostica della memoria**  
  
- Chiamare la funzione globale [AfxEnableMemoryTracking](http://msdn.microsoft.com/library/0a40e0c4-855d-46e2-9577-a8f2346f47db) per abilitare o disabilitare l'allocatore di memoria diagnostico. Dal momento che la diagnostica della memoria si trova per impostazione predefinita nella libreria di debug, in genere si ricorre a questa funzione per disattivare tale diagnostica temporaneamente, aumentando la velocità di esecuzione del programma e riducendo l'output di diagnostica.  
  
  **Per selezionare caratteristiche specifiche di diagnostica della memoria con afxMemDF**  
  
- Se si desidera godere di un maggior controllo sulle caratteristiche di diagnostica della memoria, sarà possibile attivare e disattivare selettivamente singole caratteristiche di diagnostica della memoria impostando il valore della variabile globale MFC [afxMemDF](http://msdn.microsoft.com/library/cf117501-5446-4fce-81b3-f7194bc95086). A questa variabile è possibile assegnare i seguenti valori, come specificato dal tipo enumerato **afxMemDF**.  
  
  |Valore|Descrizione|  
  |-----------|-----------------|  
  |**allocMemDF**|Attiva l'allocatore di memoria diagnostica (impostazione predefinita).|  
  |**delayFreeMemDF**|Liberare memoria quando si chiama `delete` o `free` solo dopo la chiusura del programma. In questo modo il programma allocherà la maggior quantità possibile di memoria.|  
  |**checkAlwaysMemDF**|Chiama [AfxCheckMemory](http://msdn.microsoft.com/library/4644da71-7d14-41dc-adc0-ee9558fd7a28) ogni volta che viene allocata o liberata memoria.|  
  
   È inoltre possibile usare combinazioni di questi valori eseguendo un'operazione OR logica, come illustrato di seguito:  
  
  ```cpp  
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;  
  ```  
  
  [In questo argomento](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_memory_snapshots"></a> Creazione di snapshot di memoria  
  
1. Creare un oggetto [CMemoryState](http://msdn.microsoft.com/en-us/8fade6e9-c6fb-4b2a-8565-184a912d26d2) e chiamare la funzione membro [CMemoryState::Checkpoint](http://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a) . Verrà creato il primo snapshot della memoria.  
  
2. Dopo che il programma ha eseguito le operazioni di allocazione e disallocazione di memoria, creare un altro oggetto `CMemoryState` e chiamare `Checkpoint` per tale oggetto. Verrà creato un secondo snapshot dell'utilizzo della memoria.  
  
3. Creare un terzo oggetto `CMemoryState` e chiamarne la funzione membro [CMemoryState::Difference](http://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) , fornendo come argomenti i due oggetti `CMemoryState` precedenti. Se esiste una differenza tra i due stati della memoria, la funzione `Difference` restituirà un valore diverso da zero, indicando così che alcuni blocchi di memoria non sono stati disallocati.  
  
    Il codice sarà del tipo riportato in questo esempio:  
  
   ```  
   // Declare the variables needed  
   #ifdef _DEBUG  
       CMemoryState oldMemState, newMemState, diffMemState;  
       oldMemState.Checkpoint();  
   #endif  
  
       // Do your memory allocations and deallocations.  
       CString s("This is a frame variable");  
       // The next object is a heap object.  
      CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
  
   #ifdef _DEBUG  
       newMemState.Checkpoint();  
       if( diffMemState.Difference( oldMemState, newMemState ) )  
       {  
           TRACE( "Memory leaked!\n" );  
       }  
   #endif  
   ```  
  
    Si noti che le istruzioni relative al controllo della memoria sono racchiuse in blocchi `#ifdef`[_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a)/ **#endif** in modo che vengano compilate solo nelle versioni di debug del programma.  
  
    Determinata l'esistenza di una perdita di memoria, sarà possibile usare un'altra funzione membro, [CMemoryState::DumpStatistics](http://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) , che consentirà di individuare la perdita.  
  
   [In questo argomento](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Viewing_memory_statistics"></a> Visualizzazione delle statistiche di memoria  
 La funzione [CMemoryState::Difference](http://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) esamina due oggetti stato di memoria e rileva eventuali oggetti non deallocati dall'heap tra gli stati iniziale e finale. Dopo aver creato snapshot di memoria e averli confrontati usando `CMemoryState::Difference`, è possibile chiamare [CMemoryState::DumpStatistics](http://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) per ottenere informazioni sugli oggetti non deallocati.  
  
 Si consideri l'esempio seguente:  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpStatistics();  
}  
```  
  
 Un dump campione sarà del seguente tipo:  
  
```  
0 bytes in 0 Free Blocks  
22 bytes in 1 Object Blocks  
45 bytes in 4 Non-Object Blocks  
Largest number used: 67 bytes  
Total allocations: 67 bytes  
```  
  
 I blocchi liberi rappresentano blocchi la cui deallocazione viene ritardata se `afxMemDF` è stato impostato su `delayFreeMemDF`.  
  
 I blocchi di oggetti ordinari, indicati alla seconda riga, rimangono allocati sull'heap.  
  
 I blocchi non di oggetti includono matrici e strutture allocate con `new`. In questo caso quattro blocchi non di oggetti sono stati allocati sull'heap ma non disallocati.  
  
 `Largest number used` indica la quantità massima di memoria utilizzata dal programma in qualsiasi momento.  
  
 `Total allocations` indica la quantità totale di memoria utilizzata dal programma.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_object_dumps"></a> Creazione di dump di oggetti  
 In un programma MFC, è possibile usare [CMemoryState:: DumpAllObjectsSince](http://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) per eseguire il dump una descrizione di tutti gli oggetti nell'heap non deallocati. `DumpAllObjectsSince` esegue il dump di tutti gli oggetti allocati dall'ultima [CMemoryState::Checkpoint](http://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a). Se non ha avuto luogo alcuna chiamata `Checkpoint` , `DumpAllObjectsSince` effettuerà il dump di tutti gli oggetti e non oggetti attualmente in memoria.  
  
> [!NOTE]
>  Prima di poter utilizzare il dump di oggetti MFC, è necessario [abilitare la traccia di diagnostica](../debugger/mfc-debugging-techniques.md#BKMK_Enabling_Memory_Diagnostics).  
  
> [!NOTE]
>  MFC effettua automaticamente il dump di tutti gli oggetti persi alla chiusura del programma, pertanto non è necessario creare codice per il dump degli oggetti in tale posizione.  
  
 Nel codice che segue si verifica la presenza di eventuali perdite di memoria confrontando due stati della memoria e si effettua il dump di tutti gli oggetti eventualmente persi.  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpAllObjectsSince();  
}  
```  
  
 Il contenuto del dump sarà del seguente tipo:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 I numeri tra parentesi graffe all'inizio della maggior parte delle righe specificano l'ordine in cui gli oggetti sono stati allocati. L'ultimo oggetto allocato presenta il numero più alto e si trova all'inizio del dump.  
  
 Per ottenere la quantità massima di informazioni da un dump di oggetti, è possibile eseguire l'override della funzione membro `Dump` di qualsiasi oggetto derivato da `CObject`per personalizzare il dump di oggetti.  
  
 È possibile definire un punto di interruzione su una particolare allocazione di memoria impostando la variabile globale `_afxBreakAlloc` sul numero indicato tra le parentesi graffe. Se si esegue nuovamente il programma il debugger interromperà l'esecuzione quando avrà luogo tale allocazione. Sarà quindi possibile esaminare lo stack di chiamate per sapere come il programma è giunto a tale punto.  
  
 La libreria di run-time del linguaggio C dispone di una funzione simile, [_CrtSetBreakAlloc](http://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1), che è possibile usare per le allocazioni di run-time del linguaggio C.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Interpreting_memory_dumps"></a> Interpretazione dei dump di memoria  
 Considerare questo dump di oggetti in maggior dettaglio:  
  
```  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Nel programma che ha generato questo dump erano presenti solo due allocazioni esplicite, una sullo stack e una sull'heap:  
  
```  
// Do your memory allocations and deallocations.  
CString s("This is a frame variable");  
// The next object is a heap object.  
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
```  
  
 Il costruttore `CPerson` accetta tre argomenti che rappresentano puntatori a `char`, utilizzati per inizializzare variabili membro `CString` . Nel dump della memoria è possibile individuare l'oggetto `CPerson` nonché tre blocchi non di oggetti (3, 4 e 5). Questi blocchi contengono i caratteri delle variabili membro `CString` e non verranno eliminati quando sarà chiamato il distruttore dell'oggetto `CPerson` .  
  
 Il blocco il numero 2 è l'oggetto `CPerson` stesso. `$51A4` rappresenta l'indirizzo del blocco ed è seguito dal contenuto dell'oggetto, restituito come output da `CPerson`::`Dump` quando è stato chiamato da [DumpAllObjectsSince](http://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2).  
  
 È chiaro che il blocco numero 1 è associato alla variabile di frame `CString` , in quanto presenta una sequenza di numero e dimensione che corrisponde al numero di caratteri della variabile di frame `CString` . Le variabili allocate sul frame vengono automaticamente disallocate quando il frame esce dall'ambito consentito.  
  
 **Variabili di frame**  
  
 In generale gli oggetti degli heap associati a variabili di frame non devono destare preoccupazioni, poiché vengono automaticamente disallocati quando le variabili di frame escono dall'ambito consentito. Per far sì che i dump di diagnostica della memoria non siano eccessivamente ingombranti, è opportuno inserire le chiamate a `Checkpoint` in modo che restino all'esterno dell'ambito delle variabili di frame. Inserire, ad esempio, il precedente codice di allocazione tra parentesi indicanti l'ambito, come illustrato di seguito:  
  
```  
oldMemState.Checkpoint();  
{  
    // Do your memory allocations and deallocations ...  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
}  
newMemState.Checkpoint();  
```  
  
 Dopo l'inserimento delle parentesi di ambito, il dump della memoria di questo esempio sarà il seguente:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
```  
  
 **Allocazioni di non oggetti**  
  
 Si noti che alcune allocazioni sono di oggetti (ad esempio `CPerson`) mentre altre sono allocazioni di non oggetti. Queste ultime sono allocazioni di oggetti non derivati da `CObject` o allocazioni di tipi C primitivi, ad esempio `char`, `int`o **long**. Se la classe derivata da **CObject-** alloca ulteriore spazio, ad esempio per buffer interni, questi oggetti presenteranno allocazioni di oggetti e di non oggetti.  
  
 **Prevenzione di perdite di memoria**  
  
 Si noti che nel codice precedente il blocco di memoria associato alla variabile di frame `CString` è stato disallocato automaticamente e non appare quindi come una perdita di memoria. La disallocazione automatica associata alle regole di ambito gestisce la maggior parte delle perdite di memoria associati alle variabili di frame.  
  
 Per gli oggetti allocati sull'heap, tuttavia, è necessario eliminare esplicitamente l'oggetto per impedire una perdita di memoria. Per eliminare l'ultima perdita di memoria dell'esempio precedente, eliminare l'oggetto `CPerson` allocato sull'heap, come segue:  
  
```  
{  
    // Do your memory allocations and deallocations.  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
    delete p;  
}  
```  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Customizing_object_dumps"></a> Personalizzazione di dump di oggetti  
 Quando si deriva una classe da [CObject](http://msdn.microsoft.com/library/95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a), è possibile eseguire l'override della funzione membro `Dump` per fornire ulteriori informazioni quando si usa [DumpAllObjectsSince](http://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) per eseguire il dump di oggetti nella [finestra Output](../ide/reference/output-window.md).  
  
 La funzione `Dump` scrive una rappresentazione testuale delle variabili membro dell'oggetto in un contesto di dump ([CDumpContext](http://msdn.microsoft.com/library/98c52b2d-14b5-48ed-b423-479a4d1c60fa)). Il contesto di dump è analogo a un flusso I/O. È possibile usare l'operatore APPEND (**<<**) per inviare dati a `CDumpContext`.  
  
 Quando si esegue l'override della funzione `Dump` , è opportuno chiamare dapprima la versione della classe base di `Dump` per effettuare il dump del contenuto dell'oggetto classe base, generando poi una descrizione testuale e un valore per ciascuna variabile membro della classe derivata.  
  
 La dichiarazione della funzione `Dump` sarà del seguente tipo:  
  
```  
class CPerson : public CObject  
{  
public:  
#ifdef _DEBUG  
    virtual void Dump( CDumpContext& dc ) const;  
#endif  
  
    CString m_firstName;  
    CString m_lastName;  
    // And so on...  
};  
```  
  
 Dal momento che il dump di oggetti ha senso solo quando si effettua il debug del programma, la dichiarazione della funzione `Dump` è racchiusa all'interno di un blocco **#ifdef _DEBUG / #endif** .  
  
 Nell'esempio che segue la funzione `Dump` chiama dapprima la funzione `Dump` della relativa classe base e poi scrive nel flusso diagnostico una breve descrizione di ciascuna variabile membro, insieme al valore del membro.  
  
```  
#ifdef _DEBUG  
void CPerson::Dump( CDumpContext& dc ) const  
{  
    // Call the base class function first.  
    CObject::Dump( dc );  
  
    // Now do the stuff for our specific class.  
    dc << "last name: " << m_lastName << "\n"  
        << "first name: " << m_firstName << "\n";  
}  
#endif  
```  
  
 È necessario fornire un argomento `CDumpContext` per specificare la posizione in cui verrà generato l'output del dump. La versione di debug di MFC offre un oggetto `CDumpContext` predefinito denominato `afxDump` che invia l'output al debugger.  
  
```  
CPerson* pMyPerson = new CPerson;  
// Set some fields of the CPerson object.  
//...  
// Now dump the contents.  
#ifdef _DEBUG  
pMyPerson->Dump( afxDump );  
#endif  
```  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Riduzione delle dimensioni di una build di debug di MFC  
 Le informazioni di debug di un'applicazione MFC di grandi dimensioni possono richiedere notevole spazio su disco. Per ridurre le dimensioni, è possibile usare una di queste procedure:  
  
1. Ricompilare le librerie MFC usando il [/Z7, /Zi, /ZI (formato informazioni di Debug)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) opzione, anziché **/Z7**. Queste opzioni compilano un singolo file di database di programma (PDB) che contiene informazioni di debug per l'intera libreria, riducendo la ridondanza e risparmiando spazio.  
  
2. Ricompilare le librerie MFC senza informazioni di debug (nessun [/Z7, /Zi, /ZI (formato informazioni di Debug)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) opzione). In questo caso la mancanza delle informazioni di debug impedirà di utilizzare la maggior parte delle utilità del debugger nel codice delle librerie MFC, ma dal momento che le librerie MFC sono già state sottoposte a un debug completo, questo non dovrebbe rappresentare un problema.  
  
3. Compilare l'applicazione con informazioni di debug solo per i moduli selezionati, come descritto di seguito.  
  
   [In questo argomento](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Compilazione di un'app MFC con informazioni di debug per i moduli selezionati  
 La compilazione di moduli selezionati con le librerie di debug MFC consente di eseguire i moduli un'istruzione alla volta e di utilizzare altre utilità di debug. In questa procedura vengono utilizzate sia la modalità debug che la modalità rilascio del makefile Visual C++. Per completarla, è necessario eseguire le modifiche descritte nei passaggi seguenti (nonché un'operazione di ricompilazione totale quando è richiesta una compilazione di rilascio completa).  
  
1. Selezionare il progetto in Esplora soluzioni.  
  
2. Scegliere **Pagine delle proprietà** dal menu **Visualizza**.  
  
3. Creare innanzitutto una nuova configurazione di progetto.  
  
   1.  Nel  **\<progetto > pagine delle proprietà** della finestra di dialogo fare clic sui **Configuration Manager** pulsante.  
  
   2.  Nella [finestra di dialogo Gestione configurazione](http://msdn.microsoft.com/en-us/fa182dca-282e-4ae5-bf37-e155344ca18b)individuare il progetto all'interno della griglia. Nel **Configuration** colonna, selezionare  **\<nuovo... >**.  
  
   3.  Nella [finestra di dialogo Nuova configurazione progetto](http://msdn.microsoft.com/en-us/cca616dc-05a6-4fe3-bdc1-40c72a66f2be)digitare, all'interno della casella **Nome configurazione progetto** , il nome da assegnare alla nuova configurazione, ad esempio "Debug parziale".  
  
   4.  Scegliere **Release** dall'elenco **Copia impostazioni da**.  
  
   5.  Fare clic su **OK** per chiudere la **nuova configurazione progetto**nella finestra di dialogo.  
  
   6.  Chiudere la finestra di dialogo **Gestione configurazione** .  
  
4. Impostare ora le opzioni desiderate per l'intero progetto.  
  
   1.  Nella finestra di dialogo **Pagine delle proprietà** , sotto la cartella **Proprietà di configurazione** , selezionare la categoria **Generale** .  
  
   2.  Nella griglia delle impostazioni del progetto espandere **Impostazioni predefinite progetto** (se necessario).  
  
   3.  In **Impostazioni predefinite progetto**trovare **Uso di MFC**. L'impostazione corrente verrà visualizzata nella colonna di destra della griglia. Fare clic sull'impostazione corrente e modificarla in **Usa MFC in una libreria statica**.  
  
   4.  Nel riquadro di sinistra della finestra di dialogo **Pagine delle proprietà** aprire la cartella **C/C++** e selezionare **Preprocessore**. Nella griglia delle proprietà cercare **Definizioni preprocessore** e sostituire "NDEBUG" con "_DEBUG".  
  
   5.  Nel riquadro di sinistra della finestra di dialogo **Pagine delle proprietà** aprire la cartella **Linker** e selezionare la categoria **Input** . Nella griglia delle proprietà cercare **Dipendenze aggiuntive**. Nell'impostazione **Dipendenze aggiuntive** digitare "NAFXCWD.LIB" e "LIBCMT."  
  
   6.  Scegliere **OK** per salvare le nuove opzioni di compilazione e chiudere la finestra di dialogo **Pagine delle proprietà** .  
  
5. Scegliere **Ricompila** dal menu **Compila**. Verranno così rimosse tutte le informazioni di debug dai moduli, ma non verrà apportata alcuna modifica alla libreria MFC.  
  
6. A questo punto è necessario aggiungere nuovamente le informazioni di debug ai moduli selezionati nell'applicazione. Tenere presente che è possibile impostare punti di interruzione ed eseguire altre funzioni di debug solo nei moduli che sono stati compilati con informazioni di debug. Per ciascun file di progetto in cui si desidera includere informazioni di debug, eseguire i seguenti passaggi:  
  
   1.  In Esplora soluzioni aprire la cartella **File di origine** sotto il progetto.  
  
   2.  Selezionare il file per il quale si desidera impostare informazioni di debug.  
  
   3.  Scegliere **Pagine delle proprietà** dal menu **Visualizza**.  
  
   4.  Nella finestra di dialogo **Pagine delle proprietà** , sotto la cartella **Impostazioni di configurazione** , aprire la cartella **C/C++** , quindi selezionare la categoria **Generale** .  
  
   5.  Nella griglia delle proprietà, trovare **formato informazioni di Debug.**  
  
   6.  Fare clic sulle impostazioni **Formato informazioni di debug** e selezionare l'opzione desiderata (in genere **/ZI**) per le informazioni di debug.  
  
   7.  Se si usa un'applicazione generata mediante una creazione guidata di applicazioni o si fa uso di intestazioni precompilate, sarà necessario disattivare tali intestazioni o compilarle nuovamente prima di compilare gli altri moduli. In caso contrario, verranno generati l'avviso C4650 e il messaggio di errore C2855. È possibile disattivare le intestazioni precompilate modificando il **Crea/Usa intestazioni precompilate** impostazione nelle  **\<progetto > proprietà** nella finestra di dialogo (**le proprietà di configurazione**  cartella **C/C++** sottocartella **intestazioni precompilate** categoria).  
  
7. Scegliere **Compila** dal menu **Compila** per compilare nuovamente i file di progetto non aggiornati.  
  
   In alternativa alla tecnica descritta in questo argomento è possibile usare un makefile esterno per definire singole opzioni per ciascun file. In tal caso, per collegarsi alle librerie di debug MFC, sarà necessario definire il flag [_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) per ciascun modulo. Per utilizzare le librerie di rilascio MFC, è necessario definire NDEBUG. Per altre informazioni sulla scrittura di makefile esterni, vedere [Riferimenti a NMAKE](http://msdn.microsoft.com/library/0421104d-8b7b-4bf3-86c1-928d9b7c1a8c).  
  
   [In questo argomento](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di Visual C++](../debugger/debugging-native-code.md)



