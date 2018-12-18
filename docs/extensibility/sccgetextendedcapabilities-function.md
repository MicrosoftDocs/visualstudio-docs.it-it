---
title: Funzione SccGetExtendedCapabilities | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46ae3e051028e8239be5949500ebb710d67eee17
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities (funzione)
Questa funzione restituisce le funzionalità aggiuntive supportate dal plug-in controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto plug-in controllo di origine.  
  
 lSccExCaps  
 [in] Flag che specifica una funzionalità estesa per cui eseguire il test (vedere la tabella codice funzionalità estese in [flag di capacità](../extensibility/capability-flags.md) per i possibili flag).  
  
 pbSupported  
 [out] Restituisce diverso da zero (`TRUE`) se la funzionalità specificata è supportata; in caso contrario, restituisce zero (`FALSE`).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'operazione get funzionalità è stata completata.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Errore sconosciuto o non specificato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato su richiesta. ovvero, quando una funzionalità deve essere testata, questo metodo viene chiamato per determinare se che funzionalità è supportata. Viene specificato un solo flag alla volta.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codici di errore](../extensibility/error-codes.md)   
 [Flag di funzionalità](../extensibility/capability-flags.md)