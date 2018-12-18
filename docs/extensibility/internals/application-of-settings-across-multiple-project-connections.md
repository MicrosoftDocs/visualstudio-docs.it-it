---
title: Applicazione delle impostazioni tra più connessioni di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0dff30ea80fb2de9bf4d90ffa48cd2f9b3d40756
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Applicazione delle impostazioni tra più connessioni di progetto
Per eseguire la stessa operazione di controllo di origine in più contesti di connessione o di più progetti compilati utilizzando la 1.2 di API plug-in controllo di origine, è possibile utilizzare un'operazione batch un plug-in controllo del codice sorgente. Batch possono essere utilizzati per eliminare ridondanti, finestre di dialogo dall'esperienza utente per ogni progetto.  
  
 Se un utente seleziona più elementi che appartengono a più di una connessione di un plug-in controllo del codice sorgente compilata utilizzando l'API plug-in origine controllo 1.1, (ad esempio, due progetti Web nei computer di condivisione di file diverso) e ne viene verificata l'uscita, l'utente visualizzerà la stessa finestra di dialogo più volte. Ciò si verifica anche se l'utente fa clic il **applica a tutte** casella di controllo nella finestra di dialogo, perché l'IDE Reimposta lo stato per ogni contesto di connessione.  
  
## <a name="new-capability-flag"></a>Flag di nuove funzionalità  
 `SccBeginBatch` Viene impostata dalla funzione di `SCC_CAP_BATCH` flag per indicare che un'operazione batch è in corso  
  
## <a name="new-functions"></a>Nuove funzioni  
 Le nuove funzioni seguenti supportano l'operazione batch:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 Il `SCCBeginBatch` inizia un gruppo di operazioni di controllo codice sorgente con una funzione. `SccEndBatch` Chiude il gruppo. I gruppi non possono essere annidati.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)