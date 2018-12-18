---
title: IDiaLoadCallback2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09e835d8a7bfe0bc5d7ae06f0bac457126d21956
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Riceve i callback dal simbolo DIA procedura di individuazione, che consente le restrizioni da imporre il processo di individuazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) , questa interfaccia espone i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Determina se la ricerca di un file con estensione pdb nella directory di debug originale.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Determina se la ricerca dei file PDB è consentita nel percorso in cui si trova il file .exe.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Determina se cercando le informazioni di debug da file DBG.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Determina se la ricerca di file con estensione PDB è consentita nella directory radice di sistema.|  
  
## <a name="remarks"></a>Note  
 L'applicazione client implementa questa interfaccia e fornisce un riferimento nella chiamata al [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo. Tenere presente implementare tutti i metodi nel [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) anche l'interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)