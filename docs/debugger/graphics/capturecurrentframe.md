---
title: CaptureCurrentFrame | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41169494424310427e5a8ae6a0af533bdf4be834
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
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