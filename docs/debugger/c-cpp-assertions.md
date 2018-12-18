---
title: Asserzioni C/C++ | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a53c03f1ab2c8680329f17bfa36a49b12062bff5
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="cc-assertions"></a>Asserzioni C/C++
Un'istruzione di asserzione specifica una condizione che si prevede abbia valore true in un punto del programma. Se tale condizione non è true, l'asserzione ha esito negativo, viene interrotta l'esecuzione del programma e [finestra di dialogo Asserzione non riuscita](../debugger/assertion-failed-dialog-box.md) viene visualizzato.  
  
 Visual C++ supporta le istruzioni di asserzione sono basate sui costrutti seguenti:  
  
-   Asserzioni MFC per programmi MFC.  
  
-   [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) per programmi che utilizzano ATL.  
  
-   Asserzioni CRT per programmi che utilizzano la libreria di runtime C.  
  
-   ANSI [funzione di asserzione](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) per altri programmi C/C++.  
  
 È possibile utilizzare le asserzioni per rilevare errori logici, controllare i risultati di un'operazione e verificare le condizioni di errore che avrebbero dovuto essere gestite.  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 [Funzionamento di asserzioni](#BKMK_How_assertions_work)  
  
 [Asserzioni nelle build di Debug e rilascio](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [Effetti collaterali di utilizzo di asserzioni](#BKMK_Side_effects_of_using_assertions)  
  
 [Asserzioni CRT](#BKMK_CRT_assertions)  
  
 [Asserzioni MFC](#BKMK_MFC_assertions)  
  
-   [ASSERT_VALID e CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [Limitazioni di AssertValid](#BKMK_Limitations_of_AssertValid)  
  
 [Utilizzo di asserzioni](#BKMK_Using_assertions)  
  
-   [Rilevamento di errori logici](#BKMK_Catching_logic_errors)  
  
-   [Controllo dei risultati](#BKMK_Checking_results_)  
  
-   [Errori non gestiti](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a>Funzionamento di asserzioni  
 Quando il debugger si interrompe a causa di un'asserzione di libreria run-time C o MFC, quindi se l'origine è disponibile, il debugger passa al punto nel file di origine in cui si è verificata l'asserzione. Asserzione viene visualizzato il messaggio sia il [finestra di Output](../ide/reference/output-window.md) e **asserzione non riuscita** la finestra di dialogo. È possibile copiare il messaggio dell'asserzione dal **Output** finestra in una finestra di testo se si desidera salvare i dati per riferimento futuro. Il **Output** finestra può contenere anche altri messaggi di errore. Esaminare i messaggi con attenzione, poiché forniscono indizi alla causa dell'errore di asserzione.  
  
 Usare le asserzioni per rilevare errori durante lo sviluppo. Come regola, utilizzare un'asserzione per ogni presupposto. Ad esempio, se si presuppone che un argomento non è NULL, utilizzare un'asserzione per testare questo presupposto.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a>Asserzioni nelle build di Debug e rilascio  
 Le istruzioni di asserzione compilare solo se `_DEBUG` è definito. In caso contrario, il compilatore considera asserzioni come istruzioni null. Pertanto, le istruzioni di asserzione non impongano alcun overhead o costano nella versione finale del programma, prestazioni e consentono di evitare l'utilizzo di `#ifdef` direttive.  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a>Effetti collaterali di utilizzo di asserzioni  
 Quando si aggiungono asserzioni nel codice, assicurarsi che le asserzioni non hanno effetti collaterali. Ad esempio, si consideri l'asserzione seguente che modifica il `nM` valore:  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 Poiché il `ASSERT` espressione non viene valutata nella versione di rilascio del programma, `nM` possono avere valori diversi in versioni di Debug e rilascio. Per evitare questo problema in MFC, è possibile utilizzare il [verificare](/cpp/mfc/reference/diagnostic-services#verify) macro anziché `ASSERT`.  `VERIFY`valuta l'espressione in tutte le versioni, ma non controlla il risultato nella versione di rilascio.  
  
 Prestare particolare attenzione sull'uso di chiamate di funzione nelle istruzioni di asserzione, perché la valutazione di una funzione può avere effetti collaterali imprevisti.  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY`chiamate `myFnctn` nelle versioni di Debug e di rilascio, è possibile utilizzare. Se tuttavia si utilizza `VERIFY` impone l'overhead di una chiamata di funzione non necessari nella versione di rilascio.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a>Asserzioni CRT  
 Il CRTDBG. H definisce le [macro Assert e ASSERTE](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) per il controllo delle asserzioni.  
  
|Macro|Risultato|  
|-----------|------------|  
|`_ASSERT`|Se l'espressione specificata restituisce FALSE, il numero di riga e il nome di file di `_ASSERT`.|`_ASSERTE`|  
|`_ASSERTE`|Uguale a `_ASSERT`, nonché una rappresentazione di stringa dell'espressione è stato dichiarato.|  
  
 `_ASSERTE`è più potente perché riporta l'espressione di asserzione che è risultato per essere FALSE. Questo potrebbe essere sufficiente per identificare il problema senza fare riferimento al codice sorgente. Tuttavia, la versione di Debug dell'applicazione contiene una costante di stringa per ogni espressione dichiarato utilizzando `_ASSERTE`. Se è possibile utilizzare molti `_ASSERTE` macro, queste espressioni stringa occupano una quantità notevole di memoria. Se questo costituisce un problema, utilizzare `_ASSERT` per risparmiare memoria.  
  
 Quando `_DEBUG` è definito, il `_ASSERTE` macro viene definita come segue:  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 Se l'espressione di asserzione restituisce FALSE, [CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) viene chiamato per segnalare l'errore di asserzione (utilizzando una finestra di messaggio per impostazione predefinita). Se si sceglie **ripetere** nella finestra di messaggio, `_CrtDbgReport` restituisce 1 e `_CrtDbgBreak` chiamerà il debugger tramite `DebugBreak`.  
  
### <a name="checking-for-heap-corruption"></a>Verifica di danneggiamento dell'Heap  
 L'esempio seguente usa [CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) per verificare la presenza di danneggiamento dell'heap:  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### <a name="checking-pointer-validity"></a>Il controllo di validità del puntatore  
 L'esempio seguente usa [CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) per verificare che sia valido per la lettura o scrittura di un determinato intervallo di memoria.  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 L'esempio seguente usa [CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) per verificare un puntatore fa riferimento alla memoria nell'heap locale (all'heap creato e gestito da questa istanza della libreria di runtime C, ovvero una DLL può avere la propria istanza della libreria, e di conseguenza il proprio heap, di fuori dell'heap dell'applicazione). Questa asserzione rileva non solo gli indirizzi nulli o, ma anche i puntatori alle variabili statiche, le variabili dello stack e qualsiasi altra memoria non locale.  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### <a name="checking-a-memory-block"></a>Il controllo di un blocco di memoria  
 L'esempio seguente usa [CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) per verificare che un blocco di memoria nell'heap locale e presenta un tipo di blocco valido.  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a>Asserzioni MFC  
 MFC definisce il [ASSERT](http://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) macro per il controllo delle asserzioni. Definisce inoltre la `MFC ASSERT_VALID` e `CObject::AssertValid` metodi per controllare lo stato interno di un `CObject`-oggetto derivato.  
  
 Se l'argomento di MFC `ASSERT` macro restituisce zero o false, la macro interrompe l'esecuzione del programma e avvisa l'utente; in caso contrario, l'esecuzione continua.  
  
 Quando un'asserzione ha esito negativo, una finestra di messaggio viene visualizzato il nome del file di origine e il numero di riga dell'asserzione. Se si sceglie Riprova nella finestra di dialogo casella, una chiamata a [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) , l'esecuzione al debugger. A questo punto, è possibile esaminare lo stack di chiamate e utilizzare altre utilità del debugger per determinare perché l'asserzione non è riuscita. Se è stata abilitata [Just-in-time debug](../debugger/just-in-time-debugging-in-visual-studio.md)e il debugger non era già in esecuzione, la finestra di dialogo è possibile avviare il debugger.  
  
 Nell'esempio seguente viene illustrato come utilizzare `ASSERT` per controllare il valore restituito di una funzione:  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 È possibile utilizzare ASSERT con la [IsKindOf](/cpp/mfc/reference/cobject-class.md#CObject__IsKindOf) funzione per fornire argomenti della funzione di controllo dei tipi:  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 Il `ASSERT` (macro) non produce codice nella versione di rilascio. Se è necessario valutare l'espressione nella versione di rilascio, usare il [verificare](/cpp/mfc/reference/diagnostic-services#verify) (macro) invece di ASSERT.  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a>ASSERT_VALID e CObject:: AssertValid  
 Il [CObject:: AssertValid](/cpp/mfc/reference/cobject-class.md#CObject__AssertValid) metodo consente di controlli in fase di esecuzione dello stato interno di un oggetto. Sebbene non sia necessario eseguire l'override `AssertValid` quando si deriva dalla classe `CObject`, è possibile rendere più affidabile la classe in questo modo. `AssertValid`deve eseguire asserzioni su tutte le variabili membro dell'oggetto per verificare che contengano i valori validi. Ad esempio, verificare che le variabili membro puntatore non sono NULL.  
  
 Nell'esempio seguente viene illustrato come dichiarare un `AssertValid` funzione:  
  
```  
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  
  
```  
  
 Quando esegue l'override `AssertValid`, chiamare la versione della classe di base di `AssertValid` prima di eseguire i controlli. Utilizzare quindi la macro ASSERT per controllare i membri univoci per la classe derivata, come illustrato di seguito:  
  
```  
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  
  
    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  
  
```  
  
 Se una o più delle variabili membro memorizza oggetti, è possibile utilizzare il `ASSERT_VALID` macro per verificarne la validità interna (se le classi di eseguire l'override `AssertValid`).  
  
 Ad esempio, si consideri una classe `CMyData`, quali archivi un [CObList](/cpp/mfc/reference/coblist-class) in una delle variabili membro. Il `CObList` variabile, `m_DataList`, memorizza una raccolta di `CPerson` oggetti. Una dichiarazione abbreviata di `CMyData` simile al seguente:  
  
```  
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  
  
```  
  
 Il `AssertValid` esegue l'override in `CMyData` simile al seguente:  
  
```  
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  
  
```  
  
 `CMyData`Usa il `AssertValid` meccanismo per testare la validità degli oggetti archiviati nel proprio membro dati. Eseguire l'override `AssertValid` di `CMyData` richiama il `ASSERT_VALID` macro per la propria variabile membro m_pDataList.  
  
 Verifica della validità non termina a questo livello, poiché la classe `CObList` esegue inoltre l'override `AssertValid`. Questo override esegue ulteriori verifica della validità sullo stato interno dell'elenco. Pertanto, di test di validità su un `CMyData` oggetto comporta ulteriori verifiche di validità per gli stati interni dell'oggetto archiviato `CObList` oggetto elenco.  
  
 Con alcune altre operazioni, è possibile aggiungere i test di validità per il `CPerson` gli oggetti archiviati anche nell'elenco. È possibile derivare una classe `CPersonList` da `CObList` ed eseguire l'override `AssertValid`. Eseguire l'override, chiamare `CObject::AssertValid` e quindi scorrere l'elenco, la chiamata `AssertValid` in ogni `CPerson` oggetto archiviato nell'elenco. Il `CPerson` esegue l'override di classe riportata all'inizio di questo argomento già `AssertValid`.  
  
 Si tratta di un meccanismo potente quando si compila per il debug. Quando si compila successivamente per la versione, il meccanismo viene disattivato automaticamente.  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a>Limitazioni di AssertValid  
 Generazione di un'asserzione indica che l'oggetto non è corretto e che l'esecuzione verrà interrotta. Tuttavia, una mancanza di asserzione indica solo che è stato rilevato alcun problema, ma l'oggetto potrebbe non essere valido.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a>Utilizzo di asserzioni  
  
###  <a name="BKMK_Catching_logic_errors"></a>Rilevamento di errori logici  
 È possibile impostare un'asserzione a una condizione che deve essere true in base alla logica del programma. L'asserzione non ha alcun effetto a meno che non si verifica un errore logico.  
  
 Si supponga ad esempio è una simulazione molecole di gas in un contenitore, mentre la variabile `numMols` rappresenta il numero totale di molecole. Questo numero non può essere minore di zero, pertanto è possibile includere un'istruzione di asserzione MFC simile al seguente:  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 In alternativa, è possibile includere un'asserzione CRT simile al seguente:  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 Queste istruzioni non esegue alcuna operazione se il programma funzioni correttamente. Se a causa di un errore logico `numMols` per essere minore di zero, tuttavia, l'asserzione interromperà l'esecuzione del programma e visualizza il [la finestra di dialogo di errore di asserzione](../debugger/assertion-failed-dialog-box.md).  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a>Controllo dei risultati  
 Asserzioni risultano utili per il test di operazioni i cui risultati non sono evidenti da un controllo visivo rapido.  
  
 Ad esempio, si consideri il codice seguente, che aggiorna la variabile `iMols` in base al contenuto dell'elenco collegato a cui puntata `mols`:  
  
```  
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  
  
 Il numero di molecole conteggiato da `iMols` deve sempre essere minore o uguale al numero totale di molecole, `numMols`. Esame visivo del ciclo non mostra che questo necessariamente sarà il caso, in modo dopo il ciclo viene utilizzata un'istruzione di asserzione per verificare tale condizione.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a>Errori non gestiti  
 È possibile utilizzare le asserzioni per verificare le condizioni di errore in un punto nel codice in cui gli eventuali errori dovrebbero essere stati gestiti. Nell'esempio seguente, una routine grafica restituisce zero per l'esito positivo o un codice di errore.  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 Se il codice di gestione degli errori funziona correttamente, l'errore deve essere gestito e `myErr` Reimposta su zero prima di raggiungere l'asserzione. Se `myErr` dispone di un altro valore, l'asserzione avrà esito negativo, il programma verrà interrotto e [la finestra di dialogo di errore di asserzione](../debugger/assertion-failed-dialog-box.md) viene visualizzato.  
  
 Le istruzioni di asserzione non sono tuttavia un sostituto per il codice di gestione degli errori. Nell'esempio seguente viene illustrata un'istruzione di asserzione che può causare problemi nel codice della versione finale:  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 Questo codice si basa sull'istruzione di asserzione per gestire la condizione di errore. Di conseguenza, qualsiasi codice di errore restituito da `myGraphRoutine` non verrà gestito nel codice della versione finale.  
  
 [In questo argomento](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md)