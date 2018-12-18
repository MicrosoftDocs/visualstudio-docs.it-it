---
title: Processo di hosting (vshost.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 716d19362495fccf475a068a28a9fe2acbe27b53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-process-vshostexe"></a>Processo di hosting (vshost.exe)
Il processo di hosting è una funzionalità di Visual Studio che migliora le prestazioni del debugger, abilita il debug in contesti di attendibilità parziale e la valutazione delle espressioni nella fase di progettazione. I file del processo di hosting contengono vshost nel nome del file e vengono inseriti nella cartella di output del progetto. Per altre informazioni, vedere [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  I file del processo di hosting (.vshost.exe) vengono usati da Visual Studio e non devono essere eseguiti direttamente o distribuiti con l'applicazione.  
  
## <a name="improved-debugging-performance"></a>Prestazioni di debug migliorate  
 Il processo di hosting crea un dominio dell'applicazione e associa il debugger all'applicazione. L'esecuzione di queste attività può causare un notevole ritardo tra l'inizio del debug e l'avvio dell'applicazione. Il processo di hosting consente di migliorare le prestazioni creando il dominio dell'applicazione, associando il debugger in background e salvando il dominio dell'applicazione e lo stato del debugger tra le esecuzioni dell'applicazione. Per altre informazioni sui domini dell'applicazione, vedere [Domini dell'applicazione](/dotnet/framework/app-domains/application-domains).  
  
## <a name="partial-trust-debugging"></a>Debug parzialmente attendibile  
 Un'applicazione può essere specificata come applicazione parzialmente attendibile nella [pagina di sicurezza](../ide/reference/security-page-project-designer.md) della **Creazione progetti**. Il debug di un'applicazione parzialmente attendibile richiede un'inizializzazione speciale del dominio dell'applicazione. Tale inizializzazione viene gestita dal processo di hosting.  
  
## <a name="design-time-expression-evaluation"></a>Valutazione delle espressioni per la fase di progettazione  
 La valutazione delle espressioni in fase di progettazione consente di testare il codice dalla finestra di **controllo immediato** senza dover eseguire l'applicazione. Il processo di hosting esegue questo codice durante la valutazione dell'espressione di progettazione. Per altre informazioni, vedere [Finestra di controllo immediato](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md)   
 [Procedura: Disabilitare il processo di hosting](../ide/how-to-disable-the-hosting-process.md)   
 [Finestra di controllo immediato](../ide/reference/immediate-window.md)   
 [Domini dell'applicazione](/dotnet/framework/app-domains/application-domains)