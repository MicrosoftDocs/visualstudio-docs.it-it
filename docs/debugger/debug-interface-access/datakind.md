---
title: DataKind | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7fecbec475aee44efd9a91a24ec933dbbbcb17e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="datakind"></a>DataKind
Indica l'ambito di un valore di dati specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elementi  
 DataIsUnknown  
 Impossibile determinare il simbolo dei dati.  
  
 DataIsLocal  
 Elemento dati è una variabile locale.  
  
 DataIsStaticLocal  
 Elemento dati è una variabile locale statica.  
  
 DataIsParam  
 Elemento dati è un parametro formale.  
  
 DataIsObjectPtr  
 Elemento dati è un puntatore a oggetto (`this`).  
  
 DataIsFileStatic  
 Elemento dati è una variabile con ambito file.  
  
 DataIsGlobal  
 Elemento dati è una variabile globale.  
  
 DataIsMember  
 Elemento dati è una variabile membro oggetto.  
  
 DataIsStaticMember  
 Elemento dati è una variabile statica della classe.  
  
 DataIsConstant  
 Elemento dati è un valore costante.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione sono restituiti dal [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)