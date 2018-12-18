---
title: Ottimizzazione di Menu e comandi della barra degli strumenti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 92072668f96a69a0dc5ff78839b54fa7ecc656bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Ottimizzazione di Menu e comandi della barra degli strumenti
L'aggiunta di pacchetti VSPackage e i comandi corrispondenti a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] potrebbe causare una talmente dell'interfaccia utente. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce metodi per ridurre al minimo la confusione comandi dell'interfaccia utente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Miglioramento della disponibilità dei comandi](../../extensibility/internals/making-commands-available.md)  
 Fornisce linee guida generali per ridurre al minimo affollare del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente quando si aggiungono pacchetti VSPackage.  
  
 [Linee guida per la selezione host](../../extensibility/internals/command-placement-guidelines.md)  
 Fornisce linee guida specifiche per l'implementazione di un VSPackage in base alle dimensioni del set di comandi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.