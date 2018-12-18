---
title: Funzioni di callback implementate dall'IDE | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdcc7d92770f486f9a345acf14e12e14214a2b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funzioni di callback implementate dall'IDE
Per rendere l'integrazione con l'ambiente di sviluppo integrato (IDE) come trasparente come possibili e per fornire un'esperienza unificata per l'utente finale, il plug-in controllo del codice sorgente possa utilizzare funzioni di callback che vengono implementate dall'IDE. Il plug-in può chiamare queste funzioni in momenti appropriati durante un'operazione di controllo del codice sorgente per passare informazioni a IDE; l'IDE quindi possibile visualizzare queste informazioni come gli elementi incorporati nell'interfaccia utente nativa. L'utente avrà un'esperienza meno frammentata in questo scenario rispetto a se il plug-in utilizzati la propria interfaccia utente.  
  
 Il file di intestazione richiesta è scc.h. Il percorso predefinito è \Program Files\VSIP 8.0\EnvSDK\common\inc\\. È anche nella cartella VSIP con l'esempio di plug-in controllo di origine a \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>In questa sezione  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Viene descritta la funzione di callback che viene utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal plug-in tramite l'IDE di controllo del codice sorgente.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Viene descritta la funzione di callback che viene utilizzata da [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando l'IDE non ha accesso completo alle informazioni che sono disponibile solo per il plug-in, ad esempio un elenco completo dei file nel controllo della versione di controllo del codice sorgente.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Viene descritta la funzione di callback che viene utilizzata il [SccQueryChanges](../extensibility/sccquerychanges-function.md) operazione.  
  
 [POPLISTFUNC](../extensibility/popdirlistfunc.md)  
 Viene descritta la funzione di callback che viene utilizzata il [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operazione.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Viene descritta la funzione di callback impostata da una chiamata al [SccSetOption](../extensibility/sccsetoption-function.md) che consente il controllo del codice sorgente plug-in per comunicare le modifiche di nome di nuovo l'IDE.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Apre un progetto.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Esamina l'elenco di file per il relativo stato corrente. Inoltre, viene utilizzato il `pfnPopulate` funzione per segnalare al chiamante quando un file non corrispondono ai criteri per il `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Esamina un elenco di directory e file in un progetto o i progetti inclusi nel controllo del codice sorgente. Ogni nome di directory e file trovato viene passato a una funzione di callback.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Esamina modifiche dei nomi che sono state apportate a un elenco di file. Ogni nome di file viene passato a una funzione di callback assieme al suo stato di modifica.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Imposta una vasta gamma di opzioni. Ogni opzione inizia con `SCC_OPT_xxx` e presenta un proprio set di valori definiti.  
  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)  
 Descrive il contenuto della sezione di riferimento del SDK di plug-in controllo di origine.