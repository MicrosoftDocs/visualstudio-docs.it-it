---
title: Elemento DefaultName (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e67d8970859906e839abf89e85e38c24c2d88066
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="defaultname-element-visual-studio-templates"></a>Elemento DefaultName (modelli di Visual Studio)
Specifica il nome che verrà generato il sistema del progetto di Visual Studio per il progetto o un elemento quando viene creato.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<DefaultName >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
  
 Questo testo specifica il nome predefinito del progetto o dell'elemento.  
  
## <a name="remarks"></a>Note  
 `DefaultName` è un elemento facoltativo.  
  
 Per i progetti, questo elemento specifica il nome della directory in cui archiviare il progetto su disco. Per gli elementi, specifica il nome del file del file di origine.  
  
 Quando si crea un progetto o un elemento, è possibile modificare il nome predefinito utilizzando il **nome** opzione, è disponibile il **nuovo progetto** la finestra di dialogo o **Aggiungi nuovo elemento** la finestra di dialogo.  
  
 Se non si desidera il sistema del progetto per generare il nome predefinito per il progetto o un elemento, quindi impostare il [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) elemento `False`.  
  
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