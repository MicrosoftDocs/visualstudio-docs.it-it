---
title: UnInit | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9440eeda69592fad2e7c8f4e3e936f4b3dff29b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="uninit"></a>UnInit
Finalizza il file di log di grafica, lo chiude e libera le risorse utilizzate durante la registrazione attiva delle informazioni grafiche da parte dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Note  
 `UnInit` viene automaticamente chiamata quando viene eliminata un'istanza della classe `VsgDbg`. Se l'istanza `VsgDbg` non stava registrando attivamente le informazioni grafiche, questa operazione non ha effetto.  
  
 Una volta chiamata `UnInit` su un'istanza della classe `VsgDbg`, è possibile creare e un nuovo file di log di grafica chiamando `Init` e finalizzarlo chiamando `UnInit`. È possibile ripetere questa procedura tutte le volte che si desidera utilizzare la stessa istanza `VsgDbg` per creare diversi file di log di grafica indipendenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Init](init.md)