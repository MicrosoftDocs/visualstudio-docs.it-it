---
title: Introduzione al Plug-in del controllo codice sorgente | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f5c88d932fd2915273c86924d2df8f1233baeed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-with-source-control-plug-ins"></a>Introduzione al Plug-in del controllo codice sorgente
Per creare plug-in un controllo del codice sorgente, è necessario creare una DLL che implementa le funzioni definite nell'API di plug-in controllo di origine, quindi registrare la DLL con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per renderlo disponibile per l'utilizzo nel controllo di versione del codice sorgente.  
  
 Tre versioni dell'API di plug-in controllo di origine (versioni 1.1, 1.2 e 1.3) sono disponibili per i plug-in del controllo codice sorgente. L'API plug-in controllo origine documentato qui è la versione 1.3. È stato progettato per essere completamente compatibili con plug-in del controllo codice sorgente che supporta le versioni 1.1 e 1.2. Il [novità nella versione 1.3 di origine controllo plug-in API](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) sezione illustra nel dettaglio le nuove funzionalità supportate nella versione più recente dell'API plug-in controllo di origine.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: Installare un plug-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Viene descritto come rendere le voci del Registro di sistema necessarie per collegare un controllo del codice sorgente DLL.  
  
 [Novità della versione 1.3 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Fornisce una breve panoramica delle modifiche apportate all'API plug-in controllo di origine nella versione 1.3.  
  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Fornisce una breve panoramica delle modifiche apportate all'API plug-in controllo di origine nella versione 1.2.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)  
 Fornisce un elenco completo di tutti gli elementi nell'API di plug-in del controllo origine.  
  
 [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definisce il SDK di plug-in controllo di origine e descrive le risorse incluse.