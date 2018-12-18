---
title: Funzione SccDirQueryInfo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDirQueryInfo
helpviewer_keywords: SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c7a930c0fcdffbc76bba431012d76dd6d13686d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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