---
title: IScriptEntry::GetBody | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9daa04009cf7088cbd21a2d3dfa185f581c157a3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Restituisce il testo che corrisponde al corpo di un `IScriptEntry` scriptlet, blocco di funzioni o blocco di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstr`  
 [out] Il testo che si trova nel corpo di una delle operazioni seguenti:  
  
-   Un `IScriptEntry` blocco di script  
  
-   Un `IScriptEntry` funzione in un blocco di funzioni  
  
-   Un `IScriptEntry` scriptlet gestore dell'evento  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)