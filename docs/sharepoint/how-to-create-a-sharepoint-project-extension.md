---
title: "Procedura: Creare un'estensione di progetto SharePoint | Microsoft Docs"
ms.date: 04/28/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c42fc5ec197447a8def80d3aab7bb74def2db5e3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619381"
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>Procedura: Creare un'estensione di progetto SharePoint
  Creare un'estensione di progetto quando si desidera aggiungere funzionalità a qualsiasi progetto SharePoint aperto in Visual Studio. Per altre informazioni, vedere [estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="to-create-a-project-extension"></a>Per creare un'estensione di progetto

1.  Creare un progetto Libreria di classi.

2.  Aggiungere riferimenti agli assembly riportati di seguito:

    -   Microsoft.VisualStudio.SharePoint

    -   System.ComponentModel.Composition

3.  Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.

4.  Aggiungere il <xref:System.ComponentModel.Composition.ExportAttribute> alla classe. Questo attributo consente a Visual Studio di individuare e caricare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo al costruttore dell'attributo.

5.  Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo, utilizzare i membri del *projectService* parametro per definire il comportamento dell'estensione. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto che fornisce accesso agli eventi definiti nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> interfaccia.

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato come creare un'estensione di progetto semplice che gestisce la maggior parte degli eventi di progetto SharePoint che sono definiti dal <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> interfaccia. Per testare il codice, creare un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e quindi aggiungere altri progetti alla soluzione, modificare i valori di proprietà di progetto, eliminare o escludere un progetto. L'estensione invia una notifica degli eventi mediante la scrittura di messaggi per il **Output** finestra e **elenco errori** finestra.

  ```vb
    Imports Microsoft.VisualStudio.SharePoint
    Imports System.ComponentModel
    Imports System.ComponentModel.Composition

    Namespace Contoso.ExampleProjectExtension
      <Export(GetType(ISharePointProjectExtension))> _
      Class ExampleProjectExtension
        Implements ISharePointProjectExtension

        Private WithEvents projectService As ISharePointProjectService

        Public Sub Initialize(ByVal projectService As ISharePointProjectService) _
            Implements ISharePointProjectExtension.Initialize
            Me.projectService = projectService
        End Sub

        ' A project was added.
        Private Sub projectService_ProjectAdded(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectAdded
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was added: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was loaded in the IDE.
        Private Sub projectService_ProjectInitialized(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectInitialized
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being initialized: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' The name of a property was changed.
        Private Sub projectService_ProjectNameChanged(ByVal sender As Object, ByVal e As NameChangedEventArgs) _
            Handles projectService.ProjectNameChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project property value was changed.
        Private Sub ProjectPropertyChanged(ByVal sender As Object, ByVal e As PropertyChangedEventArgs) _
            Handles projectService.ProjectPropertyChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project is being removed or unloaded.
        Private Sub projectService_ProjectRemoved(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectRemoved
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was removed or unloaded.
        Private Sub projectService_ProjectDisposing(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectDisposing
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub
      End Class
    End Namespace
    ```

    ```csharp
    using Microsoft.VisualStudio.SharePoint;
    using System;
    using System.ComponentModel;
    using System.ComponentModel.Composition;

    namespace Contoso.ExampleProjectExtension
    {
      [Export(typeof(ISharePointProjectExtension))]
      internal class ExampleProjectExtension : ISharePointProjectExtension
      {
        public void Initialize(ISharePointProjectService projectService)
        {
            projectService.ProjectAdded += projectService_ProjectAdded;
            projectService.ProjectInitialized += projectService_ProjectInitialized;
            projectService.ProjectNameChanged += projectService_ProjectNameChanged;
            projectService.ProjectPropertyChanged += projectService_ProjectPropertyChanged;
            projectService.ProjectRemoved += projectService_ProjectRemoved;
            projectService.ProjectDisposing += projectService_ProjectDisposing;
        }

        // A project was added.
        void projectService_ProjectAdded(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was added: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is loaded in the IDE.
        void projectService_ProjectInitialized(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being initialized: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // The name of a project was changed.
        void projectService_ProjectNameChanged(object sender, NameChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project property value was changed.
        private void projectService_ProjectPropertyChanged(object sender, PropertyChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is being removed or unloaded.
        void projectService_ProjectRemoved(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project was removed or unloaded.
        void projectService_ProjectDisposing(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }
     }
  }
  ```

Questo esempio Usa il servizio di progetto SharePoint in cui per scrivere il messaggio il **Output** finestra e **elenco errori** finestra. Per altre informazioni, vedere [usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Per esempi che illustrano come gestire le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> eventi, vedere [come: Aggiungere una voce di menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) e [come: Aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

## <a name="compile-the-code"></a>Compilare il codice
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuire l'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [gli strumenti di distribuzione di estensioni per SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Procedura: Aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Procedura dettagliata: Creare un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
