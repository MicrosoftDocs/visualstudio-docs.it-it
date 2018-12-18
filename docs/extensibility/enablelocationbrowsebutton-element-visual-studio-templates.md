---
title: Elemento EnableLocationBrowseButton (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d3573a1359cf7cc6347ede28b5361b01bbb7efb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>Elemento EnableLocationBrowseButton (modelli di Visual Studio)
Specifica se il **Sfoglia** pulsante è disponibile nel **nuovo progetto** nella finestra di dialogo, in modo che gli utenti possono modificare facilmente la directory predefinita in cui è stato salvato un nuovo progetto.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<EnableLocationBrowseButton >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>  
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
  
 Il testo deve essere `true` o `false`, che indica se visualizzare o meno il **Sfoglia** pulsante il **nuovo progetto** la finestra di dialogo.  
  
## <a name="remarks"></a>Note  
 `EnableLocationBrowseButton` è un elemento facoltativo. Il valore predefinito è `true`, che consente di visualizzare il **Sfoglia** pulsante il **nuovo progetto** la finestra di dialogo.  
  
 Nel **nuovo progetto** nella finestra di dialogo di **percorso** casella di testo specifica la directory in cui è stato salvato un nuovo progetto. Il **Sfoglia** pulsante consente di modificare questa directory visualizzando il **percorso progetto** nella finestra di dialogo che consente di passare facilmente a una directory diversa che è disponibile dal computer, e Scegliere quindi come la directory in cui salvare il nuovo progetto.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
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
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)