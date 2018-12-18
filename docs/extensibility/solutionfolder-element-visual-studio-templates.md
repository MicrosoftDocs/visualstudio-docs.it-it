---
title: Elemento SolutionFolder (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 635ebd5a8cfc962dd7b56b928b86a9d583a3575d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="solutionfolder-element-visual-studio-templates"></a>Elemento SolutionFolder (modelli di Visual Studio)
Raggruppa i progetti in modelli multiprogetto.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<SolutionFolder >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<SolutionFolder Name="DirectoryName">  
    ...  
</SolutionFolder>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Attributo obbligatorio.<br /><br /> Nome della cartella della soluzione.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica il percorso del file .vstemplate di un progetto in un modello multiprogetto.|  
|`SolutionFolder`|Elemento facoltativo.<br /><br /> Raggruppa i progetti in modelli multiprogetto.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|  
|`SolutionFolder`|Raggruppa i progetti in modelli multiprogetto.|  
  
## <a name="remarks"></a>Note  
 I modelli multiprogetto fungono da contenitori per due o più progetti. L'elemento `SolutionFolder` viene usato per organizzare i progetti in gruppi all'interno del modello. Le cartelle specificate dagli elementi `SolutionFolder` vengono create come cartelle della soluzione nel progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni sui modelli multiprogetto, vedere [procedura: creare modelli multiprogetto](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Esempio  
 Questo esempio usa l'elemento `SolutionFolder` per dividere il modello multiprogetto in due gruppi, `Math Classes` e `Graphics Classes`. Il modello contiene quattro progetti, due dei quali vengono inseriti in ogni cartella della soluzione.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare modelli basati su più progetti](../ide/how-to-create-multi-project-templates.md)