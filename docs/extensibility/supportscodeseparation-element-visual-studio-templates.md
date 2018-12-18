---
title: Elemento SupportsCodeSeparation (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: edd8eb9bbabb47444754d3756216fc81d02c7d7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>Elemento SupportsCodeSeparation (modelli di Visual Studio)
Specifica o meno il **inserire il codice in file separato** casella di controllo è abilitata nel **Aggiungi nuovo elemento** la finestra di dialogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SupportsCodeSeparation >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce la modalità di visualizzazione per il **nuovo progetto** o **nuovo elemento** la finestra di dialogo.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere `true` o `false`, a indicare o meno il **inserire il codice in file separato** casella di controllo è abilitata nel **Aggiungi nuovo elemento** la finestra di dialogo.  
  
## <a name="remarks"></a>Note  
 `SupportsCodeSeparation` è un elemento facoltativo. Il valore predefinito è `false`.  
  
 Il `SupportsCodeSeparation` elemento è disponibile solo per modelli di elementi di Web.  
  
 Separazione del codice o il modello di pagina code-behind, consente di mantenere il markup in un file e il codice di programmazione in un altro file. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e altri linguaggi .NET utilizzano questo modello.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente specifica per visualizzare il **inserire il codice in file separato** opzione.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)