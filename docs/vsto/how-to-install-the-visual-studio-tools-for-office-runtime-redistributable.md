---
title: 'Procedura: installare Visual Studio Tools per Office Runtime ridistribuibile | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5f76191ca8b41f252e5009c0d3e7e09415f6f081
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Procedura: Installare il ridistribuibile di Visual Studio Tools per Office Runtime
  Deve essere installato in ogni computer che esegue le soluzioni create tramite gli strumenti di sviluppo di Microsoft Office in Visual Studio 2010 Tools per Office Runtime [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Il runtime viene installato automaticamente all'installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e di Microsoft Office. Per altre informazioni, vedere [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 Attenersi alle seguenti istruzioni di installazione manuale, se si verificano le situazioni riportate di seguito:  
  
-   È necessario installare il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] su un server. Ad esempio, si desidera utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per gestire soluzioni a livello di documento su un server.  
  
-   È necessario installare il runtime in un computer su cui sono già installati tutti i prerequisiti delle soluzioni di Office.  
  
    > [!NOTE]  
    >  Per installare .NET Framework e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], è necessario essere un amministratore del computer di sviluppo.  
  
### <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Per installare l'assembly nel runtime di Visual Studio Tools per Office  
  
1.  Installare [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versione successiva.  
  
    -   Per scaricare il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], vedere [Microsoft .NET Framework 4 (programma di installazione Web)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Per scaricare il [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], vedere [Microsoft .NET Framework 4 Client Profile (programma di installazione Web)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Per scaricare il [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], vedere [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Per installare [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], eseguire il file vstor_redist.exe.  
  
     È possibile scaricare questi file di installazione da [Visual Studio 2010 Tools per Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384). I prerequisiti per [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] corrispondono a quelli per .NET Framework.  
  
     Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]include i language pack. Se l'installazione di Windows è impostata su una lingua diversa dall'inglese, è possibile visualizzare i messaggi di runtime nella stessa lingua utilizzata da Windows. Analogamente, se gli utenti finali installano [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ed eseguono le soluzioni in versioni di Windows impostate su una lingua diversa dall'inglese, verranno visualizzati i messaggi di runtime nella stessa lingua di Windows. In alcuni casi, potrebbe essere necessario installare Language Pack aggiuntivi. Ad esempio, potrebbe essere necessario language pack aggiuntivi se la copia di Windows utilizza più di una impostazione della lingua o si passa a un'altra lingua dopo aver già installato il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. È possibile trovare i language pack in [Microsoft Visual Studio 2010 Tools per il Language Pack di Microsoft Office System (versione runtime 4.0 Runtime)](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida introduttiva &#40; sviluppo per Office in Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Procedura: configurare un Computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Procedura: installare assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [La gestione dei documenti in un Server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  