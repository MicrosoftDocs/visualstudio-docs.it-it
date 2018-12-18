---
title: Configurazioni standard e personalizzate del set di strumenti | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 855bd7af4372f5216abab3d6ddd45ec8f7809baa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="standard-and-custom-toolset-configurations"></a>Configurazioni standard e personalizzate del set di strumenti
Un set di strumenti di MSBuild contiene riferimenti ad attività, destinazioni e strumenti che è possibile usare per compilare un progetto di applicazione. MSBuild include un set di strumenti standard, ma è anche possibile creare set di strumenti personalizzati. Per informazioni su come specificare un set di strumenti, vedere [Set di strumenti (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  
  
## <a name="standard-toolset-configurations"></a>Configurazioni del set di strumenti standard  
 MSBuild 15.0 include i set di strumenti standard seguenti:  
  
|ToolsVersion|Percorso del set di strumenti (come specificato nella proprietà di compilazione MSBuildToolsPath o MSBuildBinPath)|  
|------------------|--------------------------------------------------------------------------------------------|  
|2.0|*Percorso di installazione di Windows*\Microsoft.NET\Framework\v2.0.50727\|  
|3.5|*Percorso di installazione di Windows*\Microsoft.NET\Framework\v3.5\|  
|4.0|*Percorso di installazione di Windows*\Microsoft.NET\Framework\v4.0.30319\|  
|15.0|*Percorso di installazione di Visual Studio*\MSBuild\15.0\bin|  
  
 Il valore `ToolsVersion` determina quale set di strumenti viene usato da un progetto generato da Visual Studio. In Visual Studio 2017 il valore predefinito è "15.0" indipendentemente dalla versione specificata nel file di progetto, ma è possibile eseguire l'override di tale attributo usando l'opzione **/toolsversion** a un prompt dei comandi. Per informazioni su questo attributo e su altri modi per specificare `ToolsVersion`, vedere [Override delle impostazioni ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 Visual Studio 2017 non usa una chiave del Registro di sistema per il percorso di MSBuild. Per le versioni di MSBuild precedenti alla 15.0 installate con Visual Studio 2017, le seguenti chiavi del Registro di sistema specificano il percorso di installazione di MSBuild.exe.  
  
|Chiave del Registro di sistema|Nome della chiave|Valore della chiave della stringa|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|Percorso di installazione di .NET Framework 2.0|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|Percorso di installazione di .NET Framework 3.5|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|Percorso di installazione di .NET Framework 4|  
  
### <a name="sub-toolsets"></a>Subset di strumenti  
 Se la chiave del Registro di sistema nella tabella precedente ha una sottochiave, MSBuild la usa per determinare il percorso di un subset di strumenti che sostituisce il percorso nel set di strumenti padre. Di seguito è riportato un esempio di sottochiave:  
  
 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  
  
 Se si definiscono proprietà sia nel set di strumenti di base, sia nel subset di strumenti selezionato, vengono usate le definizioni delle proprietà del subset di strumenti. Ad esempio, il set di strumenti di MSBuild 4.0 definisce `SDK40ToolsPath` in modo che punti all'SDK 7.0A, ma il set di strumenti di MSBuild 4.0\11.0 definisce la stessa proprietà in modo che punti all'SDK 8.0A. Se si annulla `VisualStudioVersion`, `SDK40ToolsPath` punterà a 7.0A, ma se `VisualStudioVersion` è impostato su 11.0, la proprietà punterà invece a 8.0A.  
  
 La proprietà di compilazione `VisualStudioVersion` indica se un subset di strumenti diventa attivo. Ad esempio, il valore "12.0" di `VisualStudioVersion` specifica il subset di strumenti di MSBuild 12.0. Per altre informazioni, vedere la sezione relativa ai subset di strumenti in [Set di strumenti di MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
> [!NOTE]
>  Si consiglia di evitare di modificare queste impostazioni. Tuttavia, è possibile aggiungere le proprie impostazioni e specificare definizioni personalizzate del set di strumenti a livello di computer, come descritto nella sezione successiva.  
  
## <a name="custom-toolset-definitions"></a>Definizioni personalizzate del set di strumenti  
 Se un set di strumenti standard non soddisfa i requisiti di compilazione, è possibile creare un set di strumenti personalizzato. Ad esempio, in uno scenario di laboratorio di compilazione può essere necessario usare un sistema separato per compilare i progetti [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Usando un set di strumenti personalizzato, è possibile assegnare valori personalizzati all'attributo `ToolsVersion` quando si creano progetti o si esegue MSBuild.exe. In questo modo si può anche usare la proprietà `$(MSBuildToolsPath)` per importare i file TARGETS da quella directory, nonché definire le proprietà del set di strumenti personalizzato che possono essere usate per qualsiasi progetto che usa tale set di strumenti.  
  
 Specificare un set di strumenti personalizzato nel file di configurazione per MSBuild.exe o per lo strumento personalizzato che ospita il motore MSBuild, se in uso. Ad esempio, il file di configurazione per MSBuild.exe può includere la seguente definizione di set di strumenti se si vuole eseguire l'override del comportamento predefinito di ToolsVersion 15.0.  
  
```xml  
<msbuildToolsets default="15.0">  
   <toolset toolsVersion="15.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 È necessario definire `<msbuildToolsets>` anche nel file di configurazione, come indicato di seguito.  
  
```xml  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=15.1.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Per consentire una lettura corretta, `<configSections>` deve essere la prima sottosezione della sezione `<configuration>`.  
  
 `ToolsetConfigurationSection` è una sezione di configurazione personalizzata che può essere usata da qualsiasi host MSBuild per la configurazione personalizzata. Se si usa un set di strumenti personalizzato, non sono necessarie operazioni dell'host per inizializzare il motore di compilazione, tranne la definizione delle voci del file di configurazione. Definendo le voci del Registro di sistema, è possibile specificare i set di strumenti a livello di computer validi per MSBuild.exe, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e tutti gli host di MSBuild.  
  
> [!NOTE]
>  Se un file di configurazione definisce le impostazioni per un elemento `ToolsVersion` già definito nel Registro di sistema, le due definizioni non vengono unite. La definizione nel file di configurazione ha la precedenza e le impostazioni del Registro di sistema per tale `ToolsVersion` vengono ignorate.  
  
 Le seguenti proprietà sono specifiche per il valore di `ToolsVersion` usato nei progetti:  
  
-   **$(MSBuildBinPath)** è impostato sul valore `ToolsPath` specificato nel Registro di sistema o nel file di configurazione in cui è definito `ToolsVersion`. L'impostazione `$(MSBuildToolsPath)` nel Registro di sistema o nel file di configurazione specifica la posizione delle attività e delle destinazioni principali. Nel file di progetto viene eseguito il mapping alla proprietà $(MSBuildBinPath) e anche alla proprietà $(MSBuildToolsPath).  
  
-   `$(MSBuildToolsPath)` è una proprietà riservata definita dalla proprietà MSBuildToolsPath specificata nel file di configurazione. Questa proprietà sostituisce `$(MSBuildBinPath)`. Tuttavia, `$(MSBuildBinPath)` viene mantenuta per garantire la compatibilità. Un set di strumenti personalizzato deve definire `$(MSBuildToolsPath)` o `$(MSBuildBinPath)` ma non entrambe, a meno che non abbiano lo stesso valore.  
  
 Si possono anche aggiungere al file di configurazione proprietà personalizzate specifiche di ToolsVersion, usando la stessa sintassi usata per aggiungere la proprietà MSBuildToolsPath. Per rendere disponibili per il file di progetto queste proprietà personalizzate, usare lo stesso nome del valore specificato nel file di configurazione. È possibile definire i set di strumenti ma non i subset di strumenti nel file di configurazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Set di strumenti (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)