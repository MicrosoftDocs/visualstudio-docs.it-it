---
title: Informazioni sui SAL | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 196bfdbeeda00199861ea2f676553f024fcaf98f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-sal"></a>Informazioni su SAL
Il linguaggio di annotazione del codice sorgente Microsoft (SAL) fornisce un set di annotazioni che è possibile utilizzare per descrivere come una funzione utilizza i relativi parametri, le ipotesi su cui fa su di essi e le garanzie che rende quando viene completato. Le annotazioni sono definite nel file di intestazione `<sal.h>`. Analisi codice di Visual Studio per C++ Usa le annotazioni SAL per modificare l'analisi di funzioni. Per ulteriori informazioni su SAL 2.0 per lo sviluppo di driver di Windows, vedere [SAL 2.0 annotazioni per i driver di Windows](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 In modo nativo, C e C++ consentono solo limitato per gli sviluppatori esprimere in modo coerente finalità e l'invarianza. Utilizzando le annotazioni SAL, è possibile descrivere le funzioni in modo più dettagliato in modo che gli sviluppatori che utilizzano tali comprendere meglio come utilizzarle.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>Che cos'è SAL e perché è opportuno utilizzarla?  
 Semplificando, SAL è una soluzione economica per consentire al compilatore di cercare il codice.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL rende codice più utili  
 SAL consentono di rendere la progettazione di codice più comprensibile per gli utenti e per gli strumenti di analisi codice. Si consideri l'esempio che illustra la funzione di runtime C `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 È possibile conoscere ciò che svolge questa funzione? Quando implementata una funzione viene chiamata, è necessario configurare alcune proprietà per assicurare la correttezza di programma. Esaminando solo una dichiarazione, ad esempio quello nell'esempio, non si conosce quali sono. Senza le annotazioni SAL, è necessario basarsi sulla documentazione o commenti del codice. Ecco la documentazione di MSDN per `memcpy` è indicato:  
  
> "Copie contano i byte di src di destinazione. Se l'origine e destinazione si sovrappongono, il comportamento di memcpy è definito. Utilizzare memmove per gestire le aree di sovrapposizione.   
> **Nota sulla sicurezza:** assicurarsi che il buffer di destinazione è la stessa dimensione o maggiore del buffer di origine. Per ulteriori informazioni, vedere evitare sovraccarichi del Buffer."  
  
 La documentazione contiene un paio di bit di informazioni che suggerisce che il codice debba mantenere alcune proprietà per garantire la correttezza di programma:  
  
-   `memcpy`copie di `count` di byte dal buffer di origine per il buffer di destinazione.  
  
-   Il buffer di destinazione deve essere grande almeno come buffer di origine.  
  
 Tuttavia, il compilatore non è possibile leggere la documentazione o commenti informali. Riconosce che vi sia una relazione tra due buffer e `count`, e inoltre non è possibile in modo efficace indovinare su una relazione. SAL potrebbe fornire maggiore chiarezza sulle proprietà e implementazione della funzione, come illustrato di seguito:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Si noti che queste annotazioni sono simili le informazioni nella documentazione di MSDN, ma sono più concise e seguono un modello semantico. Durante la lettura di questo codice, è possibile comprendere rapidamente le proprietà di questa funzione e come evitare problemi di sicurezza di sovraccarico del buffer. Ancor meglio, i modelli semantici che fornisce SAL possono migliorare l'efficienza e l'efficacia di strumenti di analisi codice automatizzato l'individuazione iniziale di possibili bug. Si supponga che un utente scrive questa implementazione di anomalo `wmemcpy`:  
  
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
  
 Questa implementazione contiene un errore comune di disattivare uno. Fortunatamente, l'autore del codice incluso l'annotazione di dimensioni del buffer SAL, uno strumento di analisi del codice potrebbe intercettare il bug analizzando questa funzione.  
  
### <a name="sal-basics"></a>Nozioni di base SAL  
 SAL definisce quattro tipi di base di parametri, che sono classificati in base al modello di utilizzo.  
  
|Category|Annotazione parametro|Descrizione|  
|--------------|--------------------------|-----------------|  
|**Chiamata di funzione di input**|`_In_`|Dati viene passati alla funzione chiamata e viene considerati come di sola lettura.|  
|**Chiamata alla funzione input e output al chiamante**|`_Inout_`|Dati utilizzabili viene passati alla funzione e potenzialmente viene modificati.|  
|**Output al chiamante**|`_Out_`|Il chiamante fornisce solo spazio per la funzione chiamata da scrivere. La funzione chiamata scrive i dati in tale spazio.|  
|**Output del puntatore al chiamante**|`_Outptr_`|Ad esempio **Output al chiamante**. Il valore restituito dalla funzione chiamata è un puntatore.|  
  
 Queste quattro annotazioni di base possono essere reso più esplicite in vari modi. Per impostazione predefinita, i parametri dei puntatori con annotazioni si presuppone che siano necessari, ovvero devono essere non NULL per la funzione abbia esito positivo. La variazione delle annotazioni base utilizzata più di frequente indica che un parametro del puntatore è facoltativo, ovvero se è NULL, la funzione può ancora riesce il proprio lavoro.  
  
 Questa tabella viene illustrato come distinguere tra i parametri obbligatori e facoltativi:  
  
||I parametri sono obbligatori|I parametri sono facoltativi|  
|-|-----------------------------|-----------------------------|  
|**Chiamata di funzione di input**|`_In_`|`_In_opt_`|  
|**Chiamata alla funzione input e output al chiamante**|`_Inout_`|`_Inout_opt_`|  
|**Output al chiamante**|`_Out_`|`_Out_opt_`|  
|**Output del puntatore al chiamante**|`_Outptr_`|`_Outptr_opt_`|  
  
 Queste annotazioni aiutano a identificare i possibili valori non inizializzati e un puntatore null non valido viene utilizzato in modo accurato e formale. Passaggio di NULL a un parametro obbligatorio potrebbe causare un arresto anomalo, o potrebbe causare un codice di errore "errore" deve essere restituito. In entrambi i casi, la funzione non riesce il proprio lavoro.  
  
## <a name="sal-examples"></a>Esempi SAL  
 In questa sezione vengono illustrati esempi di codice per le annotazioni SAL base.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Utilizzando lo strumento di analisi codice di Visual Studio per trovare errori  
 Negli esempi, lo strumento di analisi del codice di Visual Studio viene utilizzato insieme alle annotazioni SAL per individuare difetti del codice. Di seguito viene illustrato come eseguire questa operazione.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Utilizzare gli strumenti di analisi codice di Visual Studio e SAL  
  
1.  In Visual Studio, aprire un progetto C++ che contiene le annotazioni SAL.  
  
2.  Nella barra dei menu, scegliere **compilare**, **Esegui analisi del codice su soluzione**.  
  
     Si consideri il riscaldamento in\_ riportato in questa sezione. Se si esegue l'analisi del codice, viene visualizzato questo avviso:  
  
    > **C6387 Il valore di parametro non valido**   
    > 'pInt' può essere '0': questa condizione non soddisfa la specifica la funzione 'InCallee'.  
  
### <a name="example-the-in-annotation"></a>Esempio: Il riscaldamento in\_ annotazione  
 Il `_In_` annotazione indica che:  
  
-   Il parametro deve essere valido e non verrà modificato.  
  
-   La funzione verrà letti solo dal buffer del singolo elemento.  
  
-   Il chiamante deve fornire al buffer e inizializzarlo.  
  
-   `_In_`Specifica di "sola lettura". Un errore comune consiste nell'applicare `_In_` a un parametro che deve avere il `_Inout_` annotazione invece.  
  
-   `_In_`è consentita ma ignorato dall'analizzatore di valori scalari non puntatore.  
  
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
  
 Se si utilizza l'analisi del codice di Visual Studio in questo esempio, verifica che i chiamanti passare un puntatore non Null in un buffer inizializzato per `pInt`. In questo caso, `pInt` puntatore non può essere NULL.  
  
### <a name="example-the-inopt-annotation"></a>Esempio: _In_opt\_ annotazione  
 `_In_opt_`è identico `_In_`, ad eccezione del fatto che il parametro di input può essere NULL e, pertanto, la funzione deve cercare.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Analisi del codice di Visual Studio consente di verificare che la funzione verifica i valori NULL prima di accedere il buffer.  
  
### <a name="example-the-out-annotation"></a>Esempio: REC0 out\_ annotazione  
 `_Out_`supporta uno scenario comune in cui viene passato un puntatore non NULL che punta a un buffer di elemento e la funzione Inizializza l'elemento. Il chiamante non dispone di inizializzare il buffer prima della chiamata. la funzione chiamata promette di inizializzarlo prima della restituzione.  
  
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
  
 Strumento di analisi di Visual Studio codice verifica che il chiamante passa un puntatore non NULL in un buffer per `pInt` e che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-outopt-annotation"></a>Esempio: _Out_opt\_ annotazione  
 `_Out_opt_`è identico `_Out_`, ad eccezione del fatto che il parametro può essere NULL e, pertanto, la funzione deve cercare.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Analisi del codice di Visual Studio verifica che questa funzione controlla i valori NULL prima di `pInt` è dereferenziato e se `pInt` non è NULL, che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-inout-annotation"></a>Esempio: InOut\_ annotazione  
 `_Inout_`viene usato per annotare un parametro del puntatore che può essere modificato dalla funzione. Il puntatore deve puntare a dati inizializzati validi prima della chiamata e anche se viene modificato, devono comunque essere un valore valido in fase di restituzione. L'annotazione specifica che la funzione può liberamente leggere e scrivere nel buffer di un elemento. Il chiamante deve fornire al buffer e inizializzarlo.  
  
> [!NOTE]
>  Ad esempio `_Out_`, `_Inout_` deve essere applicata a un valore modificabile.  
  
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
   InOutCallee(pInt); // 'pInt' should not be NULL  
}  
  
```  
  
 Analisi del codice di Visual Studio verifica che i chiamanti passare un puntatore non NULL in un buffer inizializzato per `pInt`e che, prima della restituzione, `pInt` ancora non è null e il buffer viene inizializzato.  
  
### <a name="example-the-inoutopt-annotation"></a>Esempio: _Inout_opt\_ annotazione  
 `_Inout_opt_`è identico `_Inout_`, ad eccezione del fatto che il parametro di input può essere NULL e, pertanto, la funzione deve cercare.  
  
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
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Analisi del codice di Visual Studio verifica che questa funzione controlla i valori NULL prima di accedere il buffer e, se `pInt` non è NULL, che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-outptr-annotation"></a>Esempio: _Outptr\_ annotazione  
 `_Outptr_`è possibile annotare un parametro che è progettata per restituire un puntatore.  Il parametro non deve essere NULL, la funzione chiamata restituisce un puntatore non NULL e tale puntatore punta a dati inizializzati.  
  
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
  
 Analisi del codice di Visual Studio verifica che il chiamante passa un puntatore non NULL `*pInt`, e che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-outptropt-annotation"></a>Esempio: _Outptr_opt\_ annotazione  
 `_Outptr_opt_`è identico `_Outptr_`, ad eccezione del fatto che il parametro è facoltativo, il chiamante può passare un puntatore NULL per il parametro.  
  
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
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Analisi del codice di Visual Studio verifica che questa funzione controlla i valori NULL prima di `*pInt` è dereferenziato e che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>Esempio: _Success\_ annotazione in combinazione con out\_  
 Per la maggior parte degli oggetti, è possono utilizzare le annotazioni.  In particolare, è possibile annotare un'intera funzione.  Una delle caratteristiche di una funzione più ovvie è che può avere esito positivo o esito negativo. Ma, come l'associazione tra un buffer e le relative dimensioni, C/C++ non può esprimere funzione riuscita o meno. Tramite il `_Success_` annotazione, si può supporre il caso di esito positivo per una funzione simile.  Il parametro per il `_Success_` annotazione è semplicemente un'espressione che quando è true indica che la funzione ha avuto esito positivo. L'espressione può essere qualsiasi elemento che è in grado di gestire il parser di annotazione. Gli effetti delle annotazioni dopo la funzione restituisce sono applicabili solo quando la funzione ha esito positivo. Questo esempio viene illustrato come `_Success_` interagisce con `_Out_` di eseguire l'azione di destra. È possibile utilizzare la parola chiave `return` per rappresentare il valore restituito.  
  
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
  
 Il `_Out_` annotazione provoca l'analisi di codice di Visual Studio per convalidare che il chiamante passa un puntatore non NULL in un buffer per `pInt`, e che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
## <a name="sal-best-practice"></a>SAL consigliata  
  
### <a name="adding-annotations-to-existing-code"></a>Aggiunta di annotazioni al codice esistente  
 SAL è una tecnologia potente che consente di migliorare la sicurezza e affidabilità del codice. Dopo aver appreso SAL, è possibile applicare le nuove competenze per le attività quotidiane. Nel nuovo codice, è possibile utilizzare specifiche basate su SAL per impostazione predefinita nel codice precedente, è possibile aggiungere annotazioni in modo incrementale e pertanto migliorare le prestazioni ogni volta che si aggiorna.  
  
 Microsoft pubbliche intestazioni sono già annotate. Pertanto, è consigliabile che nei progetti è innanzitutto annotare le funzioni di nodo foglia e funzioni che chiamano le API Win32 per trarre il massimo vantaggio.  
  
### <a name="when-do-i-annotate"></a>Quando annotare?  
 Di seguito sono riportate alcune linee guida:  
  
-   Annotare tutti i parametri di puntatore.  
  
-   Annotare le annotazioni di intervallo di valori in modo che l'analisi del codice può garantire la sicurezza dei buffer e puntatore.  
  
-   Annotare le regole di blocco e gli effetti collaterali. Per ulteriori informazioni, vedere [annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md).  
  
-   Annotare le proprietà del driver e le altre proprietà specifiche del dominio.  
  
 Oppure è possibile annotare tutti i parametri per rendere l'intento clear in tutto e verificare di aver eseguite le annotazioni.  
  
## <a name="related-resources"></a>Risorse correlate  
 [Blog del Team di analisi del codice](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle annotazioni SAL per ridurre gli errori del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento della funzione](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Esempi e procedure consigliate](../code-quality/best-practices-and-examples-sal.md)