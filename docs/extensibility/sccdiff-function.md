---
title: Funzione SccDiff | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 30d8d6a4b8b400088d5feed663c8257215a0f8a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccdiff-function"></a>SccDiff (funzione)
Questa funzione consente di visualizzare (o facoltativamente solo Cerca) le differenze tra il file corrente (su disco locale) e la relativa ultima versione archiviata nell'origine del sistema di controllo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpFileName  
 [in] Nome del file per cui è richiesta la differenza.  
  
 fOptions  
 [in] Flag di comando. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|La versione di copia e il server di lavoro sono identici.|  
|SCC_I_FILESDIFFERS|La copia di lavoro è diverso dalla versione di controllo del codice sorgente.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
|SCC_E_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. differenza tra i file non è stato ottenuto.|  
|SCC_E_FILENOTEXIST|Il file locale non è stato trovato.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene utilizzata due scopi diversi. Per impostazione predefinita, viene visualizzato un elenco di modifiche in un file. Il plug-in controllo del codice sorgente verrà visualizzata la relativa finestra, in qualsiasi formato scelto, per visualizzare le differenze tra il file dell'utente su disco e la versione più recente del file di controllo del codice sorgente.  
  
 In alternativa, l'IDE semplicemente potrebbe essere necessario determinare se un file è stato modificato. Ad esempio, l'IDE potrebbe essere necessario determinare se è possibile estrarre un file senza informare l'utente. In tal caso, l'IDE passa il `SCC_DIFF_CONTENTS` flag. Il plug-in controllo del codice sorgente deve controllare il file su disco, byte per byte, nel file di controllo del codice sorgente e restituire un valore che indica se i due file sono diversi, senza alcuna visualizzazione all'utente.  
  
 Ottimizzare le prestazioni, il plug-in controllo del codice sorgente può utilizzare un'alternativa in base a un checksum o di un timestamp anziché il confronto byte per byte indicato `SCC_DIFF_CONTENTS`: queste forme di confronto sono ovviamente più veloce ma meno affidabile. Non tutti i sistemi di controllo di origine supportino questi metodi di confronto alternativo e il plug-in potrebbe essere necessario eseguire il fallback a un confronto di contenuto. Tutti i plug-in controllo codice sorgente, è necessario come minimo, supporta un confronto di contenuto.  
  
> [!NOTE]
>  I flag di differenza rapido si escludono a vicenda. È possibile non passare alcun flag, ma non è valido passare contemporaneamente più di uno. `SCC_DIFF_QUICK_DIFF`, ovvero una maschera che combina tutti i flag, può essere utilizzato per testare, ma non deve mai essere passato come parametro.  
  
|`fOption`|Significato|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Confronto tra maiuscole e minuscole (può essere utilizzata per differenza visual o rapido).|  
|SCC_DIFF_IGNORESPACE|Ignora gli spazi vuoti (può essere utilizzata per differenza visual o rapido).|  
|SCC_DIFF_QD_CONTENTS|Confronta automaticamente il file, byte per byte.|  
|SCC_DIFF_QD_CHECKSUM|Confronta automaticamente il file tramite un checksum quando è supportata. Se non è supportato, esegue il fallback a un confronto del contenuto.|  
|SCC_DIFF_QD_TIME|Confronta automaticamente il file tramite il relativo timestamp quando è supportata. Se non è supportato, esegue il fallback a un confronto del contenuto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)