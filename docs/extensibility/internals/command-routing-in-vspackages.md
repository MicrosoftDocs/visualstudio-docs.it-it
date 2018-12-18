---
title: Routing di comandi in VSPackage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 58be191a3b7a2256d0883e313f77b264f6be4d69
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="command-routing-in-vspackages"></a>Routing dei comandi in VSPackage
Un comando viene instradato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in base al contesto in cui viene eseguito. Nel contesto globale viene indirizzato dal contesto iniziale verso l'esterno.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md)  
 Descrive l'ordine di risoluzione di routing di comandi.  
  
 [Disponibilità](../../extensibility/internals/command-availability.md)  
 Vengono descritti comandi (routing).  
  
 [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Vengono illustrate considerazioni nei comandi di routing tra codice gestito e COM.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)  
 Viene descritto il modello per viene illustrato come determinare lo stato attivo contesto di selezione dell'utente in una finestra.  
  
 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.