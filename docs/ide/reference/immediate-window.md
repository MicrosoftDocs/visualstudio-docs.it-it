---
title: Finestra di controllo immediato | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: VB
f1_keywords: VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 026223f89822f2d76aa1185da8691c538b15ee62
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="immediate-window"></a>Controllo immediato (finestra)
Il **immediato** finestra viene utilizzata per eseguire il debug e valutare le espressioni, eseguire istruzioni, i valori delle variabili di stampa e così via. Consente di immettere le espressioni che devono essere valutate ed eseguite dal linguaggio di sviluppo durante il debug. Per visualizzare il **immediato** finestra, aprire un progetto per la modifica, quindi scegliere **Windows** dal **Debug** dal menu **immediato**, oppure premere CTRL + ALT + I.  
  
 È possibile usare questa finestra per eseguire singoli comandi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. I comandi disponibili includono `EvaluateStatement`, che consente di assegnare valori alle variabili. Il **immediato** finestra supporta anche IntelliSense.  
  
## <a name="displaying-the-values-of-variables"></a>Visualizzazione dei valori delle variabili  
 Questa finestra può essere particolarmente utile durante il debug di un'applicazione. Ad esempio, per controllare il valore di una variabile `varA`, usare il [comando Stampa](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 Il punto interrogativo (?) è un alias di `Debug.Print`. Questo comando può quindi essere scritto anche nel modo seguente:  
  
```  
>? varA  
```  
  
 Entrambe le versioni di questo comando restituiscono il valore della variabile `varA`.  
  
> [!NOTE]
>  Da rilasciare un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando il **immediato** finestra, è necessario anteporre il comando con un segno maggiore (>). Per immettere più comandi, passare il **comando** finestra.  
  
## <a name="design-time-expression-evaluation"></a>Valutazione delle espressioni in fase di progettazione  
 È possibile utilizzare il **immediato** finestra per eseguire una funzione o subroutine in fase di progettazione.  
  
#### <a name="to-execute-a-function-at-design-time"></a>Per eseguire una funzione in fase di progettazione  
  
1.  Copiare il codice seguente in un'applicazione console di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]:  
  
    ```vb
    Module Module1  
  
        Sub Main()  
            MyFunction(5)  
        End Sub  
  
        Function MyFunction(ByVal input as Integer) As Integer  
            Return input * 2  
        End Function  
  
    End Module  
    ```  
  
2.  Scegliere **Finestre** dal menu **Debug** e quindi fare clic su **Controllo immediato**.  
  
3.  Tipo `?MyFunction(2)` nel **immediato** finestra e premere INVIO.  
  
     Il **immediato** finestra eseguirà `MyFunction` e visualizzare `4`.  
  
Se la funzione o subroutine contiene un punto di interruzione, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interromperà l'esecuzione nel punto appropriato. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Per altre informazioni, vedere [Procedura dettagliata: Debug in fase di progettazione](../../debugger/walkthrough-debugging-at-design-time.md).  
  
Non è possibile usare la valutazione delle espressioni in fase di progettazione nei tipi di progetto che richiedono l'avvio di un ambiente di esecuzione, tra cui progetti [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)], progetti Web, progetti Smart Device e progetti SQL.  
  
### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Valutazione delle espressioni in fase di progettazione nelle soluzioni multiprogetto  
 Per determinare il contesto per la valutazione delle espressioni in fase di progettazione, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fa riferimento al progetto selezionato in Esplora soluzioni. Se in Esplora soluzioni non è selezionato alcun progetto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di valutare la funzione in base al progetto di avvio. Se la funzione non può essere valutata nel contesto corrente, si riceverà un messaggio di errore. Se si sta tentando di valutare una funzione in un progetto che non è il progetto di avvio per la soluzione e viene visualizzato un errore, provare a selezionare il progetto in Esplora soluzioni e tentare nuovamente la valutazione.  
  
## <a name="entering-commands"></a>Immissione di comandi  
 È necessario immettere il segno di maggiore (>) per il rilascio di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i comandi di **immediato** finestra. Usare FRECCIA SU e FRECCIA GIÙ per scorrere i comandi immessi in precedenza.  
  
|Attività|Soluzione|Esempio|  
|----------|--------------|-------------|  
|Valutare un'espressione.|Anteporre un punto interrogativo (?) all'espressione.|`? a+b`|  
|Passare temporaneamente alla modalità di comando mentre è attiva la modalità immediata (per eseguire un singolo comando).|Immettere il comando anteponendo il segno di maggiore (>).|`>alias`|  
|Passa alla finestra di comando.|Immettere `cmd` nella finestra anteponendo il segno di maggiore (>).|`>cmd`|  
|Tornare alla finestra di controllo immediato.|Immettere `immed` nella finestra senza il segno di maggiore (>)|`immed`|  
  
## <a name="mark-mode"></a>Modalità Indicatore  
 Quando fa clic su qualsiasi riga precedente nel **immediato** finestra, si passa automaticamente in modalità indicatore. Questa modalità consente di selezionare, modificare e copiare il testo dei comandi precedenti in qualsiasi editor di testo e incollarlo nella riga corrente.  
  
## <a name="the-equals--sign"></a>Segno di uguale (=)  
 La finestra usata per immettere il comando `EvaluateStatement` determina se interpretare un segno di uguale (=) come operatore di confronto o come operatore di assegnazione.  
  
 Nel **immediato** finestra, un segno di uguale (=) viene interpretato come un operatore di assegnazione. Il comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 assegna ad esempio alla variabile `varA` il valore della variabile `varB`.  
  
 Nel **comando** finestra, al contrario, un segno di uguale (=) viene interpretato come un operatore di confronto. Non è possibile utilizzare gli operatori di assegnazione nel **comando** finestra. Pertanto, se ad esempio i valori delle variabili `varA` e `varB` sono diversi, il comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 restituisce il valore `False`.  
  
## <a name="first-chance-exception-notifications"></a>notifica di eccezioni first-chance  
 In alcune configurazioni, le notifiche di eccezioni first-chance vengono visualizzate nel **immediato** finestra.  
  
#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Per attivare o disattivare le notifiche di eccezioni first-chance nella finestra di controllo immediato  
  
1.  Scegliere **Altre finestre** dal menu **Visualizza** e quindi fare clic su **Output**.  
  
2.  Fare doppio clic sull'area di testo della finestra **Output** e selezionare o deselezionare **Messaggi di eccezione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Spostarsi nel codice con il Debugger](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Debugging in Visual Studio](../../debugger/debugging-in-visual-studio.md)  (Debug in Visual Studio)  
 [Nozioni di base sul debugger](../../debugger/debugger-basics.md)   
 [Procedura dettagliata: Debug in fase di progettazione](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Uso delle espressioni regolari in Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)