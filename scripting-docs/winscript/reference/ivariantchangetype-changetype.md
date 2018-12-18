---
title: IVariantChangeType::ChangeType | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Accetta un valore variant e crea una nuova variante con un tipo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvarDst`  
 [in, out] Una variante di contenere il valore rappresentato da `pvarSrc`, ma con il tipo specificato dal `vtNew`.  
  
 `pvarSrc`  
 [in] Un valore variant da modificare in un nuovo tipo.  
  
 `lcid`  
 [in] Contesto delle impostazioni locali da utilizzare durante la conversione gli argomenti a o da stringhe.  
  
 `vtNew`  
 [in] Specifica il tipo per `pvarDst` diventi.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il `pvarDst` e `pvarSrc` argomenti possono essere uguali, nel qual caso il valore originale viene sovrascritto. Questo metodo passa `pvarDst` per il `VariantClear` funzione e di conseguenza `pvarDst` deve essere inizializzato su un valore valido.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)