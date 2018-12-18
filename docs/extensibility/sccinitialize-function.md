---
title: Funzione SccInitialize | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1146573f3d969ffc5cd56576ba92faa4e6ffdce0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccinitialize-function"></a>SccInitialize (funzione)
Questa funzione inizializza il plug-in controllo del codice sorgente che fornisce funzionalità e i limiti per l'ambiente di sviluppo integrato (IDE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppvContext`  
 [in] Il plug-in controllo del codice sorgente può inserire qui un puntatore alla struttura relativo contesto.  
  
 `hWnd`  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 `lpCallerName`  
 [in] Il nome del programma di chiamata di plug-in di controllo del codice sorgente.  
  
 `lpSccName`  
 [in, out] Il buffer in cui il plug-in controllo del codice sorgente inserisce il proprio nome (non deve superare `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Restituisce il controllo del codice sorgente di flag di capacità del plug-in.  
  
 `lpAuxPathLabel`  
 [in, out] Il buffer in cui il plug-in controllo del codice sorgente inserisce una stringa che descrive il `lpAuxProjPath` restituito dal parametro di [SccOpenProject](../extensibility/sccopenproject-function.md) e [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (non deve superare `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Restituisce la lunghezza massima consentita per un commento di estrazione.  
  
 `pnCommentLen`  
 [out] Restituisce la lunghezza massima consentita per gli altri commenti.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Inizializzazione di controllo di origine ha avuto esito positivo.|  
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il sistema.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire l'operazione specificata.|  
|SCC_E_NONSPECFICERROR|Errore non specifico. controllo del codice sorgente non è stato inizializzato.|  
  
## <a name="remarks"></a>Note  
 L'IDE chiama questa funzione al primo caricamento del plug-in controllo del codice sorgente. In questo modo l'IDE passare a determinate informazioni, ad esempio il nome del chiamante, il plug-in. L'IDE nuovamente ottiene anche determinate informazioni, quali la lunghezza massima consentita per i commenti e le funzionalità del plug-in.  
  
 Il `ppvContext` punta a un `NULL` puntatore. Il plug-in controllo del codice sorgente è possibile allocare una struttura per l'utilizzo e archiviare un puntatore alla struttura in `ppvContext`. L'IDE passerà l'indicatore di misura a qualsiasi altra funzione API VSSCI, consentendo il plug-in per sono disponibili informazioni di contesto senza ricorrere a un archivio globale e per supportare più istanze di plug-in. Questa struttura deve essere deallocata quando il [SccUninitialize](../extensibility/sccuninitialize-function.md) viene chiamato.  
  
 Il `lpCallerName` e `lpSccName` i parametri consentono l'IDE e il plug-in controllo del codice sorgente per lo scambio di nomi. Questi nomi possono essere utilizzati per distinguere tra più istanze o effettivamente possono essere visualizzati nei menu o finestre di dialogo.  
  
 Il `lpAuxPathLabel` parametro è una stringa utilizzata come un commento per identificare il percorso del progetto ausiliario archiviato nel file di soluzione e passato il controllo del codice sorgente plug-in una chiamata al [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] viene utilizzata la stringa "progetto SourceSafe:"; altri plug-in di controllo sorgente devono evitare l'utilizzo di questa stringa particolare.  
  
 Il `lpSccCaps` parametro fornisce il controllo del codice sorgente plug-in una posizione in cui archiviare i flag di bit che indica le capacità del plug-in. (Per un elenco completo dei flag di bit di funzionalità, vedere [flag di capacità](../extensibility/capability-flags.md)). Ad esempio, se i piani di plug-in per scrivere i risultati in una funzione di callback fornito dal chiamante, il plug-in necessario impostare la funzionalità di bit SCC_CAP_TEXTOUT. Questo potrebbe segnalare l'IDE per creare una finestra per i risultati di controllo di versione.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Flag di funzionalità](../extensibility/capability-flags.md)