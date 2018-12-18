---
title: L'installazione all'esterno della cartella estensioni con VSIX v3 | Documenti Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 970d823265fc25c7248b9953602f50f19c54bc95
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="installing-outside-the-extensions-folder"></a>L'installazione all'esterno della cartella delle estensioni

A partire da Visual Studio 2017 e VSIX v3 (versione 3), è ora supportata per l'installazione di risorse di estensione all'esterno nella cartella extensions. Attualmente, i percorsi seguenti siano abilitati come percorsi di installazione valido (dove [INSTALLDIR] è stato eseguito il mapping alla directory di installazione dell'istanza di Visual Studio):

* \MSBuild [INSTALLDIR]
* [INSTALLDIR] \Xml\Schemas.
* \Common7\IDE\PublicAssemblies. [INSTALLDIR]
* \Licenses [INSTALLDIR]
* \Common7\IDE\ReferenceAssemblies [INSTALLDIR]
* \Common7\IDE\RemoteDebugger [INSTALLDIR]
* \Common7\IDE\VC\VCTargets [INSTALLDIR]

>**Nota:** il formato VSIX non consente di installare di fuori della struttura di cartelle di installazione di Visual Studio.

Per supportare l'installazione di queste directory, l'estensione VSIX deve essere installato "per istanza per ogni macchina". Questo può essere abilitato selezionando la casella di controllo "all users" nella finestra di progettazione Extension. vsixmanifest:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Come impostare la directory principale di installazione

Per impostare le directory di installazione, è possibile utilizzare il **proprietà** finestra in Visual Studio. Ad esempio, è possibile impostare il `InstallRoot` proprietà di un riferimento progetto a una delle posizioni precedenti:

![installare le proprietà radice](media/install-root-properties.png)

Verranno aggiunti alcuni metadati corrispondenti `ProjectReference` proprietà all'interno di file con estensione csproj del progetto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Nota:** è possibile modificare direttamente il file con estensione csproj, se si preferisce.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Come impostare un sottopercorso sotto la directory principale di installazione

Se si desidera installare un sottopercorso sotto il `InstallRoot`, è possibile farlo impostando la `VsixSubPath` come proprietà di `InstallRoot` proprietà. Ad esempio, ad esempio si desidera visualizzare l'output del riferimento di progetto per installare ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. È possibile farlo facilmente con la finestra di progettazione di proprietà:

![set sottopercorso](media/set-subpath.png)

Le modifiche di file con estensione csproj corrispondente saranno simile al seguente:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche di progettazione alle proprietà si applicano solo ai riferimenti al progetto; è possibile impostare il `InstallRoot` metadati per gli elementi all'interno del progetto anche (usando gli stessi metodi descritti sopra).
