---
title: Elemento EnableEditOfLocationField (modelli di Visual Studio)
description: Informazioni sull'elemento EnableEditOfLocationField e su come specifica se l'utente può modificare il campo location.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- EnableEditOfLocationField (Visual Studio project templates)
ms.assetid: 51a91963-8a3f-4741-928e-bc90c11473bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3f2ca8799b0816ffe5c33d954d362183f330f25
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070193"
---
# <a name="enableeditoflocationfield-element-visual-studio-templates"></a>Elemento EnableEditOfLocationField (modelli di Visual Studio)
Specifica se l'utente può modificare il campo del percorso.

 \<VSTemplate> \<TemplateData>
 \<EnableEditOfLocationField>

## <a name="syntax"></a>Sintassi

```
<EnableEditOfLocationField> true/false </EnableEditOfLocationField>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 nessuno

### <a name="child-elements"></a>Elementi figlio
 nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere `true` o `false` , che indica se l'utente può modificare la casella di testo **percorso** nella finestra di dialogo **nuovo progetto** .

## <a name="remarks"></a>Commenti
 `EnableEditOfLocationField` è un elemento facoltativo. Il valore predefinito è `true` , che consente all'utente di modificare il valore nella casella di testo **percorso** della finestra di dialogo **nuovo progetto** .

 Nella casella di testo **percorso** della finestra di dialogo **nuovo progetto** viene specificata la directory in cui viene salvato un nuovo progetto.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un' [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableEditOfLocationField>false</EnableEditOfLocationField>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedi anche
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
