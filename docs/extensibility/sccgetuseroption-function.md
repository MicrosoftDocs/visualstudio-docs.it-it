---
title: Funzione SccGetUserOption | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetUserOption
helpviewer_keywords: SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5c23e1fd5614963d8f52edc019e99287187fd9a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption (funzione)
Questa funzione recupera un'ampia gamma di opzioni specifiche dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto plug-in controllo di origine.  
  
 nOption  
 [in] Opzione per recuperare (per le possibili opzioni, vedere la sezione Osservazioni).  
  
 lpVal  
 [out] Valore associato all'opzione.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Opzione è stata recuperata correttamente.|  
|SCC_E_OPNOTSUPPORTED|Opzione non è supportata.|  
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|  
  
## <a name="remarks"></a>Note  
 Tramite questo comando, sono supportate le seguenti opzioni:  
  
|Opzione User|Descrizione|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se l'utente desidera Estrai versione locale del file. `lpVal`viene assegnato `SCC_USEROPT_COLV_YES` (utente desidera estrarre i file locali) o `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codici di errore](../extensibility/error-codes.md)