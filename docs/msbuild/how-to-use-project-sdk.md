---
title: 'Procedura: Fare riferimento a un SDK di progetto MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b595f08883023d1150612415fcdb6c50411db7e3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-use-msbuild-project-sdks"></a>Procedura: Usare SDK di progetto MSBuild
In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15.0 è stato introdotto il concetto di "SDK di progetto" che semplifica l'uso di Software Development Kit che richiedono l'importazione di proprietà e destinazioni.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```  
  
Durante la valutazione del progetto, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aggiunge importazioni implicite nella parte superiore e inferiore del progetto:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>  
```  

## <a name="referencing-a-project-sdk"></a>Riferimento a un SDK di progetto
 Esistono tre modi per fare riferimento a un SDK di progetto

1. Usare l'attributo `Sdk` per l'elemento `<Project/>`:
    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```
    Un'importazione implicita viene aggiunta nella parte superiore e inferiore del progetto, come illustrato in precedenza.  Il formato dell'attributo `Sdk` è `Name[/Version]` dove Version è facoltativo.  Ad esempio, è possibile specificare `My.Custom.Sdk/1.2.3`.

2. Usare l'elemento di primo livello `<Sdk/>`:
    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```
   Un'importazione implicita viene aggiunta nella parte superiore e inferiore del progetto, come illustrato in precedenza.  L'attributo `Version` non è obbligatorio.

3. Usare l'elemento `<Import/>` in un punto qualsiasi nel progetto:
    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```
   L'inclusione esplicita delle importazioni nel progetto consente il controllo completo sull'ordine.

   Quando si usa l'elemento `<Import/>` è possibile specificare anche un attributo `Version` facoltativo.  Ad esempio, è possibile specificare `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Come vengono risolti gli SDK di progetto
Durante la valutazione dell'importazione, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] risolve in modo dinamico il percorso dell'SDK di progetto in base al nome e alla versione specificati.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] include ANCHE un elenco di resolver di SDK registrati, ovvero plug-in che individuano gli SDK di progetto nel computer in uso.  Questi plug-in includono:

1. Un resolver basato su NuGet che recupera i feed di pacchetto configurati per i pacchetti NuGet corrispondenti all'ID e alla versione dell'SDK specificati.<br/>
   Questo resolver è attivo solo se è stata specificata una versione facoltativa e può essere usato per qualsiasi SDK di progetto personalizzato.  
2. Un resolver per l'interfaccia della riga di comando di .NET che risolve gli SDK installati con l'interfaccia della riga di comando di .NET.<br/>
   Questo resolver individua gli SDK di progetto, ad esempio `Microsoft.NET.Sdk` e `Microsoft.NET.Sdk.Web` che fanno parte del prodotto.
3. Un resolver predefinito che risolve gli SDK che sono stati installati con MSBuild.

Il resolver di SDK basato su NuGet supporta la specifica di una versione nel file [global.json](https://docs.microsoft.com/en-us/dotnet/core/tools/global-json) che consente di controllare la versione dell'SDK di progetto in un'unica posizione, anziché in ogni singolo progetto:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```
Durante una compilazione, è possibile usare una sola versione di ogni SDK di progetto.  Se si fa riferimento a due versioni diverse dello stesso SDK di progetto, MSBuild genererà un avviso.  È consigliabile **non** specificare una versione nei progetti se viene specificata una versione nel file `global.json`.  

## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Personalizzare la compilazione](../msbuild/customize-your-build.md)   
