---
title: Informazioni su SAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: c8f29a909f6aef75976a551546d4cbeafdf03b37
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291884"
---
# <a name="understanding-sal"></a>Informazioni su SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il linguaggio di annotazione del codice sorgente Microsoft (SAL) fornisce un set di annotazioni che è possibile usare per descrivere il modo in cui una funzione usa i parametri, le ipotesi che fa su di essi e le garanzie che apporta al termine dell'esecuzione. Le annotazioni sono definite nel file di intestazione `<sal.h>`. L'analisi del codice di C++ Visual Studio per USA le annotazioni SAL per modificare l'analisi delle funzioni. Per ulteriori informazioni su SAL 2,0 per lo sviluppo di driver Windows, vedere le [annotazioni sal 2,0 per i driver di Windows](https://go.microsoft.com/fwlink/?LinkId=250979).  
  
 In modalità nativa, C C++ e forniscono solo agli sviluppatori un metodo limitato per esprimere costantemente finalità e invarianza. Con le annotazioni SAL è possibile descrivere più dettagliatamente le funzioni in modo che gli sviluppatori che li utilizzano possano comprendere meglio come utilizzarle.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>Che cos'è SAL e perché usarlo?  
 Semplicemente, SAL è un modo economico per consentire al compilatore di controllare il codice.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL rende il codice più prezioso  
 SAL può aiutarti a rendere la progettazione del codice più comprensibile, sia per gli utenti che per gli strumenti di analisi del codice. Si consideri questo esempio che mostra la funzione runtime C `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 È possibile indicare il funzionamento di questa funzione? Quando una funzione viene implementata o chiamata, è necessario mantenere determinate proprietà per garantire la correttezza del programma. Semplicemente esaminando una dichiarazione come quella nell'esempio, non è possibile conoscerne le caratteristiche. Senza annotazioni SAL, è necessario basarsi sulla documentazione o sui commenti del codice. Di seguito è illustrata la documentazione di MSDN per `memcpy`:  
  
> "Copia il numero di byte di src in dest. Se l'origine e la destinazione si sovrappongono, il comportamento di memcpy non è definito. Usare memmove per gestire le aree sovrapposte.   
> **Nota sulla sicurezza:** Verificare che la dimensione del buffer di destinazione sia uguale o superiore a quella del buffer di origine. Per ulteriori informazioni, vedere evitare sovraccarichi del buffer. "  
  
 La documentazione contiene un paio di informazioni che indicano che il codice deve mantenere determinate proprietà per garantire la correttezza del programma:  
  
- `memcpy` copia il `count` di byte dal buffer di origine nel buffer di destinazione.  
  
- Il buffer di destinazione deve avere una dimensione almeno uguale al buffer di origine.  
  
  Tuttavia, il compilatore non è in grado di leggere la documentazione o i commenti informali. Non sa che esiste una relazione tra i due buffer e `count`e non è possibile indovinare in modo efficace una relazione. SAL può fornire maggiore chiarezza sulle proprietà e sull'implementazione della funzione, come illustrato di seguito:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Si noti che queste annotazioni sono simili a quelle contenute nella documentazione MSDN, ma sono più concise e seguono un modello semantico. Quando si legge questo codice, è possibile comprendere rapidamente le proprietà di questa funzione e come evitare i problemi di sicurezza del sovraccarico del buffer. Ancora meglio, i modelli semantici forniti da SAL possono migliorare l'efficienza e l'efficacia degli strumenti di analisi del codice automatizzati nella prima individuazione dei potenziali bug. Si supponga che un utente scriva questa implementazione buggy di `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Questa implementazione contiene un errore comune. Fortunatamente, l'autore del codice ha incluso l'annotazione delle dimensioni del buffer SAL: uno strumento di analisi del codice potrebbe rilevare il bug analizzando solo questa funzione.  
  
### <a name="sal-basics"></a>Nozioni fondamentali su SAL  
 SAL definisce quattro tipi di parametri di base, classificati in base al modello di utilizzo.  
  
|Category|Annotazione parametro|description|  
|--------------|--------------------------|-----------------|  
|**Input per la funzione chiamata**|`_In_`|I dati vengono passati alla funzione chiamata e vengono considerati di sola lettura.|  
|**Input della funzione chiamata e output al chiamante**|`_Inout_`|I dati utilizzabili vengono passati nella funzione e potenzialmente modificati.|  
|**Output al chiamante**|`_Out_`|Il chiamante fornisce solo spazio per la scrittura della funzione chiamata. La funzione chiamata scrive i dati in tale spazio.|  
|**Output del puntatore al chiamante**|`_Outptr_`|Come l' **output al chiamante**. Il valore restituito dalla funzione chiamata è un puntatore.|  
  
 Queste quattro annotazioni di base possono essere rese più esplicite in vari modi. Per impostazione predefinita, si presuppone che i parametri del puntatore con annotazioni siano necessari, perché la funzione deve essere non NULL perché la funzione abbia esito positivo. La variante più comunemente utilizzata delle annotazioni di base indica che un parametro del puntatore è facoltativo. se è NULL, la funzione può comunque avere esito positivo.  
  
 In questa tabella viene illustrato come distinguere i parametri obbligatori e facoltativi:  
  
||I parametri sono obbligatori|Parametri facoltativi|  
|-|-----------------------------|-----------------------------|  
|**Input per la funzione chiamata**|`_In_`|`_In_opt_`|  
|**Input della funzione chiamata e output al chiamante**|`_Inout_`|`_Inout_opt_`|  
|**Output al chiamante**|`_Out_`|`_Out_opt_`|  
|**Output del puntatore al chiamante**|`_Outptr_`|`_Outptr_opt_`|  
  
 Queste annotazioni consentono di identificare i possibili valori non inizializzati e l'utilizzo non valido del puntatore null in modo formale e accurato. Il passaggio di un valore NULL a un parametro obbligatorio può causare un arresto anomalo o potrebbe causare la restituzione di un codice di errore "non riuscito". In entrambi i casi, la funzione non riesce a eseguire il proprio processo.  
  
## <a name="sal-examples"></a>Esempi SAL  
 In questa sezione vengono illustrati esempi di codice per le annotazioni SAL di base.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Utilizzo dello strumento di analisi Visual Studio Code per individuare i difetti  
 Negli esempi, lo strumento di analisi Visual Studio Code viene usato insieme alle annotazioni SAL per individuare i difetti del codice. Ecco come eseguire questa operazione.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Per usare gli strumenti di analisi del codice di Visual Studio e SAL  
  
1. In Visual Studio aprire un C++ progetto che contiene le annotazioni SAL.  
  
2. Sulla barra dei menu scegliere **Compila**, **Esegui analisi del codice su soluzione**.  
  
    Si consideri il \_in\_ esempio in questa sezione. Se si esegue l'analisi del codice su di essa, viene visualizzato questo avviso:  
  
   > **C6387 valore di parametro non valido**   
   > ' pInt ' potrebbe essere ' 0': non rispetta la specifica per la funzione ' incallee '.  
  
### <a name="example-the-_in_-annotation"></a>Esempio: \_nell'annotazione\_  
 L'annotazione `_In_` indica che:  
  
- Il parametro deve essere valido e non verrà modificato.  
  
- La funzione leggerà solo dal buffer a elemento singolo.  
  
- Il chiamante deve fornire il buffer e inizializzarlo.  
  
- `_In_` specifica "di sola lettura". Un errore comune consiste nell'applicare `_In_` a un parametro che deve avere invece l'annotazione `_Inout_`.  
  
- `_In_` è consentito ma ignorato dall'analizzatore su scalari non puntatore.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Se si usa Visual Studio Code analisi in questo esempio, viene convalidato che i chiamanti passano un puntatore non null a un buffer inizializzato per `pInt`. In questo caso, `pInt` puntatore non può essere NULL.  
  
### <a name="example-the-_in_opt_-annotation"></a>Esempio: \_In_opt annotazione\_  
 `_In_opt_` è uguale a `_In_`, ad eccezione del fatto che il parametro di input può essere NULL e, pertanto, la funzione deve verificare la presenza di questa.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Code analisi convalida che la funzione verifica la presenza di valori NULL prima di accedere al buffer.  
  
### <a name="example-the-_out_-annotation"></a>Esempio: annotazione\_ \_out  
 `_Out_` supporta uno scenario comune in cui un puntatore non NULL che punta a un buffer di elemento viene passato e la funzione Inizializza l'elemento. Il chiamante non deve inizializzare il buffer prima della chiamata. la funzione chiamata promette di inizializzarla prima della restituzione.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Visual Studio Code strumento di analisi verifica che il chiamante passi un puntatore non NULL a un buffer per `pInt` e che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
### <a name="example-the-_out_opt_-annotation"></a>Esempio: \_Out_opt annotazione\_  
 `_Out_opt_` è uguale a `_Out_`, ad eccezione del fatto che il parametro può essere NULL e, pertanto, la funzione deve verificare la presenza di questa.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Code analisi convalida che questa funzione verifica la presenza di valori NULL prima che venga dereferenziata `pInt` e se `pInt` non è NULL, il buffer viene inizializzato dalla funzione prima che venga restituito.  
  
### <a name="example-the-_inout_-annotation"></a>Esempio: l'annotazione \_InOut\_  
 `_Inout_` viene utilizzato per annotare un parametro del puntatore che può essere modificato dalla funzione. Il puntatore deve puntare a dati inizializzati validi prima della chiamata e anche in caso di modifica, deve comunque avere un valore valido al momento della restituzione. L'annotazione specifica che la funzione può leggere liberamente e scrivere nel buffer a elemento singolo. Il chiamante deve fornire il buffer e inizializzarlo.  
  
> [!NOTE]
> Come `_Out_`, `_Inout_` necessario applicare a un valore modificabile.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 Visual Studio Code analisi convalida che i chiamanti passano un puntatore non NULL a un buffer inizializzato per `pInt`e che, prima della restituzione, `pInt` è ancora non NULL e il buffer viene inizializzato.  
  
### <a name="example-the-_inout_opt_-annotation"></a>Esempio: \_Inout_opt annotazione\_  
 `_Inout_opt_` è uguale a `_Inout_`, ad eccezione del fatto che il parametro di input può essere NULL e, pertanto, la funzione deve verificare la presenza di questa.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Code analisi convalida che questa funzione verifica la presenza di valori NULL prima di accedere al buffer e se `pInt` non è NULL, il buffer viene inizializzato dalla funzione prima che venga restituito.  
  
### <a name="example-the-_outptr_-annotation"></a>Esempio: \_annotazione\_ Outptr  
 `_Outptr_` viene utilizzato per annotare un parametro progettato per restituire un puntatore.  Il parametro non deve essere NULL e la funzione chiamata restituisce un puntatore non NULL al suo interno e il puntatore punta ai dati inizializzati.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Visual Studio Code analisi verifica che il chiamante passi un puntatore non NULL per `*pInt`e che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
### <a name="example-the-_outptr_opt_-annotation"></a>Esempio: \_Outptr_opt annotazione\_  
 `_Outptr_opt_` è uguale `_Outptr_`, ad eccezione del fatto che il parametro è facoltativo, il chiamante può passare un puntatore NULL per il parametro.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio Code analisi verifica che questa funzione controlli la presenza di valori NULL prima che venga dereferenziata `*pInt` e che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
### <a name="example-the-_success_-annotation-in-combination-with-_out_"></a>Esempio: l'annotazione \_Success\_ in combinazione con \_out\_  
 Le annotazioni possono essere applicate alla maggior parte degli oggetti.  In particolare, è possibile aggiungere annotazioni a una funzione intera.  Una delle caratteristiche più ovvie di una funzione è che può avere esito positivo o negativo. Tuttavia, come l'associazione tra un buffer e le relative dimensioni,C++ C/non può esprimere l'esito positivo o negativo della funzione. Utilizzando l'annotazione `_Success_`, è possibile specificare l'esito positivo di una funzione.  Il parametro per l'annotazione `_Success_` è semplicemente un'espressione che, quando è true, indica che la funzione ha avuto esito positivo. L'espressione può essere qualsiasi elemento che può essere gestito dal parser dell'annotazione. Gli effetti delle annotazioni dopo la restituzione della funzione sono applicabili solo quando la funzione ha esito positivo. In questo esempio viene illustrato come `_Success_` interagisce con `_Out_` per eseguire la corretta operazione. È possibile usare la parola chiave `return` per rappresentare il valore restituito.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 L'annotazione `_Out_` fa in modo che Visual Studio Code analisi convalidi che il chiamante passa un puntatore non NULL a un buffer per `pInt`e che il buffer venga inizializzato dalla funzione prima che venga restituito.  
  
## <a name="sal-best-practice"></a>Procedura consigliata SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Aggiunta di annotazioni al codice esistente  
 SAL è una tecnologia potente che può aiutare a migliorare la sicurezza e l'affidabilità del codice. Dopo aver apprendere SAL, è possibile applicare la nuova competenza al lavoro giornaliero. Nel nuovo codice è possibile usare le specifiche basate su SAL per progettazione; nel codice precedente, è possibile aggiungere annotazioni in modo incrementale e quindi aumentare i vantaggi ogni volta che si aggiorna.  
  
 Le intestazioni pubbliche Microsoft sono già annotate. È pertanto consigliabile che nei progetti annotare prima le funzioni e le funzioni del nodo foglia che chiamano le API Win32 per ottenere il massimo vantaggio.  
  
### <a name="when-do-i-annotate"></a>Quando si annota?  
 Di seguito sono riportate alcune linee guida:  
  
- Annota tutti i parametri del puntatore.  
  
- Annotare le annotazioni dell'intervallo di valori in modo che l'analisi del codice possa garantire la sicurezza del buffer e del puntatore  
  
- Annotare le regole di blocco e gli effetti collaterali del blocco. Per ulteriori informazioni, vedere [annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md).  
  
- Annotare le proprietà del driver e altre proprietà specifiche del dominio.  
  
  In alternativa, è possibile aggiungere annotazioni a tutti i parametri per rendere chiara l'intento e per semplificare la verifica dell'avvenuta annotazione.  
  
## <a name="related-resources"></a>Risorse correlate  
 [Blog del team di analisi del codice](https://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle annotazioni SAL per ridurreC++ i difetti di C/codice](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento della funzione](../code-quality/annotating-function-behavior.md)   
 [Annotazione di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare quando e dove si applica un'Annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)
