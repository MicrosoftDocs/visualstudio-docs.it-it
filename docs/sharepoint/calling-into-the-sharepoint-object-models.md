---
title: Chiamate ai modelli a oggetti SharePoint | Documenti Microsoft
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
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: cbb1b8f573c6dd28280e30fd5602dff2dc30ae02
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="calling-into-the-sharepoint-object-models"></a>Chiamate ai modelli a oggetti di SharePoint
  Quando si creano estensioni per gli strumenti di SharePoint in Visual Studio, è necessario chiamare APIs di SharePoint per eseguire determinate attività. Ad esempio, se si crea un passaggio di distribuzione personalizzato per i progetti SharePoint, è necessario chiamare APIs di SharePoint per eseguire alcune attività per distribuire le soluzioni.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] forniscono due modelli a oggetti diversi che è possibile utilizzare nelle estensioni degli strumenti di SharePoint: un modello a oggetti server e un modello a oggetti client. Ogni modello a oggetti presenta vantaggi e svantaggi nel contesto di estensioni degli strumenti di SharePoint.  
  
 Per una panoramica dei modelli a oggetti di SharePoint, vedere [Panoramica della programmazione del modello di estensioni di SharePoint strumenti](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="using-the-client-object-model-in-extension-projects"></a>Utilizzando il modello a oggetti Client nei progetti di estensione  
 Quando si sviluppa un'estensione degli strumenti di SharePoint, è possibile utilizzare il modello a oggetti client nel progetto come qualsiasi altro set di API gestite. È possibile aggiungere riferimenti agli assembly nel modello a oggetti client per il progetto ed è possibile chiamare le API nel modello a oggetti client direttamente dal codice.  
  
 Tuttavia, il modello a oggetti client presenta due svantaggi nel contesto di estensioni degli strumenti di SharePoint:  
  
-   Il modello a oggetti client fornisce solo un subset del modello a oggetti server. Se è necessario utilizzare la funzionalità di SharePoint che non è esposta nel modello a oggetti client, è necessario utilizzare il modello a oggetti server.  
  
-   Anche se tramite il modello a oggetti client nelle estensioni degli strumenti di SharePoint dovrebbe funzionare nella maggior parte dei casi, possono verificarsi alcuni scenari in cui le chiamate al modello a oggetti client non funzionano come previsto. Il modello a oggetti client è progettato per essere utilizzata nelle applicazioni client per chiamare nei siti di SharePoint su un server remoto o una farm. Gli strumenti di SharePoint in Visual Studio funzionano solo con un'installazione di SharePoint locale nel computer di sviluppo. Pertanto, quando si utilizza il modello a oggetti client in un'estensione degli strumenti di SharePoint, chiamare il metodo in un sito di SharePoint nel computer locale, ovvero non come il modello a oggetti client è stato progettato per essere utilizzato.  
  
 Per una procedura dettagliata viene illustrato come utilizzare il modello a oggetti client in un'estensione degli strumenti di SharePoint in Visual Studio, vedere [procedura dettagliata: chiamata al modello di oggetto Client di SharePoint in un'estensione di Esplora Server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="using-the-server-object-model-in-extension-projects"></a>Utilizzando il modello a oggetti Server nei progetti di estensione  
 Il modello a oggetti server è un superset del modello a oggetti client. Quando si utilizza il modello a oggetti server, è possibile utilizzare tutte le funzionalità che [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] esporre a livello di codice.  
  
 Estensioni di strumenti di SharePoint possono usare le API nel modello a oggetti server, ma non possono chiamare direttamente le API. Il modello a oggetti server può essere chiamato solo da un processo a 64 bit destinato a .NET Framework 3.5. Tuttavia, le estensioni di strumenti di SharePoint richiedono il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e vengono eseguiti nel processo di Visual Studio a 32 bit. Ciò impedisce che le estensioni di strumenti di SharePoint riferimento direttamente gli assembly nel modello a oggetti server SharePoint.  
  
 Se si desidera utilizzare il modello a oggetti server in un'estensione degli strumenti di SharePoint, è necessario creare un oggetto personalizzato *comando di SharePoint* per chiamare l'API. Definire il comando di SharePoint in un assembly secondario che è possibile chiamare direttamente nel modello a oggetti server. Nel progetto di estensione, viene chiamato il comando di SharePoint indirettamente tramite il metodo ExecuteCommand di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto.  
  
 Per ulteriori informazioni sulla creazione e utilizzo dei comandi di SharePoint, vedere [procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) e [procedura: eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Per informazioni su come distribuire i comandi di SharePoint, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Per procedure dettagliate che illustrano come creare e utilizzare i comandi di SharePoint, vedere [procedura dettagliata: creazione di un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) e [procedura dettagliata: estensione di Esplora Server per visualizzazione Web Parti](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understanding-how-sharepoint-commands-are-executed"></a>Informazioni sulla modalità SharePoint vengono eseguiti i comandi  
 Gli assembly che definiscono i comandi di SharePoint vengono caricati in un processo host a 64 bit, denominato vssphost4.exe. Dopo aver chiamato un comando di SharePoint in un'estensione degli strumenti di SharePoint, il comando viene eseguito da vssphost4.exe anziché al processo di Visual Studio (devenv.exe) a 32 bit. È possibile controllare alcuni aspetti della modalità di esecuzione di comandi di SharePoint impostando i valori del Registro di sistema. Per ulteriori informazioni, vedere [estensioni di debug per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Procedura: eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Panoramica del modello di programmazione delle estensioni degli strumenti di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  