---
title: Elemento MaxFrameworkVersion (modelli di Visual Studio) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c473b3253809c09f9ba0af90f7a0fed349dedb93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (modelli di Visual Studio)
Specifica la versione massima di .NET Framework che viene richiesto dal modello. Determina se il modello viene visualizzato nel **modelli** sezione del **Aggiungi nuovo progetto** la finestra di dialogo, in base al valore selezionato nel **versioneFrameworkdidestinazione** casella della finestra di **Aggiungi nuovo progetto** la finestra di dialogo.  
  
 \<VSTemplate >  
 \<MaxFrameworkVersion >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce come vengono visualizzati in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere il più alto numero di versione di .NET Framework che è consentito dal modello.  
  
## <a name="remarks"></a>Note  
 `MaxFrameworkVersion` è un elemento facoltativo. L'elemento di `TemplateData` sezione del file. vstemplate funge da filtro per il **modelli** sezione del **Aggiungi nuovo progetto** la finestra di dialogo. Solo i modelli di cui i requisiti di .NET Framework sono meno di `MaxFrameworkVersion` verranno visualizzati i valori degli elementi, in base al valore selezionato nel **versione Framework di destinazione** casella del **Aggiungi nuovo progetto**la finestra di dialogo. Il `MaxFrameworkVersion` elemento deve essere omesso solo se necessario, per non causare inavvertitamente modelli venga visualizzato quando vengono utilizzati con le versioni più recenti di .NET Framework.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati di un controllo standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modello di classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 In questo esempio, la versione massima di .NET Framework necessaria per il modello, rappresentato da `MaxFrameworkVersion`, 3.5. Il modello precedente verrà visualizzato solo quando si seleziona 3.0 o 3.5 nel **versione Framework di destinazione** casella il **Aggiungi nuovo progetto** la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)