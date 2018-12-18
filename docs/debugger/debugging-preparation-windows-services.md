---
title: 'Preparazione al debug: Servizi di Windows | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0c359e2989b1768c9c8814b11a338968bf849f59
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-preparation-windows-services"></a>Preparazione al debug: servizi Windows
Un servizio Windows è un programma che viene eseguito in background in Microsoft Windows. Ne sono un esempio il servizio Telnet e il Time Service di Windows che aggiorna l'orologio visualizzato sul computer. I servizi Windows non possono essere eseguiti dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L'esecuzione deve avvenire nel contesto di Gestione controllo servizi. Per ulteriori informazioni, vedere [creazione di servizi Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [il debug di applicazioni di servizio Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications), e [applicazioni di servizio Windows](/dotnet/framework/windows-services/index).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Procedura: Eseguire il debug del metodo OnStart](../debugger/how-to-debug-the-onstart-method.md)