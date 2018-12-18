---
title: CreateInPlace (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e032a5fa57bd85aefdb5e8b7e0d270f491503e65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="createinplace-visual-studio-templates"></a>CreateInPlace (modelli di Visual Studio)
Specifica se creare il progetto ed eseguire la sostituzione del parametro nella posizione specificata, o eseguire la sostituzione del parametro in una posizione temporanea e quindi salvare il progetto nel percorso specificato.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<CreateInPlace >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CreateInPlace> true/false </CreateInPlace>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Questo testo deve essere `true` o `false`. Se `true`, viene creato il progetto e la sostituzione dei parametri viene eseguita nella posizione specificata nel **nuovo progetto** la finestra di dialogo. Se `false`, la sostituzione dei parametri viene eseguita in un percorso temporaneo e il progetto viene quindi copiato nel percorso specificato.  
  
## <a name="remarks"></a>Note  
 `CreateInPlace` è un elemento facoltativo. Il valore predefinito è `true`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per un modello [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <CreateInPlace>false</CreateInPlace>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)