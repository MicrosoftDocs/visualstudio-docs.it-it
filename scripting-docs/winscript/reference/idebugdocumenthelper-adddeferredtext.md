---
title: IDebugDocumentHelper::AddDeferredText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifica l'helper che il testo specificato è disponibile, ma non fornisce i caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cChars`  
 [in] Numero di caratteri (Unicode) da aggiungere.  
  
 `dwTextStartCookie`  
 [in] Cookie definito host che rappresenta la posizione iniziale del testo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il metodo non è riuscita.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente all'host di rinvio che fornisce i caratteri per aggiungere fino a quando non sono necessarie, consentendo il supporto generare notifiche accurate e informazioni sulle dimensioni. Il `dwTextStartCookie` parametro è un cookie, definito dall'host, che rappresenta la posizione iniziale del testo. Le chiamate successive a `IDebugDocumentText::GetText` deve fornire questo cookie. Ad esempio, in un host che rappresenta il testo in caratteri DBCS, il cookie può essere un offset di byte.  
  
 Si presuppone che una singola chiamata a `IDebugDocumentText::GetText` possono ottenere i caratteri da più chiamate a `AddDeferredText`. Classi helper anche potrebbero richiedere più di una volta per lo stesso intervallo di caratteri posticipate.  
  
> [!NOTE]
>  Le chiamate a `AddDeferredText` non devono essere combinati con chiamate a `AddUnicodeText` o `AddDBCSText`. In questo caso, `E_FAIL` viene restituito.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)