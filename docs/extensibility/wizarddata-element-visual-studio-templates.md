---
title: Elemento WizardData (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6685c09e463b50f1fd856c65eadc09555a6dedb9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="wizarddata-element-visual-studio-templates"></a>Elemento WizardData (modelli di Visual Studio)
Specifica XML personalizzate  
  
 \<VSTemplate >  
 \<WizardData >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<WizardData>  
    <!-- XML to pass to the custom wizard extension -->  
    ...  
</WizardData>  
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Contiene tutti i metadati per il modello di progetto, un modello di elemento o lo starter kit.|  
  
## <a name="text-value"></a>Valore di testo  
 Il valore di testo è facoltativo.  
  
 Tale testo specifica il codice XML personalizzato per passare all'estensione della creazione guidata personalizzata specificata nel [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) elemento.  
  
## <a name="remarks"></a>Note  
 In questo elemento, è possibile specificare qualsiasi codice XML. Il codice XML verrà passato come parametro per l'estensione della creazione guidata personalizzata, consentendo l'estensione da utilizzare il contenuto di questo elemento. Viene eseguita alcuna convalida sui dati.  
  
 Il contenuto del `WizardData` elemento vengono passati invariati come parametro all'interno di dizionario di stringhe di parametri di `IWizard.RunStarted` (metodo). Il parametro è denominato $WizardData$.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono illustrati i metadati per il modello di progetto standard per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] applicazione Windows.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
    <WizardData>  
        <!-- XML to pass to the custom wizard extension -->  
    </WizardData>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Elemento WizardExtension (modelli di Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)   
 [Procedura: Usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)