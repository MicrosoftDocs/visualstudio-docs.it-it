---
title: Elemento Import (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4c7df0cf9e837e27e8f572bb50d5e3395b3424a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629911"
---
# <a name="import-element-msbuild"></a>Elemento Import (MSBuild)
Importa il contenuto di un file di progetto in un altro file di progetto.

\<Project> \<Import>

## <a name="syntax"></a>Sintassi

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Description|
|---------------|-----------------|
|`Project`|Attributo obbligatorio.<br /><br /> Percorso del file di progetto da importare. Il percorso può includere caratteri jolly. I file corrispondenti vengono importati in base all'ordine. Usando questa funzionalità, è possibile aggiungere codice a un progetto aggiungendo il file di codice a una directory.|
|`Condition`|Attributo facoltativo.<br /><br /> Una condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementi figlio
 nessuno

### <a name="parent-elements"></a>Elementi padre

| Elemento | Description |
| - | - |
| [Progetto](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |
| [ImportGroup](../msbuild/importgroup-element.md) | Contiene una raccolta di elementi `Import` raggruppati in una condizione facoltativa. |

## <a name="remarks"></a>Osservazioni
 Tramite l'elemento `Import` , è possibile riutilizzare codice comune a più file di progetto. Ciò semplifica la gestione del codice, poiché tutti gli aggiornamenti apportati al codice condiviso vengono propagati a tutti i progetti che lo importano.

 Per convenzione i file di progetto condivisi importati vengono salvati come file con estensione *targets* ma sono file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] standard. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] non impedisce di importare un progetto con una diversa estensione del nome del file, ma è consigliabile usare l'estensione *targets* per coerenza.

 I percorsi relativi dei progetti importati vengono interpretati rispetto alla directory del progetto in cui sono importati. Pertanto, se uno stesso file di progetto viene importato in vari file di progetto che si trovano in posizioni diverse, i percorsi relativi nel file di progetto importato vengano interpretati in modo diverso per ogni progetto importato.

 A tutte le proprietà riservate di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] relative al file di progetto, ad esempio `MSBuildProjectDirectory` e `MSBuildProjectFile`, cui viene fatto riferimento in un progetto importato vengono assegnati valori basati sul file di progetto di destinazione.

 Se il progetto importato non ha un attributo `DefaultTargets` , i progetti importati vengono esaminati nell'ordine in cui sono importati e viene usato il valore del primo attributo `DefaultTargets` individuato. Ad esempio, se ProjectA importa ProjectB e ProjectC (in questo ordine), e ProjectB importa ProjectD, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] cerca il valore `DefaultTargets` specificato prima in ProjectA, poi in ProjectB, quindi in ProjectD e infine in ProjectC.

 Lo schema di un progetto importato è identico a quello di un progetto standard. Sebbene [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] potrebbe essere in grado di creare un progetto importato, ciò è improbabile perché in genere un progetto importato contiene informazioni sulle proprietà da impostare o sull'ordine in cui eseguire le destinazioni. Il progetto importato dipende dal progetto in cui viene importato per fornire tali informazioni.


## <a name="wildcards"></a>Caratteri jolly
 In .NET Framework 4, MSBuild consente l'uso di caratteri jolly nell'attributo Project. Quando sono presenti caratteri jolly, tutte le corrispondenze trovate vengono ordinate (per riproducibilità) e quindi vengono importate nell'ordine specificato come se l'ordine fosse stato impostato in modo esplicito.

 Ciò è utile se si desidera offrire un punto di estensibilità in modo che un altro utente possa importare un file senza che sia necessario aggiungere esplicitamente il nome del file al file di importazione. A questo scopo, *Microsoft.Common.Targets* contiene la riga seguente all'inizio del file.

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
- [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
- [Procedura: Usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
