---
title: IDispError::GetSource | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 922f95206d341773632b84c3922ea3b240d8d1ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Restituisce l'identificatore a livello di codice dipendente dalla lingua per la classe o l'applicazione che ha generato l'errore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrSource`  
 [out] Stringa che contiene un identificatore a livello di codice, nel formato `progname.objectname`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato per determinare la classe o l'applicazione in cui si è verificata l'eccezione. L'identificatore a livello di codice può essere restituito nel linguaggio specificato dall'identificatore delle impostazioni locali (LCID) fornito al momento della chiamata.  
  
> [!NOTE]
>  Questo metodo non è implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispError](../../winscript/reference/idisperror-interface.md)