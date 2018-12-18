---
title: Elemento Import (MSBuild) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d13f376068d7f5f32a55768dbd02520152f0a30
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="import-element-msbuild"></a>Elemento Import (MSBuild)
Importa il contenuto di un file di progetto in un altro file di progetto.  

 \<Project>  
 \<Import>  

## <a name="syntax"></a>Sintassi  

```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  

### <a name="attributes"></a>Attributi  

|Attributo|Descrizione|  
|---------------|-----------------|  
|`Project`|Attributo obbligatorio.<br /><br /> Percorso del file di progetto da importare. Il percorso può includere caratteri jolly. I file corrispondenti vengono importati in base all'ordine. Usando questa funzionalità, è possibile aggiungere codice a un progetto aggiungendo il file di codice a una directory.|  
|`Condition`|Attributo facoltativo.<br /><br /> Una condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementi figlio  
 nessuno  

### <a name="parent-elements"></a>Elementi padre  

|Elemento|Descrizione|  
|-------------|-----------------|  
|[Progetto](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  
|[ImportGroup](../msbuild/importgroup-element.md)|Contiene una raccolta di elementi `Import` raggruppati in una condizione facoltativa.|  

## <a name="remarks"></a>Note  
 Tramite l'elemento `Import` , è possibile riutilizzare codice comune a più file di progetto. Ciò semplifica la gestione del codice, poiché tutti gli aggiornamenti apportati al codice condiviso vengono propagati a tutti i progetti che lo importano.  

 Per convenzione i file di progetto condivisi importati vengono salvati come file con estensione .targets ma sono file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] standard. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] non impedisce di importare un progetto con una diversa estensione del nome del file, ma è consigliabile usare l'estensione .targets per coerenza.  

 I percorsi relativi dei progetti importati vengono interpretati rispetto alla directory del progetto in cui sono importati. Pertanto, se uno stesso file di progetto viene importato in vari file di progetto che si trovano in posizioni diverse, i percorsi relativi nel file di progetto importato vengano interpretati in modo diverso per ogni progetto importato.  

 A tutte le proprietà riservate di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] relative al file di progetto, ad esempio `MSBuildProjectDirectory` e `MSBuildProjectFile`, cui viene fatto riferimento in un progetto importato vengono assegnati valori basati sul file di progetto di destinazione.  

 Se il progetto importato non ha un attributo `DefaultTargets` , i progetti importati vengono esaminati nell'ordine in cui sono importati e viene usato il valore del primo attributo `DefaultTargets` individuato. Ad esempio, se ProjectA importa ProjectB e ProjectC (in questo ordine), e ProjectB importa ProjectD, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] cerca il valore `DefaultTargets` specificato prima in ProjectA, poi in ProjectB, quindi in ProjectD e infine in ProjectC.  

 Lo schema di un progetto importato è identico a quello di un progetto standard. Sebbene [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] potrebbe essere in grado di creare un progetto importato, ciò è improbabile perché in genere un progetto importato contiene informazioni sulle proprietà da impostare o sull'ordine in cui eseguire le destinazioni. Il progetto importato dipende dal progetto in cui viene importato per fornire tali informazioni.  

> [!NOTE]
>  Mentre le istruzioni di importazione condizionale funzionano in MSBuilds per la riga di comando, non funzionano in MSBuild nell'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Le importazioni condizionali vengono valutate usando i valori di configurazione e piattaforma impostati quando viene caricato il progetto. Se vengono apportate modifiche successive che richiedono una rivalutazione delle istruzioni condizionali nel file di progetto, ad esempio la modifica della piattaforma, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rivaluta le condizioni sulle proprietà e gli elementi ma non sulle importazioni. Poiché non viene rivalutata la condizione di importazione, l'importazione viene ignorata.  
>   
>  Per risolvere il problema, inserire le importazioni condizionali nei file .targets o inserire il codice in un blocco condizionale, ad esempio un blocco [Choose Element (MSBuild)](../msbuild/choose-element-msbuild.md) .  

## <a name="wildcards"></a>Caratteri jolly  
 In .NET Framework 4, MSBuild consente l'uso di caratteri jolly nell'attributo Project. Quando sono presenti caratteri jolly, tutte le corrispondenze trovate vengono ordinate (per riproducibilità) e quindi vengono importate nell'ordine specificato come se l'ordine fosse stato impostato in modo esplicito.  

 Ciò è utile se si desidera offrire un punto di estensibilità in modo che un altro utente possa importare un file senza che sia necessario aggiungere esplicitamente il nome del file al file di importazione. A questo scopo, Microsoft.Common.Targets contiene la riga seguente all'inizio del file.  

```xml  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  

## <a name="example"></a>Esempio  
 L'esempio seguente illustra un progetto con diversi elementi e proprietà che importa un file di progetto generale.  

```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  

        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  

    <ItemGroup>  
        <CSFile Include="*.cs" />  

        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  

    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  

## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Procedura: Usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
