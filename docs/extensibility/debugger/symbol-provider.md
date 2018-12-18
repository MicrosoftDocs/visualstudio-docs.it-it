---
title: Provider di simboli | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a98a5b80126bcb11109acedc2d24f226cde3714a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="symbol-provider"></a>Provider di simboli
Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug sui simboli generate dal compilatore di linguaggio per valutare variabili ed espressioni. Esegue l'operazione usando le interfacce di un provider di simboli (SP), denominato anche un gestore di simboli.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce SPs per codice gestito, così come codice nativo usando il formato di file di simboli di DataBase di programma (PDB). A meno che non vi è un nome sicuro, è necessario per il programma di utilizzare i simboli archiviati in un formato personalizzato, è consigliabile utilizzare la stored procedure fornite dal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Note di implementazione  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug prevedono di mettersi in contatto con la stored procedure utilizzando le interfacce di Common Language Runtime (CLR). Di conseguenza, un Service Pack che verranno usate con i motori di debug di Visual Studio deve supportare Common Language Runtime. Un elenco completo di tutte le interfacce di debug di CLR è reperibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Se il SP verranno usate solo con il motore di debug personalizzati, è possibile implementare il SP per adattarlo a seconda delle esigenze del motore di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)