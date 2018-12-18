---
title: 'VsgDbg:: ~ VsgDbg (distruttore) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca62daa70602ac48e2b0871f764d0572b9da5f73
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
Elimina un'istanza di `VsgDbg` classe. Se le informazioni grafiche sono attiva la registrazione, il file di log di grafica viene finalizzato e chiuso e vengono rilasciate le risorse utilizzate durante l'acquisizione di informazioni grafiche attivamente.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VsgDbg::VsgDbg (Costruttore)](vsgdbg-vsgdbg-constructor.md)