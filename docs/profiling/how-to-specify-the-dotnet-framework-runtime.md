---
title: 'Procedura: Specificare il runtime di .NET Framework | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 9c2e584b467141557d6a8e2a586643417a47edf0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Procedura: Specificare il runtime di .NET Framework
Con il rilascio di [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], le applicazioni possono essere costituite da moduli compilati usando versioni diverse del runtime di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Per impostazione predefinita, gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilano il primo runtime caricato dall'applicazione. È possibile specificare il runtime di cui eseguire la profilatura quando si avvia un'applicazione con il profiler e quando si connette il profiler a un'applicazione già in esecuzione.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Per specificare il runtime di .NET Framework da profilare quando si avvia un'applicazione con il profiler  
  
1.  In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni, scegliere **Proprietà** e quindi fare clic su **Avanzate**.  
  
     Nella casella di riepilogo **Versione CLR di destinazione** viene visualizzato **Automatico** insieme alle versioni del runtime di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installate nel computer.  
  
2.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Fare clic sulla versione di CLR per la profilatura.  
  
    -   Fare clic su **Automatico** per eseguire la profilatura della prima versione caricata dall'applicazione.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Per specificare il runtime di .NET Framework da profilare quando si connette il profiler a un'applicazione  
  
1.  Nel menu Analizza scegliere Profiler e quindi fare clic su Connetti/Disconnetti.  
  
2.  Nella finestra di dialogo Connettere profiler a processo fare clic sul processo da profilare.  
  
     Nella casella di riepilogo **Versione CLR di destinazione** viene visualizzato **Automatico** insieme alle versioni del runtime di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installate nel computer.  
  
3.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Fare clic sulla versione di CLR per la profilatura.  
  
    -   Fare clic su **Automatico** per eseguire la profilatura della versione caricata quando il profiler viene connesso all'applicazione.