---
title: "Procedura: creare un'estensione di elemento di progetto SharePoint | Microsoft Docs"
description: Esaminare come creare un'estensione di elemento di progetto quando si desidera aggiungere funzionalità a un elemento del progetto SharePoint già installato in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8f01d3c15490a19c8cb5071cf7677fcf2b2a5384
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216618"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Procedura: creare un'estensione di elemento di progetto SharePoint
  Creare un'estensione di elemento del progetto quando si desidera aggiungere funzionalità a un elemento del progetto SharePoint già installato in Visual Studio. Per altre informazioni, vedere [estendere gli elementi del progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md).

### <a name="to-create-a-project-item-extension"></a>Per creare un'estensione di elemento di progetto

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft. VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.

4. Aggiungere gli attributi seguenti alla classe:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente a Visual Studio di individuare e caricare l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> tipo al costruttore dell'attributo.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In un'estensione di elemento di progetto questo attributo identifica l'elemento del progetto che si desidera estendere. Passare l'ID dell'elemento del progetto al costruttore dell'attributo. Per un elenco degli ID degli elementi del progetto inclusi in Visual Studio, vedere [estendere gli elementi del progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md).

5. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo usare i membri del parametro *projectItemType* per definire il comportamento dell'estensione. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> oggetto che fornisce l'accesso agli eventi definiti nelle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> interfacce e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . Per accedere a un'istanza specifica del tipo di elemento del progetto che si sta estendendo, gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi quali <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come creare un'estensione semplice per l'elemento del progetto ricevitore di eventi. Ogni volta che l'utente aggiunge un elemento di progetto ricevitore di eventi a un progetto SharePoint, questa estensione scrive un messaggio nella finestra di **output** e **Elenco errori** finestra.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb" id="Snippet1":::

 In questo esempio viene utilizzato il servizio di progetto SharePoint per scrivere il messaggio nella finestra di **output** e **Elenco errori** finestra. Per ulteriori informazioni, vedere [utilizzare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendi elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
