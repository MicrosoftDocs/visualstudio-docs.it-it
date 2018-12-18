---
title: "I comandi e menu che utilizzano gli assembly di interoperabilità | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d89b698a97d1793b3c5255966d9eca35ec1b78f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>I comandi e menu che utilizzano gli assembly di interoperabilità
Un VSPackage che implementa i comandi di menu e barra degli strumenti tramite assembly di interoperabilità deve:  
  
-   Informare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) sui comandi supportati e se sono attualmente abilitate.  
  
-   Rispettare le regole (contratto) per la gestione dei comandi.  
  
-   Implementare in modo esplicito la gestione dei comandi utilizzando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia.  
  
 Di seguito viene descritto come eseguire queste attività.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Determinazione dello stato dei comandi in base agli assembly di interoperabilità](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Viene descritto come un pacchetto VSPackage notifica all'IDE relative ai comandi supporta e che sono attualmente abilitate.  
  
 [Contratti dei comandi negli assembly di interoperabilità](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Fornisce una definizione del contratto di comando di base utilizzato da tutti i pacchetti VSPackage che implementa i comandi tramite assembly di interoperabilità  
  
 [Implementazione](../../extensibility/internals/command-implementation.md)  
 Viene fornita una panoramica di come un pacchetto VSPackage implementa un comando.  
  
 [Registrazione dei gestori dei comandi negli assembly di interoperabilità](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Descrive le voci del Registro di sistema necessarie per inviare una notifica dell'IDE che un pacchetto VSPackage fornisce un gestore del comando.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Disponibilità](../../extensibility/internals/command-availability.md)  
 Descrive i criteri utilizzati per determinare quali comandi VSPackage sono disponibili e l'oggetto che gestisce tali dall'IDE.  
  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Vengono fornite informazioni dettagliate su come creare un'interfaccia utente che utilizza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando supporto.  
  
 [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Panoramica del processo utilizzato per correlare un oggetto con la richiesta di comando corretto.