---
title: NumberOfParentCategoriesToRollUp (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e94e4b67727308657becac829bcdd30e571a2be6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="numberofparentcategoriestorollup-visual-studio-templates"></a>NumberOfParentCategoriesToRollUp (modelli di Visual Studio)
Specifica il numero di categorie padre che consente di visualizzare il modello di **nuovo progetto** la finestra di dialogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<NumberOfParentCategoriesToRollUp >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<NumberOfParentCategoriesToRollUp>  
    1  
</NumberOfParentCategoriesToRollUp>  
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
 Un `integer` è richiesto un valore.  
  
 Questo valore specifica il numero di categorie padre che consente di visualizzare il modello di **nuovo progetto** la finestra di dialogo.  
  
## <a name="remarks"></a>Note  
 `NumberOfParentCategoriesToRollUp` è un elemento facoltativo.  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono illustrati i metadati per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione Windows. Se un modello i metadati viene inserito in una cartella due livelli sotto il livello principale [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] il modello di nodo, verrà visualizzato nel nodo di livello superiore di **nuovo progetto** la finestra di dialogo. Se il `NumberOfParentCategoriesToRollUp` non è impostata, il modello viene visualizzato solo nel nodo in cui si trova fisicamente.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>  
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
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)