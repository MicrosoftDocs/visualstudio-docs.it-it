---
title: CaptureCurrentFrame | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 739f2a9a97fefcb1bc57c7987d5afec7a09ff4ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Acquisisce il resto del frame corrente nel file di log di grafica.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Note  
 Se è attualmente in corso un'altra acquisizione, ad esempio un'acquisizione avviata dalla funzione `BeginCapture`, tale acquisizione viene completata e registrata nel log di grafica come frame distinto. Immediatamente dopo, la diagnostica della grafica inizia ad acquisire la parte restante del frame corrente, che viene a sua volta registrata come frame distinto. La fine del frame corrente viene contrassegnata da una chiamata da presentare.  
  
 Per acquisire un frame, è necessario preparare l'app per acquisire e registrare le informazioni grafiche, vale a dire, è necessario chiamare [Init](init.md) tramite un'istanza del `VsgDbg` classe prima di chiamare `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Vedere anche  
 [Init](init.md)   
 [BeginCapture](begincapture.md)