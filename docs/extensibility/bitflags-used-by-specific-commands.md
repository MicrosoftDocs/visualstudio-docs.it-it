---
title: Flag di bit utilizzati dai comandi specifici | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be102b5eaf39db2fc7495c62c456e35e54ffd0f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="bitflags-used-by-specific-commands"></a>Flag di bit utilizzati dai comandi specifici
Il comportamento di un numero di funzioni nell'API di plug-in del controllo origine può essere modificato impostando uno o più bit in un singolo valore. Questi valori sono noti come flag di bit. Il flag di bit diversi usato dall'API plug-in controllo di origine sono descritte in dettaglio in questo caso, raggruppati per la funzione in cui vengono utilizzati.  
  
## <a name="checked-out-flag"></a>Check-Out Flag  
 Questo flag può essere impostato per uno di [SccAdd](../extensibility/sccadd-function.md) o [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Flag|Valore|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantenere il file estratto.|  
  
## <a name="add-flags"></a>Aggiungere contrassegni  
 Questi flag sono utilizzati per il [SccAdd](../extensibility/sccadd-function.md).  
  
|Flag|Valore|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|È previsto il plug-in controllo del codice sorgente di rilevare automaticamente se il file è di tipo testo o binario.|  
|`SCC_FILETYPE_TEXT`|0x01|Tipo di file è testo.|  
|`SCC_FILETYPE_BINARY`|0x04|Tipo di file è binario. **Nota:** `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` si escludono a vicenda. Impostare uno o nessuno.|  
|`SCC_ADD_STORELATEST`|0x02|Archiviare una versione più recente (nessun delta).|  
  
## <a name="diff-flags"></a>Flag di confronto  
 Il [SccDiff](../extensibility/sccdiff-function.md) utilizza questi flag per definire l'ambito di un'operazione diff. Il `SCC_DIFF_QD_xxx` si escludono a vicenda. Se viene specificato uno di essi, alcun feedback visivo non è concessa. In "diff veloce" (PC), il plug-in non determina come il file è diverso, solo se è diverso. Se nessuno di questi flag viene specificati, "diff visual" viene eseguita; differenze tra i file dettagliate vengono calcolate e visualizzate. Se il PC richiesto non è supportata, il plug-in si sposta la migliore successiva. Ad esempio, se l'IDE richiede un checksum e il plug-in non è supportata, non del plug-in un full-contenuto, selezionare (comunque molto più veloce rispetto a una rappresentazione visiva).  
  
|Flag|Valore|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorare le differenze.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorare le differenze di spazi vuoti. **Nota:** il `SCC_DIFF_IGNORECASE` e `SCC_DIFF_IGNORESPACE` flag sono facoltativi flag di bit.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|PC confrontando l'intero contenuto del file.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|PC da checksum.|  
|`SCC_DIFF_QD_TIME`|0x0040|PC dall'indicatore di data/ora di file.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Si tratta di una maschera utilizzata per controllare tutti i flag di bit PC. Non deve essere passato in una funzione. i tre flag di bit PC si escludono a vicenda. PC non significa sempre alcuna visualizzazione dell'interfaccia utente.|  
  
## <a name="populatelist-flag"></a>Flag PopulateList  
 Questo flag viene utilizzato il [SccPopulateList](../extensibility/sccpopulatelist-function.md) nel `fOptions` parametro.  
  
|Flag|Valore|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|L'IDE passa directory, non i file.|  
  
## <a name="populatedirlist-flags"></a>Flag PopulateDirList  
 Questi flag sono utilizzati per il [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) nel `fOptions` parametro.  
  
|Valore dell'opzione|Valore|Descrizione|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Esaminare solo un livello di directory per le directory (questo è il valore predefinito).|  
|SCC_PDL_RECURSIVE|0x0001|In modo ricorsivo esaminare tutte le directory in ogni directory specificata.|  
|SCC_PDL_INCLUDEFILES|0x0002|Includere i nomi di file nel processo di analisi.|  
  
## <a name="openproject-flags"></a>Flag OpenProject  
 Questi flag sono utilizzati per il [SccOpenProject](../extensibility/sccopenproject-function.md) nel `dwFlags` parametro.  
  
|Valore dell'opzione|Valore|Descrizione|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Se il progetto non esiste nel controllo del codice sorgente, è necessario crearlo. Se questo flag non è impostato, richiedere l'utente per il progetto per creare (a meno che non `SCC_OP_SILENTOPEN` flag è specificato).|  
|SCC_OP_SILENTOPEN|0x00000002L|Non chiedere conferma all'utente di creare un progetto. restituire `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Ottenere flag  
 Questi flag sono utilizzati per il [SccGet](../extensibility/sccget-function.md) e [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Flag|Valore|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|L'IDE passa le directory, non i file: ottenere tutti i file in tali directory.|  
|`SCC_GET_RECURSIVE`|0x00000002L|L'IDE passa directory: ottenere queste directory e in tutte le sottodirectory.|  
  
## <a name="noption-values"></a>Valori nOption  
 Questi flag sono utilizzati per il [SccSetOption](../extensibility/sccsetoption-function.md) nel `nOption` parametro.  
  
|Flag|Valore|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Impostare lo stato della coda di eventi.|  
|`SCC_OPT_USERDATA`|0x00000002L|Specificare i dati utente per `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|L'IDE in grado di gestire Annulla|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Impostare un callback per le modifiche di nome.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Disabilitare l'origine del plug-in dell'interfaccia utente l'estrazione dal controllo e non si imposta la directory di lavoro.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Aggiungere dal sistema di controllo di origine per specificare una directory di lavoro. Provare a condividere nel progetto associato se è un discendente diretto.|  
  
## <a name="dwval-bitflags"></a>dwVal flag di bit  
 Questi flag sono utilizzati per il [SccSetOption](../extensibility/sccsetoption-function.md) nel `dwVal` parametro.  
  
|Flag|Valore|Descrizione|Utilizzato da `nOption` valore|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Sospende l'attività di coda di eventi.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Consente la registrazione della coda eventi.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(Impostazione predefinita) Non possiede alcuna modalità di annullamento; plug-in necessario specificare se si desidera.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|L 1|IDE gestisce Annulla.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(Impostazione predefinita) OK per estrarre nell'interfaccia utente del plug-in; directory di lavoro è impostata.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|L 1|Nessun plug-in estrazione dell'interfaccia utente, nessuna directory di lavoro.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)