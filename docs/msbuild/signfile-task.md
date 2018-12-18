---
title: Attività SignFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55a569a973f874636f1b620f6983c077f177f1ac
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="signfile-task"></a>Attività SignFile
Consente di firmare il file specificato usando il certificato specificato.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `SignFile`.  
  
 Notare che i certificati SHA-256 sono consentiti solo in computer con .NET 4.5 e versioni successive.  
  
> [!WARNING]
>  A partire da Visual Studio 2013 Update 3, questa attività ha una nuova firma che consente di specificare la versione del framework di destinazione per il file. L'utente è incoraggiato a usare la nuova firma, ove possibile, perché il processo di MSBuild usa gli hash SHA-256 solo quando il framework di destinazione è .NET 4.5 o versione successiva. Se il framework di destinazione è .NET 4.0 o versione precedente, l'hash SHA-256 non verrà usato.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`CertificateThumbprint`|Parametro `String` obbligatorio.<br /><br /> Specifica il certificato da usare per la firma. Questo certificato deve trovarsi nell'archivio personale dell'utente corrente.|  
|`SigningTarget`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica i file da firmare con il certificato.|  
|`TimestampUrl`|Parametro `String` facoltativo.<br /><br /> Specifica l'URL del server di timestamp.|  
|`TargetFrameworkVersion`|La versione di.NET Framework che viene usata per la destinazione.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri sopra elencati, quest'attività eredita i parametri dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [Classe di base Task](../msbuild/task-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usata l'attività `SignFile` per firmare i file specificati nella raccolta di elementi `FilesToSign` con il certificato specificato dalla proprietà `Certificate`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.exe" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.5" />  
    </Target>  
</Project>  
```  
  
> [!NOTE]
>  L'identificazione personale del certificato è l'hash SHA-1 del certificato. Per altre informazioni, vedere [Ottenere l'hash SHA-1 di un certificato CA radice attendibile](http://msdn.microsoft.com/en-us/dd641990-9a88-4228-a245-017797131a87).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usata l'attività `Exec` per firmare i file specificati nella raccolta di elementi `FilesToSign` con il certificato specificato dalla proprietà `Certificate`. È possibile usarlo per firmare i file di Windows Installer durante il processo di compilazione.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.msi" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <Exec Command="signtool.exe sign /f CertFile /p Password "@(FileToSign)" "/>  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.0" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)