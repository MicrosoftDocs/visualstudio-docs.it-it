---
title: Origine controllo integrazione Essentials | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5d474e00186cf2110dd8e701d980a1a4562beb8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-integration-essentials"></a>Origine di controllo di integrazione di Essentials
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta due tipi di integrazione del controllo codice sorgente: plug-in controllo di origine che fornisce funzionalità di base e viene compilato utilizzando l'API plug-in controllo origine (precedentemente noto come API MSSCCI) e una soluzione di integrazione del controllo origine dati basata su VSPackage che fornisce la funzionalità più affidabile.  
  
## <a name="source-control-plug-in"></a>Plug-in controllo del codice sorgente  
 Un plug-in controllo di origine viene scritto come DLL che implementa l'API plug-in controllo di origine. La funzionalità di integrazione controllo la registrazione e di origine viene fornita tramite l'API. Questo approccio è più facile da implementare rispetto a un controllo del codice sorgente VSPackage e viene utilizzato il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente (UI) per la maggior parte delle operazioni del controllo codice sorgente.  
  
 Per implementare un controllo del codice sorgente plug-in tramite l'API plug-in controllo di origine, seguire questi passaggi:  
  
1.  Creare una DLL che implementa le funzioni specificate nel [Plug-in controllo del codice sorgente](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrare la DLL apportando le voci del Registro di sistema appropriata, come descritto in [procedura: installare un plug-in controllo origine](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Creare un file di supporto dell'interfaccia utente da visualizzare quando viene richiesto dal pacchetto di scheda di controllo di origine (il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente che gestisce controllo del codice sorgente tramite plug-in del controllo codice sorgente).  
  
 Per ulteriori informazioni, vedere [la creazione di un plug-in controllo origine](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Origine pacchetto VSPackage di controllo  
 Implementazione di VSPackage un controllo del codice sorgente consente di sviluppare una sostituzione personalizzata per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente di controllo del codice sorgente. Questo approccio fornisce il controllo completo di integrazione del controllo codice sorgente, ma è necessario fornire elementi dell'interfaccia utente e implementare le interfacce di controllo di origine che in caso contrario verrebbero fornite con l'approccio di plug-in.  
  
 Per implementare un controllo del codice sorgente VSPackage, è necessario:  
  
1.  Creare e registrare un controllo origine VSPackage, come descritto in [registrazione e la selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Sostituire il controllo del codice sorgente predefinite dell'interfaccia utente con l'interfaccia utente personalizzata. Vedere [interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Specificare i glifi da utilizzare e gestire **Esplora** eventi glifo. Vedere [glifo controllo](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Gestire gli eventi di modifica di Query e salvare Query, come illustrato nella [salvare Query modifica Query](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Per ulteriori informazioni, vedere [creando un pacchetto VSPackage controllo origine](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica](../../extensibility/internals/source-control-integration-overview.md)   
 [Creazione di plug-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)