---
title: Riferimenti dello Schema dei modelli di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- VSTEMPLATE files
- Visual Studio templates, schema
- .vstemplate files
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08e0758638bbb73cb999fb6b8aba2f195b603b42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-template-schema-reference"></a>Riferimenti allo schema dei modelli di Visual Studio
In questa sezione vengono fornite informazioni sugli elementi XML nei file .vstemplate, ovvero i file nei quali sono archiviati i metadati per i modelli di progetto, i modelli di elemento e gli starter kit.  
  
 È possibile utilizzare il file vstemplate.xsd per convalidare i file .vstemplate personalizzati. Questo file è disponibile in... \\ *Cartella di installazione di visual Studio*\Xml\Schemas\1033\vstemplate.xsd.  
  
|Elemento|Elementi figlio|Attributi|  
|-------------|--------------------|----------------|  
|[appliesTo](../extensibility/appliesto-element-visual-studio-templates.md)|Nessuno|Nessuno|  
|[Assembly (modello)](../extensibility/assembly-element-visual-studio-templates.md)|--|--|  
|[Assembly (estensione della creazione guidata)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|--|--|  
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|--|--|  
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|--|--|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|--|--|  
|[CustomDataSignature](../extensibility/customdatasignature-element-visual-studio-templates.md)|--|--|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|--|nome<br /><br /> Valore|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|--|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|--|--|  
|[Descrizione](../extensibility/description-element-visual-studio-templates.md)|--|Pacchetto<br /><br /> Id|  
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|--|--|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|--|--|  
|[Cartella](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Cartella|nome|  
||[deprecato]|--|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|--|--|  
|[Nascosto](../extensibility/hidden-element-visual-studio-templates.md)|--|--|  
|[Icona](../extensibility/icon-element-visual-studio-templates.md)|--|Pacchetto<br /><br /> Id|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|--|--|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|--|--|  
|[MaxFrameworkVersion](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|--|--|  
|[Nome](../extensibility/name-element-visual-studio-templates.md)|--|Pacchetto<br /><br /> Id|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|--|--|  
|[PreviewImage](../extensibility/previewimage-element-visual-studio-templates.md)|--|--|  
|[Progetto](../extensibility/project-element-visual-studio-templates.md)|Cartella<br /><br /> ProjectItem|File<br /><br /> TargetFileName<br /><br /> ReplaceParameters|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|--|  
|[ProjectItem (modelli di elementi)](../extensibility/projectitem-element-visual-studio-item-templates.md)|--|Sottotipo<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|  
|[ProjectItem (modelli di progetto)](../extensibility/projectitem-element-visual-studio-project-templates.md)|--|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|--|--|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|--|ProjectName|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|--|--|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|--|--|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|--|--|  
|[Reference](../extensibility/reference-element-visual-studio-templates.md)|Assembly|--|  
|[Riferimenti](../extensibility/references-element-visual-studio-templates.md)|Riferimenti|--|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|--|--|  
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|--|Versione|  
|[SDKReference](../extensibility/sdkreference-element-visual-studio-templates.md)|--|Pacchetto|  
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|--|--|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|nome|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|--|--|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|--|--|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|--|--|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|--|--|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|--|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Progetto<br /><br /> Riferimenti<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|nome<br /><br /> Descrizione<br /><br /> Icona<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Hidden<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|--|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|--|--|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|--|--|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|Tipo<br /><br /> Versione|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|--|nome|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Assembly<br /><br /> FullClassName|--|  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare starter kit](../ide/how-to-create-starter-kits.md)