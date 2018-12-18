---
title: 'Preparazione al debug: Applicazioni Windows Forms | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bde2b6d2885a83057a0211f6da4f9e4ff65ef46f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-preparation-windows-forms-applications"></a>Preparazione al debug: applicazioni Windows Forms
Il modello di progetto Windows Forms consente di creare un'applicazione Windows Forms. Il debug di questo tipo di applicazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è una procedura molto semplice. Per ulteriori informazioni, vedere [creazione di un progetto di applicazione Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Quando si crea un progetto di Windows Form mediante il modello di progetto, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono definite automaticamente le impostazioni necessarie per le configurazioni di debug e di rilascio. Se necessario, è possibile modificare tali impostazioni. Queste impostazioni possono essere modificate nel  **\<nome progetto > pagine delle proprietà** la finestra di dialogo (**progetto** in Visual Basic).  
  
 Per ulteriori informazioni, vedere [impostazioni di proprietà consigliate](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Nella tabella riportata di seguito è indicata un'impostazione consigliata aggiuntiva per le proprietà.  
  
### <a name="configuration-properties-in-debug-tab"></a>Proprietà di configurazione disponibili nella scheda Debug  
  
|**Nome della proprietà**|**Impostazione**|  
|-----------------------|-----------------|  
|**Azione di avvio**|-Impostare su **progetto di avvio,** la maggior parte dei casi. Impostare su **Avvia programma esterno** se si desidera avviare un altro eseguibile quando si avvia il debug (in genere per il debug di DLL).|  
  
 È possibile eseguire il debug di applicazioni Windows Form dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oppure stabilendo una connessione a un'applicazione già in esecuzione. Per ulteriori informazioni sulla connessione, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Per eseguire il debug di Windows Forms Application in C#, F# o Visual Basic  
  
1.  Aprire il progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Creare i punti di interruzione necessari.  
  
     Poiché le applicazioni Windows Forms sono guidate da eventi, i punti di interruzione dovranno essere inseriti nel codice del gestore eventi o nei metodi chiamati dal codice del gestore eventi. Alcuni eventi tipici in cui impostare i punti di interruzione sono:  
  
    1.  Eventi associati a un controllo, ad esempio Click, Enter e così via  
  
    2.  Eventi associati all'avvio e alla chiusura dell'applicazione, ad esempio Load, Activated e così via  
  
    3.  Eventi di convalida e relativi allo stato attivo.  
  
     Per altre informazioni, vedere [Creazione di gestori eventi in Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).  
  
3.  Nel **Debug** menu, fare clic su **avviare**.  
  
4.  Eseguire il debug utilizzando le tecniche descritte in [nozioni di base di Debugger](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Procedura: impostare Debug e rilascio delle configurazioni](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Collegare a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Form](/dotnet/framework/winforms/index)