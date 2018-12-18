---
title: Finestra di dialogo Editor (Legacy) del Set di regole | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7284b4a318f1d6c182f1d7d27e41f6c77092ad00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Finestra di dialogo Editor set di regole (legacy)
Questo argomento viene descritto come utilizzare il **Editor Set di regole** nella finestra di dialogo di progettazione del flusso di lavoro Windows legacy. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Il **Editor Set di regole** la finestra di dialogo viene utilizzata per creare e modificare [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) set, che vengono serializzati in un file con estensione rules di regole.

> [!NOTE]
> Se si desidera aprire il file con estensione rules con il **Editor XML con codifica**, è necessario chiudere la finestra di progettazione associata per il flusso di lavoro o attività.

 Per informazioni su come accedere al **Editor Set di regole** nella finestra di dialogo vedere [procedura: creare un PolicyActivity del Set di regole (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> L'editor delle regole della [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy che viene usato per fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] non supporta il multitargeting.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Editor Set di regole** la finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Aggiungi regola**|Aggiunge una nuova definizione della regola nuova nell’insieme di regole.|
|**Eliminazione**|Elimina la regola selezionata dall’insieme di regole.|
|**Il concatenamento**|Specifica quale tipo di concatenamento diretto usare con l’insieme di regole. Le opzioni disponibili sono:<br /><br /> -   **Concatenamento completo**, che consente di utilizzare meccanismi di concatenamento diretto tutti: implicito, con attribuzione del metodo ed esplicito usando un **aggiornamento** (funzione).<br />-   **Sequenziale**, che specifica di non usare alcun concatenamento diretto.<br />-   **Solo aggiornamento esplicito**, che specifica di eseguire soltanto concatenamento diretto sulle **aggiornamento** azioni.<br /><br /> Per ulteriori informazioni sul concatenamento diretto, vedere [utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|**Name**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per nome.|
|**Priorità**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per priorità.|
|**Rivalutazione**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per tipo di rivalutazione.|
|**Anteprima della regola**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per anteprima di una condizione della regola e delle azioni.|
|**Nome:**|Immettere il nome della regola.|
|**Priorità:**|Immettere una priorità per la regola. La priorità predefinita è 0.|
|**Nuova valutazione:**|Specifica quale tipo di rivalutazione della regola usare con la regola. Le opzioni disponibili sono:<br /><br /> -   **Sempre**, che comporta la regola sia rivalutata in base alle esigenze.<br />-   **Mai**, che comporta la regola sia rivalutata. In questo caso una regola viene eseguita solo una volta.|
|**Attiva**|Selezionare per rendere attiva la regola.|
|**Condizione:**|Immettere un'espressione per la condizione della regola. Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|
|**Azioni Then:**|Immettere l'espressione per azioni THEN. Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|
|**Azioni Else:**|Immettere l'espressione per azioni ELSE. Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|
|**OK**|Fare clic per salvare l’insieme di regole in un file con estensione rules.|

 Per ulteriori informazioni sui set di regole, vedere [utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Immissione di espressioni di condizioni e azioni
 Immettere espressioni per la condizione e Then ed Else azioni come testo contenuto nella loro rispettive caselle di **Editor Set di regole** la finestra di dialogo. È possibile digitare **questo.** Nell'editor per fare riferimento a campi, proprietà e metodi usati nel flusso di lavoro, tramite IntelliSense-tipo di menu. In alternativa, è possibile digitare direttamente il nome di un membro del flusso di lavoro. È possibile richiamare metodi statici sui tipi a cui viene fatto riferimento digitando il nome della classe seguito dal nome del metodo.

 È possibile aggiungere operatori logici alla condizione, ad esempio E, O e NON. È anche possibile aggiungere predicati. Un predicato è composto da un operatore binario e due operandi. Gli operatori binari supportati sono = =, >, \<, > =, e < =. Gli operandi supportati sono membri pubblici ai quali è stato assegnato un valore costante, una funzione aritmetica e un ambito.

 È possibile specificare il tipo per il confronto, ed è possibile confrontare a **null** o una stringa vuota. È possibile annidare chiamate ai membri su una variabile contenente un tipo complesso, ad esempio, `this.Address.State == "WA"`.

 Le espressioni supportano gli operatori seguenti:

-   operatori relazionali: ==, =, !=

-   Gli operatori di confronto: <, \<=, >, > =

-   Operatori aritmetici: +, - , *, /, MOD

-   Operatori logici: E, & &, OR, &#124; &#124;, NOT,!

-   Operatori bit per bit: &,&#124;

 La precedenza di operatori dell’espressione segue le regole di precedenza dell’operatore C#.

 Per ulteriori informazioni sulle condizioni, vedere [utilizzo delle condizioni nei flussi di lavoro](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Funzioni Halt e Aggiorna
 **Azioni Then:** e **azioni Else:** le espressioni supportano **Halt** e **aggiornamento** funzioni. Utilizzare il **Halt** di funzione, digitare **Halt** in un **azione Then:** o **azione Else:** casella di testo. Il **Halt** azione causa l'esecuzione di set di regole arrestare immediatamente e restituisce il controllo al codice chiamante. Utilizzare il **aggiornamento** funzione con concatenamento in avanti.

 Un **aggiornamento** istruzione può essere espressa nell'editor in uno dei due moduli; entrambi i moduli vengono visualizzati nell'esempio seguente:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Per ulteriori informazioni sull'utilizzo **aggiornamento** con concatenamento diretto, vedere [utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>Vedere anche

- [Attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [Finestra di dialogo Seleziona set di regole (legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [Utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)
- [Utilizzo delle condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)