---
title: Ottimizzazione di Menu e comandi della barra degli strumenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f95675f420284b9d67a6d36ac30b3e71f085e565
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Ottimizzazione di Menu e comandi della barra degli strumenti
L'aggiunta di pacchetti VSPackage e i comandi corrispondenti a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] potrebbe causare una talmente dell'interfaccia utente. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce metodi per ridurre al minimo la confusione comando dell'interfaccia utente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Miglioramento della disponibilità dei comandi](../../extensibility/internals/making-commands-available.md)  
 Fornisce linee guida generali per ridurre al minimo affollare del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente quando si aggiungono pacchetti VSPackage.  
  
 [Linee guida per la selezione host](../../extensibility/internals/command-placement-guidelines.md)  
 Fornisce linee guida specifiche per l'implementazione di un VSPackage in base alle dimensioni del set di comandi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.