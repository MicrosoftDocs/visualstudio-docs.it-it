---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44285e1d0ec0210193f196b5436407d8a0c2ff66
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Legge il numero specificato di byte a partire dall'offset specificato da un file eseguibile.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 fileOffset  
 [in] Offset nel file eseguibile per iniziare la lettura.  
  
 cbData  
 [in] Numero di byte da leggere.  
  
 pcbData  
 [out] Restituisce il numero di byte letti.  
  
 dati]  
 [in, out] Matrice che viene riempita con byte letti dal file.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato dal codice di supporto di DIA per caricare i byte di dati da un eseguibile usando un offset di file assoluto. Questo metodo viene chiamato supportano il [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)