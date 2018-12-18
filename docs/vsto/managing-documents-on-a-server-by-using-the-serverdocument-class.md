---
title: La gestione dei documenti in un Server utilizzando la classe ServerDocument | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef676de4ff352a557019f68037203364a97834d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>Gestione dei documenti di un server utilizzando la classe ServerDocument
  È possibile utilizzare la classe ServerDocument nel [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] per gestire diversi aspetti delle personalizzazioni a livello di documento, anche se non sono installati Microsoft Office Word e Microsoft Office Excel. È possibile eseguire le attività seguenti:  
  
-   Accedere e modificare i dati nella cache dei dati di un documento o una cartella di lavoro. Per ulteriori informazioni, vedere [utilizzo dei dati memorizzati nella cache del documento](#CachedData).  
  
-   Gestire l'assembly di personalizzazione che viene associato a un documento. Per ulteriori informazioni, vedere [gestione della personalizzazione del documento](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>Comprendere la classe ServerDocument  
 La classe ServerDocument è progettata per essere utilizzato nei computer che non è installato Office. Pertanto, in genere si utilizza questa classe nelle applicazioni che non si integrano con Office, ad esempio progetti di Console o Windows Form, anziché i progetti di Office. Utilizzare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe nell'assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 La classe ServerDocument consente di operare su personalizzazioni a livello di documento create mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Per ulteriori informazioni su Visual Studio 2010 Tools per Office Runtime e le estensioni di Office per .NET Framework, vedere [Visual Studio Tools per Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Se si dispone di un'applicazione legacy che usa la classe ServerDocument in Visual Studio Tools per Office system (versione 3.0 Runtime), Visual Studio Tools per Office system (versione 3.0 Runtime) deve essere installato nei computer che eseguono l'applicazione. Visual Studio 2010 Tools per Office Runtime non è possibile eseguire queste applicazioni.  
  
##  <a name="CachedData"></a> Utilizzo dei dati memorizzati nella cache nel documento  
 La classe ServerDocument fornisce membri che è possibile utilizzare per gestire la cache di dati nei documenti personalizzati. Per ulteriori informazioni sui dati memorizzati nella cache, vedere [la memorizzazione nella cache dati](../vsto/caching-data.md) e [accesso ai dati dei documenti sul Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Nella tabella seguente sono elencati i membri che è possibile utilizzare per lavorare con i dati memorizzati nella cache.  
  
|Attività|Membro da usare|  
|----------|-------------------|  
|Per determinare se un documento dispone di una cache di dati.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>.|  
|Per accedere ai dati memorizzati nella cache in un documento.<br /><br /> Per altre informazioni, vedere [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).|La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Gestione della personalizzazione del documento  
 È possibile utilizzare i membri della classe ServerDocument per gestire l'assembly di personalizzazione che viene associato a un documento. Ad esempio, è possibile rimuovere a livello di codice la personalizzazione da un documento in modo che il documento non è più parte di una personalizzazione.  
  
 Nella tabella seguente sono elencati i membri che è possibile utilizzare per gestire l'assembly di personalizzazione.  
  
|Attività|Membro da usare|  
|----------|-------------------|  
|Per determinare se un documento fa parte di una personalizzazione a livello di documento.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>.|  
|Per associare a livello di codice una personalizzazione a un documento in fase di esecuzione.<br /><br /> Per altre informazioni, vedere [procedura: associare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Uno del <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodi.|  
|Per rimuovere a livello di codice una personalizzazione da un documento in fase di esecuzione.<br /><br /> Per ulteriori informazioni, vedere [procedura: rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>.|  
|Per ottenere l'URL del manifesto di distribuzione che viene associato al documento.|La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: associare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Procedura: rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Panoramica di Visual Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Memorizzazione di dati nella cache](../vsto/caching-data.md)  
  