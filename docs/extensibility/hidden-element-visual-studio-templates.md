---
title: Nascosto elemento (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Hidden
helpviewer_keywords:
- Hidden element [Visual Studio project template]
ms.assetid: f37406b0-52e7-4f2c-aacf-bc8d7a4117b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b41005dc789cf464973b225c76b2845db5565772
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="hidden-element-visual-studio-templates"></a>Elemento Hidden (modelli di Visual Studio)
Specifica se il modello viene visualizzato in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Nascosta >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Hidden> true/false </Hidden>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere `true` o `false`, a indicare o meno il modello verrà visualizzato il **nuovo progetto** o **Aggiungi nuovo elemento** finestre di dialogo.  
  
## <a name="remarks"></a>Note  
 `Hidden` è un elemento facoltativo.  
  
 Se non specificato, nessun altro elemento figlio del `TemplateData` elemento sono necessari.  
  
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
        <Hidden>true</Hidden>  
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
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)