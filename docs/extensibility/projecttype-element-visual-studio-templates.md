---
title: Elemento ProjectType (modelli di Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento ProjectType e sul modo in cui Categorizza il modello di progetto in modo che venga visualizzato nella finestra di dialogo nuovo progetto o Aggiungi nuovo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d494d27b2a3302d0beff68b770d0172edb520f35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068687"
---
# <a name="projecttype-element-visual-studio-templates"></a>Elemento ProjectType (modelli di Visual Studio)
Categorizza il modello di progetto in modo che venga visualizzato sotto il gruppo specificato nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** .

> [!WARNING]
> I modelli di progetto sono supportati per C++ a partire da Visual Studio 2012. Non sono supportate per C++ in Visual Studio 2010 e versioni precedenti.

 \<VSTemplate> \<TemplateData>
 \<ProjectType>

## <a name="syntax"></a>Sintassi

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuna.

### <a name="child-elements"></a>Elementi figlio
 Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Questo valore specifica il tipo di progetto che verrà creato dal modello e deve contenere uno dei valori seguenti:

- `CSharp`: Specifica che il modello crea un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] progetto o un elemento.

- `VisualBasic`: Specifica che il modello crea un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] progetto o un elemento.

- `Web`: Specifica che il modello crea un progetto Web o un elemento. Se l' `ProjectType` elemento contiene questo valore, il linguaggio del progetto o dell'elemento viene definito nell' [elemento ProjectSubType (modelli di Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).

## <a name="remarks"></a>Commenti
 `ProjectType` è un elemento figlio obbligatorio di `TemplateData`.

 Il valore dell' `ProjectType` elemento specifica il punto in cui si trova il modello nella finestra di dialogo **nuovo progetto** o **Aggiungi nuovo elemento** . Ad esempio, un modello con un `ProjectType` valore di `CSharp` viene visualizzato sotto il nodo **Visual C#** nella finestra di dialogo **nuovo progetto** .

 Un sottotipo di modello può essere specificato tramite l'elemento [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) .

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i metadati per un modello di progetto per un' [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectSubType (modelli di Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
