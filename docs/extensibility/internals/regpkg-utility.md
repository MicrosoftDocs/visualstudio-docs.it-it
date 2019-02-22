---
title: Utilità RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b9b07bc801e687da9ce93968dbac59966328484
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619238"
---
# <a name="regpkg-utility"></a>Utilità RegPkg
> [!NOTE]
>  Il modo migliore per registrare i pacchetti in Visual Studio consiste nell'usare i file con estensione pkgdef. In questo modo per la distribuzione di un'estensione senza la necessità di accedere al Registro di sistema, che è un requisito per la distribuzione di VSIX. I file pkgdef vengono creati tramite il [utilità CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Per ulteriori informazioni sulla distribuzione del pacchetto Visual Studio, vedere [spedizione di estensioni di Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 L'utilità RegPkg.exe registra un pacchetto VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e lo prepara per la distribuzione. Questa utilità viene usata in background durante lo sviluppo di VSPackage. Viene eseguito come parte del processo di compilazione in modo che è possibile compilare ed eseguire un pacchetto VSPackage nell'hive sperimentale.

 RegPkg può generare gli script del Registro di sistema in diversi formati. È possibile incorporare questi script nei progetti di distribuzione come file con estensione msi progetti o file di set di strumenti di Windows Installer XML.

 RegPkg.exe trova in genere \< *percorso di installazione di Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue questa sintassi:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 registrazione esegue /root:root sotto l'oggetto specificato

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] radice.

 /regfile:filename crea un file con estensione reg anziché l'aggiornamento del Registro di sistema.  Non è utilizzabile con /vrgfile o /rgsfile o /wixfile.

 /rgsfile:filename crea un file con estensione RGS anziché l'aggiornamento del Registro di sistema.  Non è utilizzabile con /vrgfile o /regfile o /wixfile.

 /vrgfile:filename crea un file .vrg anziché l'aggiornamento del Registro di sistema.  Non è utilizzabile con /regfile o /rgsfile o /wixfile.

 /rgm crea un file .rgm oltre che il file rgs.  Deve essere combinato con /rgsfile.

 /wixfile:filename crea un file compatibile con set di strumenti Windows Installer XML anziché l'aggiornamento del Registro di sistema.  Non è utilizzabile con /regfile o /rgsfile o /vrgfile.

 / codebase registrazione forza con CodeBase anziché come Assembly.

 registrazione di forze /assembly con Assembly anziché CodeBase.

 / annullare la registrazione unregister questo pacchetto.  Non è possibile usare

 con /regfile o /vrgfile /rgsfile o /wixfile.

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)
- [Risoluzione dei problemi di registrazione dei pacchetti RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)