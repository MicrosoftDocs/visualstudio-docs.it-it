---
title: 'Idialoadcallback:: Notifydebugdir | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46621c667967f0b87d197839012e830207cc306a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Chiamato quando una directory di debug è stata trovata nel file .exe.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fExecutable`  
 [in] `TRUE` se la directory di debug viene letto da un file eseguibile (anziché un file DBG).  
  
 `cbData`  
 [in] Numero di byte dei dati nella directory di debug.  
  
 `data[]`  
 [in] Matrice che viene compilata con la directory di debug.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Il codice restituito in genere viene ignorato.  
  
## <a name="remarks"></a>Note  
 Il [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo richiama il callback quando viene trovata una directory di debug durante l'elaborazione del file eseguibile.  
  
 Questo metodo elimina la necessità per il client decodificare il file eseguibile e/o di debug per supportare le informazioni di debug diverso da quello trovato nel file PDB. Con questi dati, il client possa riconoscere il tipo di informazioni di debug disponibile e se si trova all'interno del file eseguibile o il file DBG.  
  
 La maggior parte dei client non sarà necessario questo callback perché le `IDiaDataSource::loadDataForExe` metodo apre in modo trasparente i file con estensione pdb e DBG quando è necessario soddisfare i simboli.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)