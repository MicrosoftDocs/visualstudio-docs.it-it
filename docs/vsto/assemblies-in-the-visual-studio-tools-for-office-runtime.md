---
title: Gli assembly di Visual Studio Tools per Office Runtime | Documenti Microsoft
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
helpviewer_keywords: Visual Studio Tools for Office runtime, assemblies
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 22750553e714c0aa02577ee95753e7d5b2bf13f4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assembly nel runtime di Visual Studio Tools per Office
  Quando si crea un progetto di Office, in Visual Studio vengono automaticamente aggiunti riferimenti agli assembly [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usati per il tipo di progetto e .NET Framework di destinazione del progetto. Sono disponibili diversi assembly nelle estensioni di Office per .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per altre informazioni sulle estensioni di Office, vedere [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Assembly nelle estensioni di Office per .NET Framework 4 e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per la documentazione sugli spazi dei nomi e i tipi di questi assembly, vedere [riferimenti gestiti &#40; sviluppo per Office in Visual Studio &#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Nome assembly|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Fornisce i seguenti tipi:<br /><br /> -Tipi per la creazione di personalizzazioni della barra multifunzione e smart tag. **Nota:** Smart tag sono deprecati in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Tipi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento e di riquadri attività personalizzati nei componenti aggiuntivi VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Excel e tipi di supporto. Per altre informazioni, vedere [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Fornisce tipi che è possibile usare per creare aree del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|  
|Microsoft.Office.Tools.Word.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Word e tipi di supporto. Per altre informazioni, vedere [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Fornisce i seguenti tipi:<br /><br /> -Le eccezioni che possono essere generate da Visual Studio Tools per Office runtime.<br />-Aree del modulo attributi da utilizzare durante la creazione di Outlook.|  
|Microsoft.Office.Tools.dll|Fornisce i tipi che fanno parte dell'infrastruttura runtime di Visual Studio Tools per Office e che non è previsto vengano usati direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fornisce i seguenti tipi:<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia, è possibile utilizzare per memorizzare gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [Caching Data](../vsto/caching-data.md).<br />-La <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interfaccia, è possibile implementare per eseguire ulteriori passaggi di installazione come passaggio finale del programma di installazione ClickOnce per una soluzione Office. Per ulteriori informazioni, vedere [distribuisce una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Le eccezioni che possono essere generate da Visual Studio Tools per Office runtime.<br />-Gli altri tipi che fanno parte di Visual Studio Tools per infrastruttura di runtime di Office e non deve essere utilizzato direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fornisce i seguenti tipi:<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (classe), che è possibile utilizzare per collegare gli assembly di personalizzazione ai documenti e accedere ai dati memorizzati nella cache dei documenti. Per altre informazioni, vedere [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Diverse classi che rappresentano la gerarchia dei dati memorizzati nella cache una personalizzazione a livello di documento. Per altre informazioni, vedere [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 I progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] fanno riferimento agli assembly seguenti. Questi assembly non fanno parte del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ridistribuibile. Sono invece gli assembly dipendenti che devono essere distribuiti con la soluzione. Per impostazione predefinita, vengono copiati nella cartella di output di compilazione del progetto (la proprietà **Copia localmente** di questi assembly è impostata su **True**). Se si distribuisce il progetto tramite ClickOnce, questi assembly vengono inclusi nel pacchetto generato.  
  
|Nome assembly|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fornisce le classi base per la classe `ThisAddIn` generata nei progetti di componente aggiuntivo VSTO e la classe Ribbon generata in tutti i progetti.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> -Classi di base generate `ThisWorkbook` e `Sheet` classi a livello di documento progetti per Excel.<br />-Windows Form che è possibile utilizzare nei fogli di lavoro nei progetti di Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fornisce le classi di base le classi `ThisAddIn` e le classi dell'area del modulo generate nei progetti di Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> -Classi di base generate `ThisDocument` classe nei progetti a livello di documento per Word.<br />-Windows Form che è possibile utilizzare nei documenti dei progetti di Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assembly nelle estensioni di Office per .NET Framework 3.5  
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per .NET Framework 3.5. Per la documentazione sugli spazi dei nomi e le classi in questi assembly, vedere la sezione di riferimento seguente nella documentazione di Visual Studio 2008: [http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Nome assembly|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -Microsoft.Office.Tools.AddIn classe di base per i componenti aggiuntivi VSTO.<br />-Classi per la creazione di personalizzazioni della barra multifunzione e smart tag. **Nota:** Smart tag sono deprecati in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Classi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento e di riquadri attività personalizzati nei componenti aggiuntivi VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Excel. Per altre informazioni, vedere [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fornisce classi che è possibile usare per creare arre del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Word. Per altre informazioni, vedere [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -La classe Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent, che fornisce le funzionalità di associazione dati per i controlli host nelle personalizzazioni a livello di documento.<br />-Gli altri tipi che fanno parte di Visual Studio Tools per infrastruttura di runtime di Office e non deve essere utilizzato direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -L'attributo Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute e interfaccia Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType, che è possibile utilizzare per memorizzare gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [Caching Data](../vsto/caching-data.md).<br />-Le eccezioni che possono essere generate da Visual Studio Tools per Office runtime.<br />-Gli altri tipi che fanno parte di Visual Studio Tools per infrastruttura di runtime di Office e non deve essere utilizzato direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fornisce l'interfaccia IAddInPostDeploymentAction, che è possibile implementare per eseguire ulteriori passaggi di installazione come passaggio finale del programma di installazione ClickOnce per una soluzione Office. Per altre informazioni, vedere [Advanced Office Solution Deployment](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> -La classe ServerDocument, che è possibile utilizzare a livello di codice per collegare gli assembly di personalizzazione ai documenti e accedere ai dati memorizzati nella cache nei documenti. Per altre informazioni, vedere [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Diverse classi che rappresentano la gerarchia dei dati memorizzati nella cache una personalizzazione a livello di documento. Per altre informazioni, vedere [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> -Le classi AddInSecurityEntry e Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList, che è possibile utilizzare per creare le voci dell'elenco per concedere l'attendibilità a Office di inclusione dell'utente nelle soluzioni destinate a .NET Framework 3.5.<br />-Gli altri tipi che fanno parte di Visual Studio Tools per infrastruttura di runtime di Office e non deve essere utilizzato direttamente dal codice.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Scenari di installazione di Visual Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  