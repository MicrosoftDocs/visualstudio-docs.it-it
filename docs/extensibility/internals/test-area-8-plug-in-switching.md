---
title: 'Test Area 8: Cambio plug-| Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9f6a518d618b3a98ec85cbbe015d3b2c5fc7a710
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-8-plug-in-switching"></a>Test Area 8: Cambio plug-
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) è l'interfaccia utente (UI) per modificare il controllo del codice sorgente corrente del plug-in. Questa area di test fornisce i test case per il processo di selezione plug-in da utilizzare per controllo del codice sorgente soluzioni che.  
  
## <a name="command-menu-access"></a>Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi menu dell'ambiente di sviluppo integrato nei test case.  
  
-   Plug-in controllo del codice sorgente corrente: **strumenti** -> **opzioni** -> **controllo del codice sorgente** -> **Selezione plug-in** .  
  
-   Modifica dell'origine dell'associazione di controllo: **File** -> **controllo del codice sorgente** -> **Modifica controllo del codice sorgente**...  
  
## <a name="common-expected-behavior"></a>Comportamento previsto comune  
 Modifica il plug-in per una soluzione di controllo del codice sorgente può essere eseguita senza uscire da Visual Studio o il ricaricamento della soluzione. Inoltre, il controllo del codice sorgente corrente del plug-in modifica automaticamente a quello utilizzato da una soluzione quando viene caricata la soluzione.  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case, dell'area di commutazione plug-in test.  
  
### <a name="case-8a-automatic-change"></a>Caso 8a: delle modifiche automatico  
  
#### <a name="expected-behavior"></a>Comportamento previsto  
 Quando un utente carica una soluzione nel controllo del codice sorgente, la soluzione viene caricata automaticamente e il plug-in controllo del codice sorgente appropriato viene selezionato come corrente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Modifica di plug-in controllo origine automatico|1.  Selezionare plug-nel test corrente (**strumenti** -> **opzioni** -> **controllo del codice sorgente** -> **plug-in Selezione**.)<br />2.  Creare un nuovo progetto.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Selezionare un altro plug-in (ad esempio, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  Accettare il prompt di soluzione lo scaricamento.<br />6.  Riaprire la soluzione dal disco.|Soluzione è aperta.<br /><br /> Plug-in sottoposta a test è il controllo del codice sorgente corrente del plug-in.|  
  
### <a name="case-8b-solution-based-change"></a>Caso 8 b: modifica basati su una soluzione  
  
#### <a name="expected-behavior"></a>Comportamento previsto  
 La soluzione può avere il controllo del codice sorgente associato plug-in modificato.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Modifica del plug-in per una soluzione|1.  Selezionare plug-nel test corrente (**strumenti** -> **opzioni** -> **controllo del codice sorgente** -> **plug-in Selezione**).<br />2.  Creare un nuovo progetto e soluzione.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Separare la soluzione dal controllo del codice sorgente (utilizzando la **Modifica controllo del codice sorgente** la finestra di dialogo).<br />5.  Selezionare un altro plug-in (ad esempio, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  Ricaricamento della soluzione dal disco se scaricato.<br />7.  Aggiungere la soluzione al controllo del codice sorgente.<br />8.  Separare la soluzione dal controllo del codice sorgente (utilizzando **Modifica controllo del codice sorgente** la finestra di dialogo).<br />9. Selezionare un plug-in da testare nuovamente.<br />10. Ricaricare la soluzione dal disco se scaricato.<br />11. Associare la soluzione nel percorso originale (tramite il **Modifica controllo del codice sorgente** la finestra di dialogo).|Soluzione viene aggiunta al controllo del codice sorgente utilizzando il plug-in.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)