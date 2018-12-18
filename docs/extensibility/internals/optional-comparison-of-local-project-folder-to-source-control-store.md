---
title: Confrontare la cartella di progetto per l'archivio del controllo codice sorgente | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cbf4e9f2ccbe895db79115949818345c62245f71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Confronto facoltativo della cartella di progetto locale per l'archivio del controllo codice sorgente
Nell'origine, controllare il confronto tra la cartella di progetto locale e il controllo del codice sorgente viene eseguito utilizzando le funzioni di plug-in API 1.2 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 All'interno di **Esplora**, se si seleziona una cartella anziché un singolo file, il **confrontare versioni** richiama il nuovo menu di scelta rapida [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [ SccDirDiff](../../extensibility/sccdirdiff-function.md) il plug-in controllo del codice sorgente.  
  
## <a name="new-capability-flags"></a>Nuovo flag di capacità  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nuove funzioni  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Il `SccDirQueryInfo` funzione viene chiamata prima `SccDirDiff` per determinare se la directory di lavoro è di controllo del codice sorgente. Il `SccDirDiff` funzione consente di visualizzare le differenze tra la directory corrente e la cartella del controllo origine corrispondente. Questo comando richiede il controllo del codice sorgente plug-in per visualizzare l'elenco delle modifiche alla directory. Un plug-in controllo del codice sorgente fornisce la propria interfaccia utente per visualizzare le differenze.  
  
> [!NOTE]
>  Questa funzione utilizza gli stessi flag di comando come [SccDiff](../../extensibility/sccdiff-function.md). Come un provider di plug-in controllo codice sorgente, è possibile scegliere di non supportare l'operazione "diff veloce" per le directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)