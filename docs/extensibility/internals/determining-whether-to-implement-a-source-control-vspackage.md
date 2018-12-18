---
title: Per determinare se implementare un controllo di origine pacchetto VSPackage | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 88281496c2e8350f910feda7934e2b55a494243b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Per determinare se implementare un controllo di origine pacchetto VSPackage
In questa sezione vengono illustrate le scelte del plug-in del controllo origine e di controllo del codice sorgente VSPackage per l'estensione di controllo del codice sorgente soluzioni e fornisce linee guida generali sulla scelta di un percorso di integrazione adatto.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Soluzione di controllo di origine di dimensioni ridotte con risorse limitate  
 Se si dispongano di risorse limitate e non può essere migliore con l'overhead della scrittura di un pacchetto di controllo di origine, è possibile creare plug-in basato su API plug-in controllo di origine. Ciò consente di lavorare in modo affiancato con pacchetti di controllo di origine e per passare da plug-in del controllo codice sorgente e i pacchetti su richiesta. Per ulteriori informazioni, vedere [registrazione e la selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Soluzione di controllo di grandi dimensioni di origine con un Set di funzionalità avanzate  
 Se si desidera implementare una soluzione di controllo di origine che fornisce un modello di controllo completo di origine che non viene acquisito in modo adeguato tramite l'API plug-in controllo di origine, è possibile considerare un pacchetto di controllo di origine come percorso di integrazione. Questo vale in particolare se invece si sostituirà il pacchetto di scheda di controllo di origine (che comunica con plug-in del controllo codice sorgente e fornisce un controllo del codice sorgente di base dell'interfaccia utente) con valori personalizzati in modo che sia possibile gestire gli eventi di controllo di origine in modo personalizzato. Se si dispone già di un'origine soddisfacente controllo dell'interfaccia utente e per mantenere tale esperienza acquisita in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'opzione di pacchetto di origine controllo consente di farlo. Il package del controllo del codice sorgente non è generico e progettata esclusivamente per l'utilizzo con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Se si desidera implementare una soluzione di controllo di origine che offre flessibilità e controllo più dettagliato per l'interfaccia utente e la logica del controllo origine, è preferibile instradamento controllo pacchetto integration. È possibile:  
  
1.  Registrare un controllo origine pacchetto VSPackage (vedere [registrazione e la selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Sostituire il controllo del codice sorgente predefinite dell'interfaccia utente con l'interfaccia utente personalizzata (vedere [interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Specificare i glifi da utilizzare e gestire gli eventi del glifo di Esplora soluzioni (vedere [controllo glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Gestire gli eventi di modifica di Query e salvare Query (vedere [salvare Query modifica Query](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)