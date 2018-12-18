---
title: Architettura plug-in del controllo origine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 22929c34d656fb4f163076ca0b5dfb498d44c884
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-in-architecture"></a>Architettura plug-in controllo di origine
È possibile aggiungere il supporto del controllo di origine per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) implementando e collegamento di un plug-in controllo del codice sorgente. L'IDE si connette il controllo del codice sorgente plug-in tramite l'API di plug-in controllo origine ben definito. L'IDE espone le funzionalità di controllo di versione del sistema di origine, fornendo un'interfaccia utente (UI) che include i comandi di menu e barre degli strumenti. Il plug-in controllo del codice sorgente implementa la funzionalità di controllo di origine.  
  
## <a name="source-control-plug-in-resources"></a>Risorse di plug-in controllo di origine  
 Il plug-in controllo di origine vengono fornite risorse che consentono di creare e collegare l'applicazione di controllo delle versioni per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Il plug-in controllo di origine contiene la specifica di API che deve essere implementata da un plug-in controllo del codice sorgente, in modo che è possibile integrare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Contiene inoltre un esempio di codice (scritto in C++) che implementa una struttura implementazione del controllo plug-nella dimostrazione delle funzioni essenziali compatibile con l'API plug-in controllo di origine.  
  
 La specifica dell'API di plug-in controllo origine consente di utilizzare qualsiasi controllo del codice sorgente di propria scelta, se si crea un controllo del codice sorgente DLL con il set di funzioni implementati in conformità con l'API plug-in controllo di origine necessari.  
  
## <a name="components"></a>Componenti  
 Il pacchetto di scheda di controllo di origine nel diagramma è il componente dell'IDE che traduce la richiesta dell'utente per un'operazione di controllo del codice sorgente in una chiamata di funzione supportata dal plug-in controllo del codice sorgente. A tale scopo, l'IDE e il plug-in controllo del codice sorgente deve avere una finestra di dialogo efficace che passa informazioni avanti e indietro tra l'IDE e del plug-in. Per questa finestra di dialogo eseguire entrambi devono parlano la stessa lingua. L'API plug-in controllo origine descritte in questa documentazione è il vocabolario comune per questo scambio.  
  
 ![Diagramma dell'architettura di controllo codice sorgente](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
Diagramma dell'architettura con l'interazione tra Visual Studio e controllo del codice sorgente plug-in  
  
 Come illustrato nel diagramma dell'architettura, la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell, etichettata come shell di Visual Studio nel diagramma, ospita i progetti di lavoro dell'utente e i componenti associati, ad esempio l'Editor ed Esplora soluzioni. Il pacchetto di Adapter origine controllo gestisce l'interazione tra l'IDE e il plug-in controllo del codice sorgente. Il pacchetto di origine controllo scheda fornisce il proprio controllo del codice sorgente dell'interfaccia utente. È l'interfaccia utente di primo livello che l'utente interagisce con per avviare e definire l'ambito di un'operazione di controllo del codice sorgente.  
  
 Il plug-in controllo del codice sorgente può avere la propria interfaccia utente, che può essere costituito da due parti come illustrato nella figura. La casella "Fornitore dell'interfaccia utente" rappresenta elementi dell'interfaccia utente personalizzata specificata dall'utente, un autore del plug-in del controllo origine. Quando l'utente richiama un'operazione di controllo avanzati di origine, questi vengono visualizzati direttamente per il plug-in controllo del codice sorgente. La casella "Supporto dell'interfaccia utente" è un set di origine del plug-in dell'interfaccia utente funzionalità di controllo che vengono richiamati indirettamente tramite l'IDE. Il plug-in controllo del codice sorgente passa i messaggi relativi all'interfaccia utente all'IDE tramite funzioni speciali di callback fornita dall'IDE. L'interfaccia utente del supporto facilita un'integrazione più affidabile con l'IDE (spesso mediante l'utilizzo di un **avanzate** pulsante) e pertanto fornisce un'esperienza utente finale più unificata.  
  
 Un plug-in controllo del codice sorgente non è possibile apportare modifiche per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] della shell e, di conseguenza, per il pacchetto di scheda di controllo di origine o l'origine di controllo dell'interfaccia utente fornita dall'IDE. È necessario sfruttare al massimo alla flessibilità offerta tramite l'implementazione delle diverse funzioni dell'API di plug-in controllo di origine che contribuiscono a un'esperienza integrata per l'utente finale. La sezione di riferimento della documentazione dell'API di plug-in controllo di origine include informazioni per alcune funzionalità di plug-in del controllo origine avanzate. Per sfruttare queste funzionalità, il plug-in controllo del codice sorgente deve dichiarare le funzionalità avanzate di IDE durante l'inizializzazione e deve implementare funzioni avanzate specifiche per ogni funzionalità.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo codice sorgente](../../extensibility/source-control-plug-ins.md)   
 [Glossario](../../extensibility/source-control-plug-in-glossary.md)   
 [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)