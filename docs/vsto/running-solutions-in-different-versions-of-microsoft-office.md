---
title: Esecuzione di soluzioni in versioni diverse di Microsoft Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e228f407edd38e173da78c092c0cca7061a661a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="running-solutions-in-different-versions-of-microsoft-office"></a>Esecuzione di soluzioni in versioni diverse di Microsoft Office
    
## <a name="running-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Esecuzione di soluzioni Office create mediante Visual Studio 2010 e versioni successive  
  
|Versione di destinazione del modello di progetto di Office|Destinato a .NET Framework del progetto<sup>1</sup>|Versioni di Office che possono eseguire la soluzione|Runtime richiesto sul computer dell'utente finale|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Office 2016 e [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office system 2007<sup>2</sup>|Visual Studio 2010 Tools per Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office system 2007<sup>2</sup>|Visual Studio 2010 Tools per Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools per Office Runtime|  
|Microsoft Office System 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, <br /><br /> oppure<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office System 2007|Visual Studio 2010 Tools per Office Runtime|  
  
 1. Perché la soluzione funzioni è necessario che nei computer degli utenti finali sia installata la versione di .NET Framework di destinazione del progetto. Ad esempio, se il progetto è per .NET Framework 3.5, sui computer degli utenti finali deve essere installato .NET Framework 3.5. In questo esempio, la soluzione non verrà eseguita se nei computer degli utenti finali è installato solo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
 2. In questo scenario, la soluzione verrà eseguita senza errori in Microsoft Office System 2007 solo se non utilizza funzionalità introdotte in [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
## <a name="running-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Esecuzione di soluzioni Office create utilizzando versioni di Visual Studio precedenti a Visual Studio 2010  
 Le applicazioni Microsoft Office possono eseguire soluzioni create utilizzando versioni di Visual Studio precedenti a Visual Studio 2010. In alcuni casi, queste soluzioni richiedono versioni diverse di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Versioni diverse del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] possono essere installate nello stesso computer.  
  
 La tabella seguente illustra le versioni di Microsoft Office possono eseguire soluzioni create utilizzando versioni precedenti di Visual Studio e le versioni del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e .NET Framework sono necessarie per ciascuna soluzione.  
  
|Edizione di Visual Studio utilizzate per creare la soluzione|Versione di destinazione del modello di progetto di Office|Versioni di Office che possono eseguire la soluzione|Runtime richiesto sul computer dell'utente finale|Versione di .NET Framework richiesta nel computer dell'utente finale|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> oppure<br /><br /> Visual Studio Team System 2008|Microsoft Office System 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> Microsoft Office System 2007|Visual Studio 2010 Tools per Office Runtime<sup>1</sup><br /><br /> oppure<br /><br /> Microsoft Visual Studio Tools per Microsoft Office System (versione 3.0 Runtime)|.NET Framework 3.5|  
|Una delle seguenti edizioni di Visual Studio 2005 con VSTO 2005 SE<sup>2</sup> installato:<br /><br /> -Visual Studio 2005 Tools per Office<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|Microsoft Office System 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (solo 32 bit<sup>3</sup>)<br /><br /> Microsoft Office System 2007|Microsoft Visual Studio 2005 Tools per Office Second Edition Runtime (x86)|.NET framework 2.0, .NET Framework 3.0 o .NET Framework 3.5|  
|Una delle seguenti edizioni di Visual Studio:<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Visual Studio 2005 Tools per Office (con o senza VSTO 2005 SE<sup>2</sup> installato)<br />-Visual Studio Team System 2005 (con o senza VSTO 2005 SE<sup>2</sup> installato)<br />-Visual Studio 2005 Professional con VSTO 2005 SE<sup>2</sup> installato|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (solo 32 bit<sup>3</sup>)<br /><br /> Microsoft Office System 2007<br /><br /> Microsoft Office 2003|Microsoft Visual Studio 2005 Tools per Office Second Edition Runtime (x86)|.NET framework 2.0, .NET Framework 3.0 o .NET Framework 3.5|  
  
 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] includono Visual Studio 2010 Tools per Office Runtime. Pertanto, queste applicazioni utilizzano sempre Visual Studio 2010 Tools per Office Runtime anziché Visual Studio Tools per Microsoft Office System (versione 3.0 Runtime) in questo scenario. Le applicazioni di Microsoft Office 2007 possono utilizzare Visual Studio 2007 Tools per Office Runtime o Visual Studio Tools per Microsoft Office System (versione 3.0 Runtime).  
  
 2. VSTO 2005 SE è un componente aggiuntivo di Visual Studio gratuito che fornisce modelli di progetto di componente aggiuntivo VSTO per Microsoft Office 2003 e Microsoft Office System 2007. Può essere installato con Visual Studio 2005 Professional, Visual Studio 2005 Tools per Office o un'edizione di Visual Studio Team System 2005. Per ulteriori informazioni, vedere [Visual Studio 2005 Tools per Office Second Edition](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3. Le soluzioni Office che richiedono Visual Studio 2005 Tools per Office Second Edition Runtime non sono compatibili con le versioni a 64 bit di [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Per eseguire queste soluzioni nell'edizione a 64 bit di [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], è necessario aggiornare il progetto a [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] o a un progetto di Visual Studio 2008 destinato a Microsoft Office System 2007.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Panoramica di Visual Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Configurazione di computer per lo sviluppo di soluzioni Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  