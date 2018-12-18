---
title: IDiaLoadCallback::NotifyOpenPDB | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02069369e92862fffd90fcf4fe49c2d7e064f64e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Chiamato quando viene aperto un file con estensione pdb candidato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdbPath`  
 [in] Il percorso completo del file PDB.  
  
 `resultCode`  
 [in] Codice che indica l'esito positivo (`S_OK`) o negativo del carico, così come applicato a questo file.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Il codice restituito in genere viene ignorato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)