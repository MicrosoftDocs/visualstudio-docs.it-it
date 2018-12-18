---
title: Elemento ProjectType (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb16116994648ec70c770af7ca4932cd1443bd30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="projecttype-element-visual-studio-templates"></a>Elemento ProjectType (modelli di Visual Studio)
Classifica il modello di progetto in modo che venga visualizzato nel gruppo specificato di **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.  
  
> [!WARNING]
>  Per C++, a partire da Visual Studio 2012 sono supportati i modelli di progetto. Non sono supportate per C++ in Visual Studio 2010 e versioni precedenti.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectType >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
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
  
 Questo valore specifica il tipo di modello di progetto verrà creato e deve contenere uno dei valori seguenti:  
  
-   `CSharp`: Specifica che il modello verrà creato un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] progetto o un elemento.  
  
-   `VisualBasic`: Specifica che il modello verrà creato un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] progetto o un elemento.  
  
-   `Web`: Specifica che il modello verrà creato un progetto Web o un elemento. Se il `ProjectType` elemento contiene questo valore, il linguaggio del progetto o dell'elemento è definito nel [elemento ProjectSubType (modelli di Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Note  
 `ProjectType` è un elemento figlio obbligatorio di `TemplateData`.  
  
 Il valore della `ProjectType` elemento specifica dove si trova il modello nel **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo. Ad esempio, un modello con un `ProjectType` valore `CSharp` viene visualizzata sotto il **Visual c#** nodo il **nuovo progetto** la finestra di dialogo.  
  
 È possibile specificare un sottotipo di modello utilizzando il [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) elemento.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra i metadati per un modello di progetto per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dell'applicazione.  
  
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
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Elemento ProjectSubType (modelli di Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)