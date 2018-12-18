---
title: "Abilitazione di funzionalità di Debug in Visual C++ (-/D_DEBUG) | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f1067ee5b60b8a8a402c9612357f2d83b6da138
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Attivazione delle funzionalità di debug in Visual C++ (/D_DEBUG)
In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], le funzionalità di debug, ad esempio le asserzioni vengono attivate quando si compila il programma definendo il simbolo **debug** definito. È possibile definire **debug** in uno dei due modi:  
  
-   Specificare **#define debug** nel codice sorgente, o  
  
-   Specificare il **/D_DEBUG** l'opzione del compilatore. (Se si crea il progetto in Visual Studio mediante le procedure guidate, **/D_DEBUG** viene definito automaticamente nella configurazione di Debug.)  
  
 Quando **debug** è definito, il compilatore compila le sezioni di codice racchiuso **debug #ifdef** e `#endif`.  
  
 La configurazione di debug di un programma MFC deve essere collegata a una versione di debug della libreria MFC. File di intestazione MFC determinano la versione corretta della libreria MFC il collegamento in base ai simboli definiti, ad esempio **debug** e **Unicode**. Per informazioni dettagliate, vedere [versioni della libreria MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)