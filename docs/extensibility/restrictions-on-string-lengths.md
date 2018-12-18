---
title: Restrizioni sulle lunghezze di stringa | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56a76e84c27684d422b6554b22c75d945df4e928
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="restrictions-on-string-lengths"></a>Restrizioni sulle lunghezze di stringa
L'API di plug-in controllo origine limita la lunghezza delle stringhe usate nelle varie funzioni.  
  
## <a name="string-length-values"></a>Valori di lunghezza stringa  
  
|Costante|Valore|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  La lunghezza non include l'interruzione del `null`. Altre costanti con un suffisso "_SIZE" anziché "_LEN" include lo spazio per l'interruzione del `null`.  
  
|Costante|Valore|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)