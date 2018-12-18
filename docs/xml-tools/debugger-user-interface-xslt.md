---
title: Interfaccia utente (XSLT) del debugger | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1071db6a7a8205ef337737473a18d1a6c31af43c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-user-interface-xslt"></a>Interfaccia utente del debugger (XSLT)
In questo argomento vengono descritte le finestre di dialogo e altre finestre del debugger. Vengono illustrati solo gli elementi dell'interfaccia utente che presentano un comportamento di debug specifico per XSLT.  
  
 Per ulteriori informazioni, vedere il [il debug dell'interfaccia utente](../debugger/debugging-user-interface-reference.md).  
  
## <a name="locals-window"></a>Finestra Variabili locali  
 Nella finestra Variabili locali vengono visualizzate le informazioni sulle variabili definite nel foglio di stile. La finestra Variabili locali contiene tre colonne di informazioni:  
  
 **Name**  
 Questa colonna contiene i nomi di tutte le variabili locali nell'ambito corrente. I set di nodi dispongono di un controllo albero in cui è possibile eseguire il drill-down per visualizzare le sottocartelle.  
  
 **Valore**  
 In questa colonna è visualizzato il valore contenuto da ciascuna variabile. Nei nodi Attribute, processing instruction, comment, text e CData viene visualizzato il valore di testo del nodo. Nei nodi Namespace viene visualizzato l'URI dello spazio dei nomi.  
  
 **Type**  
 Questa colonna identifica il tipo di dati di ciascuna variabile elencata nella **nome** colonna.  
  
 Nella finestra Variabili locali vengono inoltre visualizzate le variabili di contesto predefinite che tengono traccia del contesto della trasformazione XSLT. Nella tabella seguente vengono descritte le variabili di contesto predefinite usate dal debugger XSLT.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`last()`|La dimensione del contesto.|  
|`position()`|Posizione, ossia il numero di indice, del nodo di contesto, in base alla dimensione del contesto.|  
|`self::node()`|Il valore del nodo di contesto.|  
  
## <a name="output-window"></a>Finestra di output  
 Nella finestra di output vengono visualizzati eventuali messaggi di errore o eccezioni di sicurezza che si verificano durante il debug.  
  
 Nel debugger XSLT viene usata una finestra separata per visualizzare l'output del debugger. Si tratta della stessa finestra usata per visualizzare l'output di un **Mostra l'Output XSL** comando.  
  
## <a name="task-list"></a>Elenco attività  
 Nell'Elenco attività vengono elencati tutti gli errori di compilazione del foglio di stile. Se si fa doppio clic sull'errore il cursore si sposta sulla riga contenente l'errore.  
  
 L'Elenco attività comprende gli eventuali errori che si verificano nei blocchi di script nel file XSLT.  
  
> [!NOTE]
>  Il debugger XSLT non dispone di avvisi, pertanto nell'Elenco attività non verranno visualizzati avvisi.  
  
## <a name="breakpoints-window"></a>Finestra Punti di interruzione  
 Nella finestra Punti di interruzione vengono visualizzati tutti i punti di interruzione impostati nel progetto corrente. Se si aggiunge un punto di interruzione mentre la finestra è visualizzata, la finestra viene aggiornata automaticamente per mostrare il nuovo punto di interruzione.  
  
 La finestra Punto di interruzione dovrebbe comportarsi allo stesso modo degli altri debugger di Visual Studio.  
  
## <a name="command-windowimmediate-window"></a>Finestra di comando e finestra di controllo immediato  
 Non implementate in questa versione del debugger XSLT.  
  
## <a name="watch-window"></a>Finestra Espressioni di controllo  
 La finestra Espressioni di controllo viene usata per valutare le variabili. È anche possibile modificare i valori delle variabili.  
  
 Le variabili visualizzate nella finestra Espressioni di controllo sono relative al contesto corrente (l'elemento in primo piano nello stack di chiamate). Se si modifica il contesto, la finestra viene aggiornata e vengono visualizzate le variabili impostate per quel determinato contesto.  
  
## <a name="call-stack-window"></a>Finestra Stack di chiamate  
 La finestra Stack di chiamate viene usata per visualizzare i nomi delle funzioni contenute nello stack di chiamate, nonché i tipi e i valori dei parametri. Le informazioni relative allo stack di chiamate sono visualizzate solo quando il programma in fase di debug si trova in modalità interruzione.  
  
 Lo stack di chiamate rappresenta i vari contesti in cui si verifica l'esecuzione XSLT. Ad esempio, se viene rilevata una chiamata dal modello "a" al modello "b", il modello "a" e il modello "b" vengono visualizzati nella finestra dello stack di chiamate e il contesto corrente è posizionato in cima all'elenco. L'utente è in grado di visualizzare la query attualmente in esecuzione.  
  
 Se i modelli non dispongono di un nome nel file XSLT, vengono usati i nomi generati dal processore XSLT.  
  
 Se si fa clic su un elemento diverso da quello presente all'inizio dell'elenco, viene indicato al visualizzatore dove si è verificata la creazione di un ramo dell'esecuzione XSLT usando l'evidenziazione verde standard e le frecce verdi.  
  
## <a name="quickwatch-dialog-box"></a>Finestra di dialogo Controllo immediato  
 Il **controllo immediato** la finestra di dialogo viene utilizzata per valutare le espressioni XPath 1.0. Il nodo di contesto (il nodo `self::node()` proveniente dalla finestra Variabili locali) fornisce il contesto per l'esecuzione dell'espressione XPath. Il risultato dell'esecuzione dell'espressione XPath viene visualizzato nella finestra Espressioni di controllo.  
  
 Nell'elenco seguente vengono descritte alcune restrizioni alla valutazione dell'espressione XPath.  
  
-   Sono consentite solo le funzioni XPath incorporate.  
  
-   Non sono consentite le funzioni XSLT incorporate quali `document()`, `key()` e così via.  
  
-   Non sono consentite funzioni definite dall'utente.  
  
Per ulteriori informazioni, vedere [procedura: valutare un'espressione XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## <a name="disassembly-window"></a>Finestra Disassembly  
 Nella finestra Disassembly viene visualizzato il codice di assembly generato dal compilatore XSLT. Questa finestra può essere usata nello stesso modo in cui si usano tutte le altre finestre Disassembly di Visual Studio.  
  
 Per ulteriori informazioni, [procedura: utilizzare la finestra Disassembly](../debugger/how-to-use-the-disassembly-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug XSLT](../xml-tools/debugging-xslt.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Controllare le variabili in auto e variabili locali Windows in Visual Studio](../debugger/autos-and-locals-windows.md)