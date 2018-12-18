---
title: Conversione tra tipi di sistema di progetto SharePoint e altri tipi di progetto di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6cf039f3d5330b2f4869ae323ac358a1220c2fbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Conversione tra tipi di sistemi di progetto SharePoint e altri tipi di progetto Visual Studio
  In alcuni casi potrebbe essere un oggetto nel sistema del progetto SharePoint e si desidera utilizzare le funzionalità di un oggetto corrispondente nel modello oggetto di automazione di Visual Studio o modello di integrazione, o viceversa. In questi casi, è possibile utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo del servizio di progetto SharePoint per convertire l'oggetto in un modello a oggetti diversi.  
  
 Ad esempio, potrebbe essere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto, ma si desidera utilizzare i metodi che sono disponibili solo in un <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> oggetto. In questo caso, è possibile utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo per convertire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> per un <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Per ulteriori informazioni sul modello oggetto di automazione di Visual Studio e il modello di oggetti di integrazione di Visual Studio, vedere [Panoramica della programmazione del modello di estensioni di SharePoint strumenti](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="types-of-conversions"></a>Tipi di conversione  
 Nella tabella seguente sono elencati i tipi di questo metodo consente di convertire tra il sistema di progetto SharePoint e altri modelli a oggetti di Visual Studio.  
  
|Tipo di sistema di progetto SharePoint|Tipi corrispondenti nei modelli a oggetti di automazione e integrazione|  
|------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> oppure<br /><br /> Qualsiasi interfaccia nel modello a oggetti Visual Studio integration implementate dall'oggetto COM sottostante per il progetto. Tali interfacce includono <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (o un'interfaccia derivata) e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Per un elenco delle interfacce implementate da progetti principale, vedere [componenti di base del modello di progetto](/visualstudio/extensibility/internals/project-model-core-components).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> oppure<br /><br /> Oggetto<xref:System.UInt32> valore (detto anche VSITEMID) che identifica il membro del progetto nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> che lo contiene. Questo valore può essere passato per il *itemid* parametro alcune <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metodi.|  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo per convertire un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> l'oggetto in un <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]  
  
 L'esempio presenta i requisiti seguenti:  
  
-   Un'estensione del sistema del progetto SharePoint che dispone di un riferimento all'assembly EnvDTE.dll. Per ulteriori informazioni, vedere [estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Codice che registra il `projectService_ProjectAdded` metodo per gestire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto. Per un esempio, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo del servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Procedura: recuperare il servizio di progetto SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Panoramica del modello di programmazione delle estensioni degli strumenti di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  