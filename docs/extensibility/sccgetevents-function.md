---
title: Funzione SccGetEvents | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetEvents
helpviewer_keywords: SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e2e9a22d0340774087fab8dd7dc564f415d9d9aa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetevents-function"></a>SccGetEvents (funzione)
Questa funzione recupera un evento di stato in coda.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 lpFileName  
 [in, out] Buffer in cui il plug-in controllo del codice sorgente inserisce il nome di file restituito (un massimo di caratteri di MAX_PATH).  
  
 lpStatus  
 [in, out] Restituisce il codice di stato (vedere [codice di stato File](../extensibility/file-status-code-enumerator.md) per i valori possibili).  
  
 pnEventsRemaining  
 [in, out] Restituisce i numero di voci lasciato nella coda dopo questa chiamata. Se questo numero è elevato, il chiamante può decidere di chiamare il [SccQueryInfo](../extensibility/sccqueryinfo-function.md) per ottenere tutte le informazioni in una sola volta.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Ottenere gli eventi ha avuto esito positivo.|  
|SCC_E_OPNOTSUPPORTED|Questa funzione non è supportata.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene chiamata durante l'elaborazione di inattività per vedere se sono state eventuali aggiornamenti di stato per i file nel controllo del codice sorgente. Il plug-in controllo del codice sorgente gestisce lo stato di tutti i file di che cui è a conoscenza e ogni volta che una modifica di stato viene indicato il plug-in, lo stato e i file associato vengono archiviati in una coda. Quando `SccGetEvents` viene chiamato, nella parte superiore dell'elemento della coda viene recuperato e restituito. Questa funzione è vincolata da restituire solo le informazioni memorizzate nella cache e deve avere un metodo molto rapidi (vale a dire, non durante la lettura del disco o che richiede il controllo del codice sorgente per lo stato); in caso contrario, le prestazioni dell'IDE possono avviare una riduzione.  
  
 Se non sono presenti aggiornamenti di stato per i report, il plug-in controllo del codice sorgente archivia una stringa vuota nel buffer a cui puntato `lpFileName`. In caso contrario, il plug-in archivia il nome e percorso completo del file per cui è stato modificato le informazioni sullo stato e restituisce il codice di stato appropriato (uno dei valori descritti in dettaglio in [codice di stato File](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di stato file](../extensibility/file-status-code-enumerator.md)