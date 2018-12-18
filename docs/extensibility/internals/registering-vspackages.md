---
title: Registrazione di pacchetti VSPackage | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 119e6dc088c6f6e80d79ab096d97b7404c530611
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="registering-vspackages"></a>Registrazione di pacchetti VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]si basa su file. pkgdef per descrivere e individuare un pacchetto VSPackage. Un file. pkgdef contiene tutte le informazioni di registrazione che, in caso contrario, verrebbero aggiunto al Registro di sistema. VSPackage gestiti sono registrati per l'aggiunta di attributi per il codice sorgente e quindi eseguendo il [CreatePkgDef utilità](../../extensibility/internals/createpkgdef-utility.md) sull'assembly risultante per generare un file. pkgdef.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Definizione del percorso di file VSPackage nella shell di Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Descrive il percorso di caricamento per pacchetti VSPackage.  
  
 [Registrazione e annullamento della registrazione di pacchetti VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Viene illustrato come registrare un VSPackage.  
