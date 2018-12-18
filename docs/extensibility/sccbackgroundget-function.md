---
title: Funzione SccBackgroundGet | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77e70720c9a26710c6d659ebac5b842bef3757eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet (funzione)
Questa funzione recupera dal controllo del codice sorgente ogni dei file specificati senza l'intervento dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto plug-in controllo di origine.  
  
 nFiles  
 [in] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 [in, out] Matrice di nomi di file da recuperare.  
  
> [!NOTE]
>  I nomi devono essere nomi di file locale completo.  
  
 dwFlags  
 [in] Flag di comando (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Un valore univoco associato all'operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata correttamente.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Il recupero in background è già in corso (plug-in controllo del codice sorgente deve restituire questo solo se non supporta operazioni batch simultanei).|  
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del relativo completamento.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene sempre chiamata su un thread diverso da quello che caricata il plug-in controllo del codice sorgente. Questa funzione non deve restituire fino al termine; Tuttavia, è possibile chiamato più volte con più elenchi di file, tutti nello stesso momento.  
  
 L'utilizzo del `dwFlags` argomento è lo stesso come il [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)