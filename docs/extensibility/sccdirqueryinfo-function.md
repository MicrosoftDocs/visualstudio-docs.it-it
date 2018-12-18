---
title: Funzione SccDirQueryInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1de32b8502e40c953bd7080d64e56047e6bb5ce9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo (funzione)
Questa funzione esamina un elenco di directory completo per il relativo stato corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 nDirs  
 [in] Il numero di directory selezionato deve essere sottoposto a query.  
  
 lpDirNames  
 [in] Matrice di percorsi completi delle directory in cui eseguire la query.  
  
 lpStatus  
 [in, out] Una struttura di matrice per il plug-in per restituire i flag di stato del controllo del codice sorgente (vedere [codice di stato Directory](../extensibility/directory-status-code-enumerator.md) per informazioni dettagliate).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|La query è riuscita.|  
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 La funzione riempie la matrice restituita con maschera di bit di bit dal `SCC_DIRSTATUS` famiglia (vedere [codice di stato Directory](../extensibility/directory-status-code-enumerator.md)), una voce per ogni directory specificata. Matrice di stato viene allocata dal chiamante.  
  
 Prima di una directory viene rinominata per verificare la directory di controllo del codice sorgente eseguendo una query se dispone di un progetto corrispondente, l'IDE Usa questa funzione. Se la directory non è incluso nel controllo del codice sorgente, l'IDE è possibile fornire l'avviso corretto all'utente.  
  
> [!NOTE]
>  Se un plug-in controllo del codice sorgente sceglie di non implementare una o più dei valori di stato, bit non implementata devono essere impostati su zero.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di stato di directory](../extensibility/directory-status-code-enumerator.md)