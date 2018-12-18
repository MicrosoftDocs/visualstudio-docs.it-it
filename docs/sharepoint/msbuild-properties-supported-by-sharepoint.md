---
title: "Proprietà MSBuild supportate in SharePoint | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 115896965eb47eb6dc4a9cdbb0b9df8dd8972c5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Proprietà MSBuild supportate in SharePoint
  Qualsiasi [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] definito nel file di progetto utente, i file di progetto o di file targets può essere utilizzata [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetti SharePoint. Oltre alle comuni [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] proprietà fornite dal progetto di SharePoint definisce le proprietà aggiuntive specifiche per i progetti SharePoint.  
  
 Per un elenco di comune [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] proprietà, vedere [proprietà di progetto MSBuild comuni](http://go.microsoft.com/fwlink/?LinkID=168687). Per un elenco completo delle proprietà supportati dal linguaggio di programmazione, consultare il file con estensione targets, il file di progetto (con estensione csproj o vbproj) o il file di progetto utente (csproj o. vbproj).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>Proprietà MSBuild specifiche di SharePoint  
 La tabella seguente elenca [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] proprietà che si applicano in modo specifico per i progetti SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Esistono altre proprietà, ma sono per uso interno.  
  
|Nome proprietà|Descrizione|  
|-------------------|-----------------|  
|SharePointSiteUrl|Stringa che rappresenta il [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] al sito di SharePoint.|  
|SandboxedSolution|Valore booleano che indica se la soluzione è una soluzione creata mediante sandbox.|  
|ActiveDeploymentConfiguration|Configurazione di distribuzione attiva.|  
|IncludeAssemblyInPackage|Valore booleano che indica se l'assembly è incluso nel file del pacchetto.|  
|PreDeploymentCommand|Valore stringa che rappresenta il comando da eseguire durante il passaggio di un comando di pre-distribuzione.|  
|PostDeploymentCommand|Valore stringa che rappresenta il comando da eseguire durante il passaggio di un comando di post-distribuzione.|  
|CustomBeforeSharePointTargets|Stringa che rappresenta il percorso di un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] file di destinazioni. Se il file di destinazioni, esiste ed è definito, viene importato prima che i dati di destinazioni di SharePoint. Questa proprietà consente di personalizzare il processo del pacchetto dalle proprietà correlate alla creazione di pacchetti predefinendo senza modificare il file targets incluso in SharePoint, ma il file di destinazioni è ancora valida per tutti i progetti SharePoint.|  
|CustomAfterSharePointTargets|Stringa che rappresenta il percorso di un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] file di destinazioni. Se il file di destinazioni, esiste ed è definito, è importata dopo tutte le destinazioni dati di SharePoint. Questa proprietà consente di personalizzare il processo del pacchetto eseguendo l'override di proprietà correlate alla creazione di pacchetti e le destinazioni senza dover modificare il file targets incluso in SharePoint, ma il file di destinazioni è ancora valida per tutti i progetti SharePoint.|  
|LayoutPath|Stringa che rappresenta la directory radice in cui ognuno dei file da includere nel pacchetto vengono temporaneamente inseriti prima di essere aggiunti al file con estensione wsp. Questo percorso può essere utile conoscere quando si esegue l'override di destinazioni di BeforeLayout e AfterLayout per aggiungere, rimuovere o modificare i file da includere nel pacchetto, quanto è possibile utilizzarlo per modificare il contenuto del file con estensione wsp.|  
|BasePackagePath|Stringa che rappresenta la cartella in cui è stato inserito il pacchetto. Questo valore viene utilizzata la directory di output del progetto, ad esempio Bin\Debug.|  
|PackageExtension|Stringa che rappresenta l'estensione del nome file da aggiungere al pacchetto. Il valore predefinito è wsp.|  
|AssemblyDeploymentTarget|Stringa che rappresenta la posizione in cui l'assembly del progetto viene distribuito nel server SharePoint. Il valore è GlobalAssemblyCache (impostazione predefinita) o WebApplication. Questa proprietà può anche essere impostata nella finestra Proprietà.|  
|PackageWithValidation|Valore booleano che specifica se la convalida viene eseguita prima della creazione del pacchetto. Questa proprietà consente di ignorare gli errori di convalida durante la compilazione di pacchetti.|  
|ValidatePackageDependsOn|Stringa che definisce le destinazioni aggiuntive da eseguire prima della destinazione ValidatePackage.|  
|TokenReplacementFileExensions|Stringa che definisce i file che hanno i relativi token sostituiti durante la creazione di pacchetti.|  
  
## <a name="using-msbuild-properties-in-the-properties-page"></a>Utilizzando le proprietà di MSBuild nella pagina delle proprietà  
 Per maggiore flessibilità, anziché utilizzare stringhe hardcoded nel **riga di comando pre-distribuzione** e **riga di comando post-distribuzione** caselle nella pagina proprietà di SharePoint, è possibile utilizzare SharePoint proprietà come argomenti. Ad esempio, anziché specificare una determinata [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] stringa per il sito di SharePoint, è possibile utilizzare invece `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  È possibile utilizzare il [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] sintassi delle variabili `$(` *propertyName* `)` o la sintassi di variabili di ambiente `%` *propertyName* `%` Per specificare una proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti a MSBuild](/visualstudio/msbuild/msbuild-reference)  
  
  