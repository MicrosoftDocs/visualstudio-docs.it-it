---
title: Selezione e la valuta nell'IDE | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e46c18f424130a29085aaccad19328c9f86682f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="selection-and-currency-in-the-ide"></a>Selezione e la valuta nell'IDE
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) gestisce informazioni degli utenti oggetti attualmente selezionati tramite selezione *contesto*. Con il contesto di selezione, VSPackage possono prendere parte valuta rilevamento in due modi:  
  
-   Mediante propagazione delle informazioni di valuta i VSPackage all'IDE.  
  
-   Monitorando le selezioni di attualmente attive degli utenti all'interno dell'IDE.  
  
## <a name="selection-context"></a>Contesto della selezione  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globale tiene traccia della valuta IDE nel proprio oggetto di contesto di selezione globale. Nella tabella seguente sono mostrati gli elementi che costituiscono il contesto della selezione.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Gerarchia corrente.|In genere il progetto corrente. una gerarchia corrente di NULL indica che la soluzione nel suo complesso è corrente.|  
|ID elemento corrente|L'elemento selezionato all'interno della gerarchia corrente; Quando sono presenti più selezioni in una finestra del progetto, possono esserci più elementi correnti.|  
|Corrente`SelectionContainer`|Contiene uno o più oggetti per cui la finestra proprietà deve essere visualizzato le proprietà.|  
  
 Inoltre, l'ambiente gestisce due elenchi globali:  
  
-   Un elenco di identificatori di comando attivi dell'interfaccia utente  
  
-   Un elenco di tipi di elementi attualmente attivo.  
  
### <a name="window-types-and-selection"></a>Selezione e tipi di finestre  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organizza windows in due tipi generali:  
  
-   Windows tipo di gerarchia  
  
-   Finestre cornice, ad esempio documenti e degli strumenti di windows  
  
 L'IDE tiene traccia valuta in modo diverso per ognuno di questi tipi di finestra.  
  
 La finestra più comune di tipi di progetto è Esplora soluzioni, che controlla l'IDE. Tiene traccia di una finestra del tipo di progetto gerarchia globale e ItemID del contesto di selezione globale, e la finestra si basa sulla selezione dell'utente per determinare la gerarchia corrente. Per windows di tipo di progetto, l'ambiente fornisce il servizio globale <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, tramite cui VSPackage è possono monitorare i valori correnti per gli elementi aperti. Proprietà di navigazione nell'ambiente viene gestita da questo servizio globale.  
  
 Finestre cornice, d'altra parte, eseguire il DocObject all'interno della finestra cornice push il valore di SelectionContext (confrontarsi ItemID/gerarchia/SelectionContainer). . Finestre cornice utilizzano il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> a questo scopo. Dell'oggetto documento push solo i valori per il contenitore di selezione, lasciando i valori locali per la gerarchia e ItemID invariato, come avviene per i documenti figlio MDI.  
  
### <a name="events-and-currency"></a>Gli eventi e valuta  
 Due tipi di eventi possono verificarsi che influiscono sulla nozione dell'ambiente di valuta:  
  
-   Eventi che vengono propagati a livello globale e modificare il contesto della selezione finestra cornice. Esempi di questo tipo di evento di una finestra figlio MDI viene aperta una finestra di strumento globale in corso l'apertura o una finestra degli strumenti del tipo di progetto viene aperto.  
  
-   Eventi che modificano gli elementi tracciati all'interno del contesto di selezione cornice di finestra. Ad esempio la modifica di selezione all'interno di DocObject o la modifica della selezione in una finestra del tipo di progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md)   
 [Commenti e suggerimenti per l'utente](../../extensibility/internals/feedback-to-the-user.md)