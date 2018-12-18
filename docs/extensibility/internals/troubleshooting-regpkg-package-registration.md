---
title: Risoluzione dei problemi di registrazione del pacchetto RegPkg | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5651e7c00abe91ec8e4cae7b720b6534318051f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-regpkg-package-registration"></a>Risoluzione dei problemi di registrazione del pacchetto RegPkg
> [!NOTE]
>  Il modo migliore per registrare i pacchetti in Visual Studio è tramite il file. pkgdef. In questo modo per la distribuzione di un'estensione senza la necessità di accedere al Registro di sistema. File pkgdef vengono creati utilizzando il [CreatePkgDef utilità](../../extensibility/internals/createpkgdef-utility.md).  
  
 Per registrare un pacchetto utilizzando RegPkg in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è necessario utilizzare la versione di RegPkg appropriata per il pacchetto.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versioni di RegPkg correlate alle versioni di pacchetto  
 Esistono due versioni di RegPkg. Una versione è incluso in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Utilizzare questa versione per registrare i pacchetti che sono stati compilati utilizzando uno degli assembly seguenti:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 È possibile registrare pacchetti che sono stati compilati con l'assembly shell precedenti.  
  
 La versione precedente di RegPkg possibile registrare pacchetti che sono stati compilati con l'assembly della shell. Tuttavia, non è registrato per i pacchetti creati con versioni successive di tale assembly.  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)