---
title: Funzione SccDirDiff | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d2bea7816375da1131f557ebcbe206056f347f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccdirdiff-function"></a>SccDirDiff (funzione)
Questa funzione consente di visualizzare le differenze tra la directory corrente del disco di client e il progetto corrispondente nel controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpDirName  
 [in] Percorso completo della directory locale per cui si desidera mostrare una differenza di visual.  
  
 dwFlags  
 [in] Flag di comando (vedere la sezione Osservazioni sezione).  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|La directory sul disco è lo stesso come il progetto nel controllo del codice sorgente.|  
|SCC_I_FILESDIFFER|La directory sul disco è diversa dal progetto nel controllo del codice sorgente.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
|SCC_E_FILENOTCONTROLLED|La directory non è incluso nel controllo del codice sorgente.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
|SCC_E_FILENOTEXIST|Impossibile trovare la directory locale.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene utilizzata per indicare il controllo del codice sorgente plug-in da visualizzare all'utente un elenco di modifiche in una directory specificata. Il plug-in verrà visualizzata la relativa finestra, in un formato di propria scelta, per visualizzare le differenze tra la directory dell'utente su disco e il progetto corrispondente nel controllo della versione.  
  
 Se un confronto supporta plug-in di directory affatto, deve supportare il confronto delle directory con cadenza nome del file anche se non sono supportate le opzioni "rapida diff".  
  
|`dwFlags`|Interpretazione|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Confronto tra maiuscole e minuscole (può essere utilizzata per diff veloce o visivo).|  
|SCC_DIFF_IGNORESPACE|Ignora gli spazi vuoti (può essere utilizzato per rapida diff o visual).|  
|SCC_DIFF_QD_CONTENTS|Se supportata dal plug-in controllo del codice sorgente, confronta automaticamente nella directory, byte per byte.|  
|SCC_DIFF_QD_CHECKSUM|Se supportata dal plug-in, automaticamente confronta la directory tramite un checksum o, se non è supportato, esegue il fallback a SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Se supportata dal plug-in, automaticamente confronta la directory tramite il relativo timestamp o, se non è supportato, esegue il fallback su SCC_DIFF_QD_CHECKSUM o SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Questa funzione utilizza gli stessi flag di comando come il [SccDiff](../extensibility/sccdiff-function.md). Tuttavia, un plug-in controllo del codice sorgente può scegliere di non supporta l'operazione "rapida diff" per le directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)