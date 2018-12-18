---
title: Elemento ProjectSubType (modelli di Visual Studio) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 11effbe7e1fc6c7380ba8dbc8da3f2fe14614b5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Elemento ProjectSubType (modelli di Visual Studio)
Classifica il modello in una sottocategoria del valore specificato nel `ProjectType` elemento.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectSubType >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
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
  
 Questo valore specifica la sottocategoria del modello.  
  
## <a name="remarks"></a>Note  
 `ProjectSubType` è un elemento figlio facoltativo di `TemplateData`.  
  
 Il `ProjectSubType` elemento fornisce una sottocategoria di [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) elemento. Questo valore può includere:  
  
-   `SmartDevice-NETCFv1`: Specifica che il modello è destinato il [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versione 1.0.  
  
-   `SmartDevice-NETCFv2`: Specifica che il modello è destinato il [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versione 2.0.  
  
 Se il modello contiene un `ProjectType` elemento con un valore di `Web`, `ProjectSubType` elemento specifica il linguaggio di programmazione del modello. Questo elemento può avere i valori seguenti:  
  
-   `CSharp`: Specifica che il modello crea un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] progetto Web o un elemento.  
  
-   `VisualBasic`: Specifica che il modello crea un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] progetto Web o un elemento.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra i metadati per un modello di progetto per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] destinata applicazione dispositivo il [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versione 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
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
 [Elemento ProjectType (modelli di Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)