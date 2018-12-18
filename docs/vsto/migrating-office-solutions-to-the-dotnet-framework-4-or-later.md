---
title: Migrazione di soluzioni Office a .NET Framework 4 o versioni successive | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8cb61186c7e8260578e9b69242c594c198f7e525
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Migrazione di soluzioni Office a .NET Framework 4 o versioni successive
  Se il framework di destinazione di un progetto di Office viene modificato per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o per versione successiva da una versione precedente di.NET Framework, potrebbero essere necessari alcuni passaggi aggiuntivi per poter continuare a eseguire la soluzione nei computer di sviluppo e degli utenti finali. Per ulteriori informazioni, vedere [modifiche necessarie per eseguire progetti di Office migrati a .NET Framework 4 o .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Inoltre, il progetto potrebbe non venire più compilato. Alcune funzionalità dei progetti di Office dispongono di modelli di programmazione diversi per le diverse versioni di .NET Framework. Quando il framework di destinazione di un progetto di Office viene modificato per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva da una versione precedente di .NET Framework, è necessario apportare le seguenti modifiche al codice del progetto:  
  
-   [L'aggiornamento di progetti di Excel e Word che si esegue la migrazione a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aggiornamento delle personalizzazioni della barra multifunzione nei progetti di Office migrati a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [L'aggiornamento di aree del modulo in progetti Outlook di cui eseguire la migrazione a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Il framework di destinazione di un progetto di Office cambia quando si aggiorna il progetto da una versione precedente di Visual Studio. Per altre informazioni, vedere [Upgrading and Migrating Office Solutions](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Per ulteriori informazioni sui motivi per cui alcune funzionalità nei progetti di Office presentano un modello di programmazione diverso quando la destinazione di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, vedere [modifiche alla progettazione dei progetti di Office destinati a .NET Framework 4 o .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) e [Visual Studio Tools per Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Risoluzione degli errori nelle soluzioni Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Supporto aggiuntivo per gli errori nelle soluzioni Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  