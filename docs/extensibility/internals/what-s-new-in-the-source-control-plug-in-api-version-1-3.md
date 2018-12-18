---
title: Novità&#39;s nuove nell'origine di controllo del plug-in API versione 1.3 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abeb2a0a936a5d706e2e3744e9dd0f4e3123bdbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Novità&#39;s nuove nell'origine di controllo del plug-in API versione 1.3
L'API di plug-in controllo origine versione 1.3 introduce le nuove funzioni seguenti per fornire un controllo più avanzata.  
  
## <a name="changes"></a>Modifiche  
 Le funzioni seguenti sono nuove per l'API di plug-in controllo origine versione 1.3:  
  
|Funzione|Panoramica|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Consente di bit di capacità aggiuntive da segnalare|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Consente di esaminare di file con le versioni più recenti nel database di controllo della versione sul disco locale|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Consente di esaminare dello stato delle modifiche dei nomi (ridenominazioni, aggiunte ed eliminazioni) per i file specificati|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Consente di esaminare di directory e file nel database del controllo della versione|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco di file specificato dal database di controllo di versione per il progetto corrente|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Esegue un invisibile all'utente "Get" dei file specificati (non è visualizzata alcuna interfaccia utente)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Consente di accedere alle opzioni specifiche dell'utente|  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)