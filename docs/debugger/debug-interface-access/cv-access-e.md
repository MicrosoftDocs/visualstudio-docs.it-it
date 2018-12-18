---
title: CV_access_e | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35b10f8a98284fdec9e94043a4b827fab226d3aa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="cvaccesse"></a>CV_access_e
Specifica l'ambito di visibilità (livello di accesso) di variabili e funzioni membro.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elementi  
 CV_private  
 Membro con accesso privato.  
  
 CV_protected  
 Membro con l'accesso protetto.  
  
 CV_public  
 Membro dispone di accesso pubblico.  
  
## <a name="remarks"></a>Note  
 Il `friend` identificatore di accesso non è incluso in questo caso perché è in genere utilizzata da funzioni non membro che hanno accesso a elementi privati e protetti della classe. Utilizzare il [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metodo per individuare i simboli con `SymTagFriend` accesso.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)