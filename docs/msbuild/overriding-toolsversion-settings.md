---
title: Override delle impostazioni ToolsVersion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f1efc774b4eb0c98ef6c5de36864dfc092133b52
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="overriding-toolsversion-settings"></a>Override delle impostazioni ToolsVersion
È possibile modificare il set di strumenti per progetti e soluzioni nei tre modi seguenti:  
  
1.  Usando l'opzione `/ToolsVersion` (o `/tv`, in breve) quando si compila il progetto o la soluzione dalla riga di comando  
  
2.  Impostando il parametro `ToolsVersion` sull'attività MSBuild  
  
3.  Impostando la proprietà `$(ProjectToolsVersion)` in un progetto all'interno di una soluzione Questo consente di compilare un progetto in una soluzione con una versione del set di strumenti diversa da quella degli altri progetti.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Eseguire l'override delle impostazioni di ToolsVersion di progetti e soluzioni nelle compilazioni da riga di comando  
 Anche se i progetti Visual Studio vengono in genere compilati con la versione di ToolsVersion specificata nel file di progetto, è possibile usare l'opzione `/ToolsVersion` (o `/tv`) della riga di comando per eseguire l'override del valore e compilare tutti i progetti e le dipendenze tra progetti con un set di strumenti diverso. Ad esempio:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 Nell'esempio seguente tutti i progetti vengono compilati usando ToolsVersion 12.0. Vedere la sezione "Ordine di precedenza" più avanti in questo argomento.  
  
 Quando si usa l'opzione `/tv` della riga di comando, è possibile usare facoltativamente la proprietà `$(ProjectToolsVersion)` nei progetti singoli per compilarli con un valore ToolsVersion diverso dagli altri progetti della soluzione.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Eseguire l'override delle impostazioni ToolsVersion usando il parametro ToolsVersion dell'attività MSBuild  
 L'attività MSBuild è il mezzo principale per consentire a un progetto di compilarne un altro. Per consentire all'attività MSBuild di compilare un progetto con un ToolsVersion diverso da quello specificato nel progetto, è disponibile un parametro dell'attività facoltativo denominato `ToolsVersion`. L'esempio seguente illustra come usare tale parametro:  
  
1.  Creare un file denominato `projectA.proj` e contenente il codice seguente:  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2.  Creare un altro file denominato `projectB.proj` e contenente il codice seguente:  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3.  Immettere il comando seguente in un prompt dei comandi:  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4.  Viene visualizzato l'output seguente. Per `projectA`, l'impostazione `/toolsversion:3.5` nella riga di comando esegue l'override dell'impostazione `ToolsVersion=12.0` nel tag `Project`.  
  
     `ProjectB` viene chiamato da un'attività in `projectA`. L'attività presenta `ToolsVersion=2.0`, che esegue l'override delle altre impostazioni di `ToolsVersion` per `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>Ordine di precedenza  
 L'ordine di precedenza, dal più alto al più basso, usato per determinare `ToolsVersion` è il seguente:  
  
1.  Attributo `ToolsVersion` sull'attività MSBuild usato per compilare il progetto, se disponibile.  
  
2.  Opzione `/toolsversion` (o `/tv`) usata nel comando msbuild.exe, se disponibile.  
  
3.  Se la variabile di ambiente `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` è impostata, usare il valore `ToolsVersion` corrente.  
  
4.  Se la variabile di ambiente `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` è impostata e il valore `ToolsVersion` definito nel file di progetto è maggiore del valore `ToolsVersion` corrente, usare il valore `ToolsVersion` corrente.  
  
5.  Se la variabile di ambiente `MSBUILDLEGACYDEFAULTTOOLSVERSION` non è impostata o se `ToolsVersion` non è impostato, vengono usati i passaggi seguenti:  
  
    1.  Attributo `ToolsVersion` dell'elemento [Project](../msbuild/project-element-msbuild.md) del file di progetto. Se questo attributo non esiste, si presuppone che si tratti della versione corrente.  
  
    2.  Versione predefinita degli strumenti del file MSBuild.exe.config.  
  
    3.  Versione predefinita degli strumenti nel Registro di sistema. Per altre informazioni, vedere [Configurazioni standard e personalizzate del set di strumenti](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Se la variabile di ambiente `MSBUILDLEGACYDEFAULTTOOLSVERSION` non è impostata, vengono usati i passaggi seguenti:  
  
    1.  Se la variabile di ambiente `MSBUILDDEFAULTTOOLSVERSION` è impostata su un valore `ToolsVersion` esistente, usare tale valore.  
  
    2.  Se `DefaultOverrideToolsVersion` è impostata in MSBuild.exe.config, usarla.  
  
    3.  Se `DefaultOverrideToolsVersion` è impostata nel Registro di sistema, usarla.  
  
    4.  In caso contrario, usare il valore `ToolsVersion` corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  (Set di strumenti (ToolsVersion))  
 [Configurazioni standard e personalizzate del set di strumenti](../msbuild/standard-and-custom-toolset-configurations.md)