---
title: Distribuzione ClickOnce in Windows Vista | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 49ea73293e8cc491b515644a7e7d3f226a799339
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-deployment-on-windows-vista"></a>Distribuzione ClickOnce in Windows Vista
Compilazione di applicazioni in Visual Studio per controllo Account utente (UAC) in Windows Vista genera normalmente un manifesto incorporato, come dati binari con codifica XML nel file eseguibile dell'applicazione. Poiché le applicazioni ClickOnce e COM senza registrazione richiedono un manifesto esterno, Visual Studio genera un file per questi tipi di progetti che contiene i dati di controllo dell'account utente invece di un manifesto incorporato. Per impostazione predefinita, Visual Studio Usa le informazioni da un file denominato app. manifest per generare informazioni del manifesto UAC esterno (per la distribuzione ClickOnce e COM senza registrazione) o per incorporarlo nel file eseguibile dell'applicazione (per tutti gli altri casi). Visual Studio fornisce le seguenti opzioni per la generazione del manifesto:  
  
-   Utilizzare un manifesto incorporato. Incorporare i dati di controllo dell'account utente nel file eseguibile dell'applicazione e accedere come utente normale.  
  
     Questo è l'impostazione predefinita (a meno che non si utilizza ClickOnce). Questa impostazione supporta la normale modalità in cui viene eseguito in Visual Studio in Windows Vista. ovvero, la generazione di un manifesto interno ed esterno, entrambi con `AsInvoker`.  
  
-   Utilizzare un manifesto esterno. Generare un manifesto esterno utilizzando l'app. manifest.  
  
     Questo genera solo il manifesto esterno utilizzando le informazioni in App. manifest. Quando si pubblica un'applicazione tramite ClickOnce o COM senza registrazione, Visual Studio aggiunge al progetto di App. manifest e aggiunge questa opzione.  
  
-   Non utilizzare alcun manifesto. Creare l'applicazione senza un manifesto.  
  
     Questo approccio è noto anche come *virtualizzazione*. Utilizzare questa opzione per la compatibilità con le applicazioni esistenti da versioni precedenti di Visual Studio.  
  
 Le nuove proprietà sono disponibili sul **applicazione** pagina della finestra di Progettazione progetti (Visual c# solo per progetti) e nel formato di file di progetto MSBuild.  
  
 Si noti che il metodo per la configurazione di generazione del manifesto UAC nell'IDE di Visual Studio varia a seconda della visualizzazione di un tipo di progetto (Visual c# e Visual Basic).  
  
 Per informazioni sulla configurazione di progetti Visual c# per la generazione del manifesto, vedere [pagina applicazione, Progettazione progetti (c#)](../ide/reference/application-page-project-designer-csharp.md).  
  
 Per informazioni sulla configurazione di progetti di Visual Basic per la generazione del manifesto, vedere [pagina applicazione, Progettazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Autorizzazioni utente e Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)  (Applicazione (pagina), Creazione progetti (C#))  
 [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)