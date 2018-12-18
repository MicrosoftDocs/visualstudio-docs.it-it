---
title: Utilità RegPkg | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d677aaf155e533c27a775f3995b53dd59b65385
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="regpkg-utility"></a>Utilità RegPkg
> [!NOTE]
>  Il modo migliore per registrare i pacchetti in Visual Studio è tramite il file. pkgdef. In questo modo per la distribuzione di un'estensione senza la necessità di accedere al Registro di sistema, che è un requisito per la distribuzione VSIX. File pkgdef vengono creati utilizzando il [CreatePkgDef utilità](../../extensibility/internals/createpkgdef-utility.md). Per ulteriori informazioni sulla distribuzione del pacchetto di Visual Studio, vedere [Shipping estensioni di Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Eseguire l'utility RegPkg.exe registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e lo prepara per la distribuzione. Questa utilità è utilizzata in background durante lo sviluppo di VSPackage. Viene eseguito come parte del processo di compilazione in modo che è possibile compilare ed eseguire un pacchetto VSPackage nell'hive sperimentale.  
  
 RegPkg può generare gli script del Registro di sistema di sistema in diversi formati. È possibile incorporare questi script nei progetti di distribuzione come file con estensione msi progetti o file di set di strumenti di Windows Installer XML.  
  
 RegPkg.exe si trova in genere in \< *il percorso di installazione di Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue questa sintassi:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Esegue la registrazione con il nome specificato  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] radice.  
  
 /regfile:filename  
 Crea un file con estensione reg, anziché aggiornare il Registro di sistema.  Non può essere utilizzato con /vrgfile o /rgsfile o /wixfile.  
  
 /rgsfile:filename  
 Crea un file con estensione RGS anziché l'aggiornamento del Registro di sistema.  Non può essere utilizzato con /vrgfile o /regfile o /wixfile.  
  
 /vrgfile:filename  
 Crea un file vrg anziché l'aggiornamento del Registro di sistema.  Non può essere utilizzato con /regfile o /rgsfile o /wixfile.  
  
 /rgm  
 Crea un file .rgm oltre al file rgs.  Deve essere combinato con /rgsfile.  
  
 /wixfile:filename  
 Crea un file di set di strumenti compatibili con Windows Installer XML anziché l'aggiornamento del Registro di sistema.  Non può essere utilizzato con /regfile o /rgsfile o /vrgfile.  
  
 /codebase  
 Registrazione forza con CodeBase anziché come Assembly.  
  
 /assembly  
 Registrazione forza con Assembly anziché CodeBase.  
  
 / annullare la registrazione  
 Annulla la registrazione di questo pacchetto.  Non può essere utilizzato  
  
 con /regfile o /vrgfile o /rgsfile o /wixfile.  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)  
 [Risoluzione dei problemi di registrazione dei pacchetti RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)