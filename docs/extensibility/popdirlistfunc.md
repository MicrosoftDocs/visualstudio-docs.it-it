---
title: PopDIRLISTFUNC | Microsoft Docs
description: Informazioni sulla funzione di callback POPDIRLISTFUNC, che viene passata alle directory di aggiornamento per scoprire quali sono sotto il controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c98b35d9f915e16072333c72df2e1e045850f5d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900395"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Si tratta di una funzione di callback data alla funzione [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) per aggiornare una raccolta di directory e (facoltativamente) nomi di file per individuare le directory nel controllo del codice sorgente.

 Il callback deve essere chiamato solo per le directory e i nomi di file (nell'elenco fornito alla funzione) effettivamente sotto `POPDIRLISTFUNC` il controllo del codice `SccPopulateDirList` sorgente.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parametri
 pvCallerData

[in] Valore utente assegnato a [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[in] `TRUE` se il nome in `lpDirectoryOrFileName` è una directory; in caso contrario, il nome è un nome di file.

 lpDirectoryOrFileName

[in] Percorso locale completo di una directory o di un nome di file sotto il controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'IDE restituisce un codice di errore appropriato:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Continuare l'elaborazione.|
|SCC_I_OPERATIONCANCELED|Consente di arrestare l'elaborazione.|
|SCC_E_xxx|Qualsiasi errore di controllo del codice sorgente appropriato deve arrestare l'elaborazione.|

## <a name="remarks"></a>Commenti
 Se il `fOptions` parametro della funzione contiene il flag , l'elenco conterrà probabilmente nomi `SccPopulateDirList` di file e nomi di `SCC_PDL_INCLUDEFILES` directory.

## <a name="see-also"></a>Vedere anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Codici di errore](../extensibility/error-codes.md)
