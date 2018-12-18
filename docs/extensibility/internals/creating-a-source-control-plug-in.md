---
title: Creazione di plug-in un controllo del codice sorgente | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 679559b70096dc7ec3baa792ea98c0c3fea7cc67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-source-control-plug-in"></a>Creazione di plug-in un controllo del codice sorgente
Visual Studio SDK fornisce le risorse che consentono di aggiungere funzionalità di controllo di origine per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Consente di utilizzare qualsiasi DLL plug-in che è conforme con l'API plug-in controllo origine descritte in questa documentazione.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Viene descritto come installare un plug-in controllo del codice sorgente ed evidenziare le versioni API plug-in controllo di origine attualmente disponibile.  
  
 [Architettura](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Usa un diagramma dell'architettura per spiegare l'integrazione di un controllo del codice sorgente plug-in con il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Vengono fornite istruzioni su come testare l'installazione e l'operazione di un plug-in controllo del codice sorgente.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Viene illustrato come creare un controllo del codice sorgente VSPackage che non solo fornisce controllo del codice sorgente ma sostituisce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente di controllo del codice sorgente.  
  
 [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)  
 Fornisce un elenco completo di tutti gli elementi nell'API di plug-in del controllo origine.  
  
 [Controllo del codice sorgente](../../extensibility/internals/source-control.md)  
 Vengono descritte le opzioni per l'implementazione del controllo del codice sorgente come una funzionalità integrata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].