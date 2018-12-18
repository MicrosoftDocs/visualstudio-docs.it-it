---
title: Visual Studio Tools per Office Runtime scenari di installazione | Documenti Microsoft
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
helpviewer_keywords: Visual Studio Tools for Office runtime, installation scenarios
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9c63f5e4cef88ed927326b69f1fa389e34b06c8b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Scenari di installazione di Visual Studio Tools per Office Runtime
  È possibile installare Visual Studio 2010 Tools per Office Runtime in tre modi:  
  
-   Quando si installa Visual Studio.  
  
-   Quando si installa Microsoft Office.  
  
-   Quando si installa il runtime ridistribuibile di Visual Studio 2010 Tools per Office.  
  
 I componenti runtime vengono installati in base alla configurazione del computer e allo scenario di installazione.  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Componenti runtime installati in ogni scenario di installazione  
 Visual Studio 2010 Tools per Office Runtime include tre componenti: il caricatore di soluzioni di Office, le estensioni di Office per .NET Framework 3.5 e le estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Quando si installa il runtime, il caricatore di soluzioni Office viene sempre installato. L'installazione delle estensioni di Office per .NET Framework dipende dalla configurazione del computer e dallo scenario di installazione. Se una delle estensioni di Office non può essere installata quando il runtime viene installato per la prima volta, il runtime installerà automaticamente le estensioni di Office mancanti in un secondo momento, quando determinati requisiti saranno soddisfatti. Questa funzionalità del runtime è denominata *installazione su richiesta*.  
  
 Nella tabella seguente vengono illustrati i componenti runtime installati per impostazione predefinita in ogni scenario di installazione del runtime. Ulteriori informazioni su ogni scenario verranno visualizzate in un secondo momento.  
  
|Scenario di installazione del runtime|Caricatore di soluzioni di Office|Estensioni di Office per .NET Framework 3.5|Estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Estensioni di Office per [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|  
|-----------------------------------|----------------------------|--------------------------------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Con [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] e versione successiva|Yes|Sì, se è già installata .NET Framework 3.5.|Yes|Yes|  
|Con [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Yes|Sì, se è già installata .NET Framework 3.5.|No|No|  
|Con Office 2010 Service Pack 1 (SP1) o versione successiva|Yes|Sì, se è già installata .NET Framework 3.5.|Sì, se [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] è già installato.|No|  
|Con runtime ridistribuibile|Yes|Sì, se è già installata .NET Framework 3.5|Sì, se [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] è già installato.|Sì, se [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] è già installato.|  
  
### <a name="installing-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Installazione del runtime con Visual Studio o Microsoft Office Developer Tools per Visual Studio  
 Quando si installano gli strumenti di sviluppo di Office in Visual Studio, le estensioni di Office per [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] e [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] vengono sempre installate nel computer di sviluppo. Le estensioni di Office per .NET Framework 3.5 vengono installate solo se .NET Framework 3.5. è già presente nel computer di sviluppo. Se si installa .NET Framework 3.5 dopo l'installazione di [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], tramite il runtime vengono installate automaticamente le estensioni di Office per .NET Framework 3.5 la prima volta che si crea un progetto Office destinato a .NET Framework 3.5.  
  
> [!WARNING]  
>  Non è possibile creare un progetto Office destinato a .NET Framework 3.5 utilizzando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o versione successiva.  
  
 Per ulteriori informazioni su come installare Office developer tools, vedere [procedura: configurare un Computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
### <a name="installing-the-runtime-with-office"></a>Installazione del runtime con Office  
 Quando si installa Office, le estensioni di Office per .NET Framework 3.5 vengono installate solo se .NET Framework 3.5. è già presente nel computer di sviluppo. Se si installa .NET Framework 3.5 dopo Office, il runtime installerà automaticamente le estensioni di Office per .NET Framework 3.5 la prima volta che un'applicazione Office prova a caricare una soluzione destinata a .NET Framework 3.5.  
  
 Le estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva non vengono installate con Office, anche se [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva è già presente quando si installa Office.  
  
 Le estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] vengono installate con Office. Gli utenti finali possono ottenere le estensioni di Office per [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] installando un aggiornamento di Windows.  
  
 Per assicurarsi che gli utenti abbiano le estensioni necessarie per utilizzare l'applicazione, includere la versione più recente ridistribuibile di Visual Studio 2010 Tools per Office Runtime come prerequisito per la soluzione. Per ulteriori informazioni sui prerequisiti, vedere [prerequisiti per la distribuzione di soluzioni Office](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="installing-the-runtime-by-using-the-runtime-redistributable"></a>Installazione del runtime tramite il runtime ridistribuibile  
 È possibile installare il runtime eseguendo la versione ridistribuibile di Visual Studio 2010 Tools per Office Runtime manualmente o includendo il pacchetto ridistribuibile come prerequisito quando si distribuisce una soluzione Office.  
  
 Quando si installa il runtime utilizzando la versione ridistribuibile di Visual Studio 2010 Tools per Office Runtime, le estensioni di Office per .NET Framework 3.5 e le estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva vengono installate in un secondo momento se le corrispondenti versioni di .NET Framework sono già presenti nel computer. Se nel computer manca una di queste versioni di .NET Framework quando è installato il runtime, le estensioni di Office per la versione mancante di .NET Framework al momento non vengono installate. Se si installa la versione mancante di .NET Framework in un secondo momento, il runtime installerà automaticamente le estensioni di Office corrispondenti alla successiva installazione (se il runtime è stato installato con una soluzione che è stata distribuita tramite ClickOnce) o al successivo caricamento (se il runtime è stato installato con una soluzione che è stata distribuita tramite Windows Installer) di una soluzione che richiede le estensioni.  
  
 Per ulteriori informazioni sull'inclusione dei prerequisiti in una soluzione ClickOnce, vedere [procedura: installare i prerequisiti nei computer degli utenti finali per eseguire soluzioni Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Per ulteriori informazioni su come installare manualmente il runtime dal pacchetto ridistribuibile, vedere [procedura: installare Visual Studio Tools per Office Runtime ridistribuibile](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Assembly in Visual Studio Tools per Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
  
  