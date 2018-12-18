---
title: Creare modelli Web per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f94823131e568b3f1f254ead9d760210a4c9c1e0
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-manually-create-web-templates"></a>Procedura: Creare manualmente modelli Web

La creazione di un modello Web è diversa dalla creazione di altri tipi di modelli. Poiché i modelli di progetto Web vengono visualizzati nella finestra di dialogo **Aggiungi nuovo sito Web** e gli elementi di progetto Web vengono classificati in base al linguaggio di programmazione, il file con estensione vstemplate deve specificare il modello come modello Web e identificare il linguaggio di programmazione.

> [!NOTE]
> I modelli Web devono contenere un file WEBPROJ vuoto a cui si deve fare riferimento nel file VSTEMPLATE nell'attributo `File` dell'elemento `Project`. Benché i progetti Web non richiedano un file .\*proj, è necessario creare questo file stub perché il modello Web funzioni correttamente.

### <a name="to-manually-create-a-web-template"></a>Per creare manualmente un modello Web

1. Creare un progetto Web.

1. Modificare o eliminare i file nel progetto o aggiungere nuovi file al progetto.

1. Creare un file XML e salvarlo con estensione vstemplate nella stessa directory del progetto. Non aggiungerlo al progetto in Visual Studio.

1. Modificare il file XML con estensione vstemplate per specificare i metadati del modello di progetto. Per altre informazioni, vedere l'[esempio riportato di seguito](#example).

1. Individuare l'elemento `ProjectType` nel file con estensione vstemplate e impostare il valore di testo su `Web`.

1. Dopo l'elemento `ProjectType` aggiungere un elemento `ProjectSubType` e impostare il valore di testo sul linguaggio di programmazione del modello. Il linguaggio di programmazione può essere uno dei valori seguenti:

    - CSharp
    - VisualBasic

    Ad esempio:

    ```xml
    <TemplateData>
        ...
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        ...
    </TemplateData>
    ```

1. Selezionare i file nel modello (incluso il file VSTEMPLATE), fare clic con il pulsante destro del mouse sulla selezione e scegliere **Invia a** > **Cartella compressa**. I file verranno compressi in un file ZIP.

1. Inserire il file di modello ZIP nella directory dei modelli di progetti di Visual Studio. Per impostazione predefinita la directory è %USERPROFILE%\Documenti\Visual Studio \<Versione\>\ProjectTemplates.

## <a name="example"></a>Esempio

L'esempio seguente illustra un file VSTEMPLATE di base per un modello di progetto Web:

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche

[Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)  
[Riferimento allo schema di modello di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md)