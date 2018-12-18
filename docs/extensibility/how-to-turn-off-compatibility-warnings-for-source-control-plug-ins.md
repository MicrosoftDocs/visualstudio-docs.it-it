---
title: "Disattivare gli avvisi di compatibilità per i Plug-in del controllo codice sorgente | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 622c0d4a75289e5025051b339b959a6b0b56442d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Procedura: disattivare gli avvisi di compatibilità per i Plug-in del controllo codice sorgente
Un utente potrebbe vedere alcuni avvisi di compatibilità quando si utilizza controllo del codice sorgente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Gli avvisi presentati dipendono dalle funzionalità di plug-in controllo del codice sorgente e possono essere disabilitati come dettagliate qui.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Per disabilitare l'avviso: "per garantire l'integrazione del controllo origine ottimale con Visual Studio..."  
  
-   Impostare la seguente voce del Registro di sistema (se necessario, aggiungere il valore):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Questo avviso viene visualizzato per tutti non[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-in.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Per disabilitare l'avviso: "il provider del controllo del codice sorgente installato non supporta tutte le funzionalità..."  
  
-   Impostare i seguenti valori del Registro di sistema (se necessario, aggiungere i valori):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Questo avviso viene visualizzato se il plug-in controllo del codice sorgente non supportano in modo esplicito della reentrancy per più progetti (ovvero, se è possibile verificare in un solo file e di progetto in un momento).  
  
     È consigliabile per il supporto della reentrancy (`SCC_CAP_REENTRANT` funzionalità); verrà rimosso questo avviso. Tuttavia, se tale supporto non è possibile, è possono impostare queste voci del Registro di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Flag di funzionalità](../extensibility/capability-flags.md)