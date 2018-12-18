---
title: 'Vsgdbg:: Vsgdbg (costruttore) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04f33b117a7ee47fb0c11932c3722f6f2a4a3541
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (costruttore)
Costruisce un'istanza della classe `VsgDbg` con o senza la preparazione del componente della diagnostica della grafica integrato nell'applicazione per acquisire e registrare attivamente le informazioni grafiche per impostazione predefinita, in base al parametro booleano specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bDefaultInit`  
 `true` per specificare che il componente di diagnostica della grafica integrato nell'applicazione deve essere preparato per acquisire e registrare attivamente le informazioni grafiche; `false` per specificare che in questo momento l'applicazione non deve essere preparata per acquisire e registrare attivamente le informazioni grafiche.  
  
## <a name="remarks"></a>Note  
 Quando il costruttore viene chiamato con `bDefaultInit` impostato su `true`, il nome file del file di log di grafica viene determinato dal modo `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME` vengono definiti i simboli del preprocessore prima `vsgcapture.h` è incluso nell'applicazione.  
  
 Quando il costruttore viene chiamato con `bDefaultInit` impostato su `false`, il componente di diagnostica della grafica integrato nell'applicazione può essere preparato per acquisire e registrare attivamente le informazioni grafiche in un secondo momento chiamando la funzione `Init`.  
  
## <a name="see-also"></a>Vedere anche  
 [VsgDbg:: ~ VsgDbg (distruttore)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)