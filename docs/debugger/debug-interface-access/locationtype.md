---
title: LocationType | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f59f33ef51eee099a8dfe5bbc5c822f217f8cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="locationtype"></a>LocationType
Indica il tipo di informazioni di percorso contenuti in un simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Elementi  
 `LocIsNull`  
 Informazioni sul percorso non è disponibile.  
  
 `LocIsStatic`  
 Percorso è statico.  
  
 `LocIsTLS`  
 Si trova nell'archivio locale del thread.  
  
 `LocIsRegRel`  
 Il percorso è relativo al registro.  
  
 `LocIsThisRel`  
 Percorso è `this`-relativo.  
  
 `LocIsEnregistered`  
 Si trova in un registro.  
  
 `LocIsBitField`  
 Si trova in un campo di bit.  
  
 `LocIsSlot`  
 Trova uno slot di Microsoft Intermediate Language (MSIL).  
  
 `LocIsIlRel`  
 Il percorso è relativo al codice MSIL.  
  
 `LocInMetaData`  
 Si trova nei metadati.  
  
 `LocIsConstant`  
 Si trova in un valore costante.  
  
 `LocTypeMax`  
 Il numero di tipi di percorso di questa enumerazione.  
  
## <a name="remarks"></a>Note  
 Le proprietà disponibili per il [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interfaccia dipendono dalla posizione del simbolo all'interno del file di immagine. Per ulteriori informazioni, vedere [percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md).  
  
 I valori di questa enumerazione vengono restituiti da una chiamata al [idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)