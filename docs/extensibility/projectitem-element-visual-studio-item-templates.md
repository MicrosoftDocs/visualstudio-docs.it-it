---
title: Elemento ProjectItem (modelli di elemento di Visual Studio) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2fe9abece45efdc206e775bc8f5e79666e334001
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Elemento ProjectItem (modelli di elementi di Visual Studio)
Specifica un file incluso nel modello di elemento.  
  
> [!NOTE]
>  Il `ProjectItem` elemento accetta attributi diversi a seconda che il modello sia per un progetto o un elemento. Questo argomento viene illustrato il `ProjectItem` elemento per elemento. Per una spiegazione di `ProjectItem` elemento per i modelli di progetto, vedere [elemento ProjectItem (Modelli Visual Studio Project)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectItem >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`SubType`|Attributo facoltativo.<br /><br /> Specifica il sottotipo di un elemento in un modello di elemento a più file. Questo valore viene utilizzato per determinare l'editor che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà utilizzato per aprire l'elemento.|  
|`CustomTool`|Attributo facoltativo.<br /><br /> Imposta il CustomTool per l'elemento nel file di progetto.|  
|`ItemType`|Attributo facoltativo.<br /><br /> Imposta l'ItemType per l'elemento nel file di progetto.|  
|`ReplaceParameters`|Attributo facoltativo.<br /><br /> Valore booleano che specifica se l'elemento contiene i valori dei parametri devono essere sostituiti quando viene creato un progetto dal modello. Il valore predefinito è `false`.|  
|`TargetFileName`|Attributo facoltativo.<br /><br /> Specifica il nome dell'elemento che viene creato dal modello. Questo attributo è utile per utilizzare la sostituzione dei parametri per creare un nome di elemento.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Oggetto `string` che rappresenta il nome di un file nel file zip del modello.  
  
## <a name="remarks"></a>Note  
 `ProjectItem`è un elemento figlio facoltativo di `TemplateContent`.  
  
 Il `TargetFileName` attributo può essere utilizzato per rinominare i file con parametri. Ad esempio, se il file `MyFile.vb` esiste nella directory radice del file. zip il modello, ma si desidera che il file sia denominato in base al nome file fornito dall'utente nel **Aggiungi nuovo elemento** nella finestra di dialogo si utilizzerebbe il seguente codice XML:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Quando viene creato un elemento con questo modello, il nome del file si baserà sul nome utente specificato nella **Aggiungi nuovo elemento** la finestra di dialogo. Ciò è utile quando si creano modelli di elementi a più file. Per ulteriori informazioni, vedere [procedura: creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md) e [parametri di modello](../ide/template-parameters.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per il modello di elemento standard per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md)   
 [Parametri di modelli](../ide/template-parameters.md)