---
title: Restrizioni sulle lunghezze delle stringhe | Microsoft Docs
description: Informazioni sui limiti relativi alla lunghezza delle stringhe usate dalle varie funzioni imposte dall'API plug-in del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7fd0d88a50f64aee1f0bc5c273d7a3cd50c6f53f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900252"
---
# <a name="restrictions-on-string-lengths"></a>Restrizioni sulle lunghezze delle stringhe
L'API plug-in del controllo del codice sorgente limita la lunghezza delle stringhe usate in varie funzioni.

## <a name="string-length-values"></a>Valori di lunghezza stringa

|Costante|Valore|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> La lunghezza non include l'oggetto di `null` terminazione. Altre costanti con suffisso "_SIZE" anziché "_LEN" includono lo spazio per l'oggetto di `null` terminazione.

|Costante|Valore|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
