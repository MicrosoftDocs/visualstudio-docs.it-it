---
title: Elemento ProvideDefaultName (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c56ad565dfffd454eeca465aa4097c077fdc0a65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Elemento ProvideDefaultName (modelli di Visual Studio)
Specifica se il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sistema del progetto verrà generato un nome predefinito per il modello di **Aggiungi nuovo elemento** o **nuovo progetto** la finestra di dialogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProvideDefaultName >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 Il testo deve essere `true` o `false`, che indica se generare un nome predefinito per il modello nella **Aggiungi nuovo elemento** o **nuovo progetto** la finestra di dialogo.  
  
## <a name="remarks"></a>Note  
 `ProvideDefaultName` è un elemento facoltativo. Il valore predefinito è `true`.  
  
 Se il `ProvideDefaultName` elemento `false`, **nome** caselle del **Aggiungi nuovo elemento** e **nuovo progetto** finestre di dialogo contengono il valore `<Enter_name>`.  
  
 Utilizzare il [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) elemento per specificare il nome predefinito del progetto o elemento di **Aggiungi nuovo elemento** e **nuovo progetto** finestre di dialogo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice viene impostata la `ProvideDefaultName` elemento `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)