---
title: Creare convalide di funzionalità e pacchetti per le soluzioni SharePoint
titleSuffix: ''
description: Creare regole di convalida personalizzate per verificare il pacchetto della soluzione generato da Visual Studio o per verificare un'intera funzionalità.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee6b27b92f1c79bfda95ba3d6dce7dbdce4a6fac
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216566"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>Creare convalide di funzionalità e pacchetti per le soluzioni SharePoint

  È possibile creare regole di convalida personalizzate per verificare il pacchetto della soluzione generato da Visual Studio. È possibile eseguire la convalida completa su un'intera funzionalità o un pacchetto selezionando **convalida** dal menu di scelta rapida di un pacchetto o di una funzionalità in **PackagingExplorer**. La convalida parziale viene eseguita quando si aggiungono nuove funzionalità o elementi del progetto SharePoint al progetto per determinare se il pacchetto o la funzionalità sono in uno stato valido.

### <a name="to-create-a-custom-package-validation-rule"></a>Per creare una regola di convalida del pacchetto personalizzata

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft. VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Creare una classe che implementi una delle interfacce seguenti:

    - Per creare una regola di convalida del pacchetto, implementare l' <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfaccia.

    - Per creare una regola di convalida della funzionalità, implementare l' <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfaccia.

4. Aggiungere alla <xref:System.ComponentModel.Composition.ExportAttribute> classe. Questo attributo consente a Visual Studio di individuare e caricare la regola di convalida. Passare il <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> tipo o al costruttore dell'attributo.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come creare una regola di convalida della funzionalità personalizzata.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. Composition.

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
