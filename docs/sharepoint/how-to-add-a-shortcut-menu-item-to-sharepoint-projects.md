---
title: 'Procedura: aggiungere una voce di menu di scelta rapida ai progetti SharePoint | Microsoft Docs'
titleSuffix: ''
description: Aggiungere una voce di menu di scelta rapida a un progetto SharePoint in Visual Studio. La voce di menu viene visualizzata facendo clic con il pulsante destro del mouse su un nodo del progetto in Esplora soluzioni.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 54ac53ad317f500e787baebfdfeb4a86dc917e06
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216813"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Procedura: aggiungere una voce di menu di scelta rapida ai progetti SharePoint
  È possibile aggiungere una voce di menu di scelta rapida a qualsiasi progetto SharePoint. La voce di menu viene visualizzata quando un utente fa clic con il pulsante destro del mouse su un nodo di progetto **Esplora soluzioni**.

 Nei passaggi seguenti si presuppone che sia già stata creata un'estensione di progetto. Per altre informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Per aggiungere una voce di menu di scelta rapida ai progetti SharePoint

1. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementazione, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento del parametro *ProjectService* .

2. Nel gestore eventi per l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento, aggiungere un nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> oggetto alla <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> raccolta o del parametro degli argomenti dell'evento.

3. Nel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> gestore eventi per il nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> oggetto, eseguire le attività che si desidera eseguire quando un utente fa clic sulla voce di menu di scelta rapida.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come aggiungere una voce di menu di scelta rapida ai nodi del progetto SharePoint in **Esplora soluzioni**. Quando l'utente fa clic con il pulsante destro del mouse su un nodo di progetto e fa clic sulla voce **di menu Scrivi messaggio in finestra di output** , Visual Studio Visualizza un messaggio nella finestra **output** . In questo esempio viene utilizzato il servizio di progetto SharePoint per visualizzare il messaggio. Per ulteriori informazioni, vedere [utilizzare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un progetto di libreria di classi con riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estensione di progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
