---
title: Scegliere la Directory di installazione per un pacchetto VSPackage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 564a184e8b3907f5a61bccc26cfbafa8d2cf8e67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Scegliere la Directory di installazione per un pacchetto VSPackage
Nel file system di un utente devono essere un VSPackage e i relativi file di supporto. Il percorso varia a seconda se il pacchetto VSPackage gestito o non gestiti, a regime di controllo delle versioni side-by-side la scelta dell'utente.  
  
## <a name="unmanaged-vspackages"></a>Pacchetti VSPackage non gestiti  
 Un VSPackage non gestito è un server COM che può essere installato in qualsiasi posizione. Le informazioni di registrazione deve riflette accuratamente la posizione. Interfaccia utente (UI) programma di installazione deve fornire un percorso predefinito come sottodirectory della proprietà ProgramFilesFolder Windows Installer. Ad esempio:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 L'utente deve essere autorizzato a modificare la directory predefinita per le esigenze degli utenti che dispongono di una partizione di avvio di piccole dimensioni e si desidera installare strumenti e applicazioni in un altro volume.  
  
 Se lo schema side-by-side utilizza un VSPackage con controllo delle versioni, è possibile utilizzare le sottodirectory per archiviare le diverse versioni. Ad esempio:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackage gestiti  
 VSPackage gestiti possono anche essere installati in qualsiasi posizione. Tuttavia, è consigliabile installarli sempre la global assembly cache (GAC) per ridurre i tempi di caricamento di assembly. Poiché un VSPackage gestito sono sempre assembly con nome sicuro, installarli nella Global Assembly Cache indica che la verifica delle firme con nome sicuro che utilizza solo al momento dell'installazione. Gli assembly con nome sicuro installati in un' posizione nel file system devono avere le firme verificare ogni volta che vengono caricati. Quando si installano pacchetti VSPackage gestiti nella Global Assembly Cache, utilizzare lo strumento regpkg **/assembly** commutatore per scrivere voci del Registro di sistema che punta al nome sicuro dell'assembly.  
  
 Se si installano pacchetti VSPackage gestiti in un percorso diverso dalla Global Assembly Cache, seguire i consigli precedenti specificato per i pacchetti VSPackage non gestiti per la scelta delle gerarchie di directory. Utilizzare lo strumento regpkg **/codebase** commutatore per scrivere voci del Registro di sistema che punta al percorso dell'assembly VSPackage.  
  
 Per ulteriori informazioni, vedere [registrazione e annullamento della registrazione VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>DLL satellite  
 Per convenzione, VSPackage DLL satellite, che contengono le risorse per una determinata lingua, ovvero si trovano nella sottodirectory della directory VSPackage. Le sottodirectory corrispondano ai valori di ID (LCID) delle impostazioni locali.  
  
 [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md) indica che le voci del Registro di sistema consentono di controllare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] effettivamente Cerca un VSPackage satellite DLL. Tuttavia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di caricare una DLL satellite in una sottodirectory denominata per un valore LCID, nell'ordine seguente:  
  
1.  LCID (VS LCID, ad esempio \1033 per inglese) predefinito  
  
2.  Identificatore LCID predefinito con la varietà di lingua predefinita.  
  
3.  Identificatore LCID predefinito di sistema.  
  
4.  Sistema LCID predefinito con la varietà di lingua predefinita.  
  
5.  STATI UNITI Inglese (. \1033 o. \0x409).  
  
 Se la DLL VSPackage include risorse e i punti di ingresso del Registro di sistema SatelliteDll\DllName, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta di caricarli nell'ordine sopra indicato.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta tra package VS condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)   
 [Registrazione del pacchetto gestito](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)