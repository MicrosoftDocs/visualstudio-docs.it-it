---
title: Creazione di un pacchetto VSPackage controllo origine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3fac86583126e94bcfaea65a82c7cf923275769
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-source-control-vspackage"></a>Creazione di un VSPackage di controllo di origine
Questa documentazione include i collegamenti per la panoramica dell'architettura di un pacchetto di controllo del codice sorgente integrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'API che viene definito mediante le interfacce da implementare e i servizi per l'utilizzo e un esempio che illustra una semplice origine controllare l'implementazione del pacchetto.  
  
 Con un controllo del codice sorgente VSPackage, è possibile creare un percorso di integrazione per controllo del codice sorgente per l'integrazione con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Consente il pacchetto di ignorare il controllo del codice sorgente predefinite dell'interfaccia utente ospitati da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], rispondere alle richieste di controllo di origine del sistema del progetto e interagire con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componenti, ad esempio **Esplora**. Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] conferisce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] collabora con un meccanismo per creare un pacchetto VSPackage che può essere integrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzando un modello di servizio.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Viene descritto il pacchetto di controllo di origine, che è un'alternativa più avanzata per il plug-in per implementare le funzionalità di controllo di origine nel controllo del codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Architettura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Viene presentato un diagramma e vengono illustrati i componenti di un pacchetto di controllo di origine.  
  
 [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)  
 Descrive le varie funzionalità di un pacchetto di controllo di origine.  
  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Descrive la struttura del pacchetto VSPackage che un pacchetto di controllo di origine deve implementare per l'integrazione completa.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Viene illustrato come creare un controllo del codice sorgente plug-in che fornisce controllo del codice sorgente nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia di origine controllo utente (UI).  
  
 [Controllo del codice sorgente](../../extensibility/internals/source-control.md)  
 Vengono descritte le opzioni per l'implementazione del controllo del codice sorgente come una funzionalità integrata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].