---
title: 'Idialoadcallback:: Notifydebugdir | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fad37acafae21c6e82839979360f4ed9574aef1a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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