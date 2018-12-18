---
title: 'Procedura: Configurare le regole di prestazioni | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c9b389f570a1dd0a16fb4266268be953433aaa1e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-performance-rules"></a>Procedura: Configurare le regole di prestazioni
Gli avvisi di prestazioni degli strumenti di profilatura di Visual Studio segnalano i problemi che possono rallentare l'esecuzione di un'applicazione profilata. Gli avvisi possono anche indicare che potrebbe essere necessario modificare i metodi di raccolta per raccogliere dati più utili. Gli avvisi di prestazioni vengono generati automaticamente in una sessione di profilatura e visualizzati nella finestra **Elenco errori** quando un file di dati di profilatura viene aperto in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Alcuni avvisi potrebbero non essere applicabili agli scenari desiderati, mentre altri potrebbero essere generati in modo non corretto. È possibile configurare gli avvisi di prestazioni per mostrare o nascondere avvisi specifici.  
  
### <a name="to-configure-profiler-performance-warnings"></a>Per configurare gli avvisi di prestazioni del profiler  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Espandere **Strumenti per le prestazioni** e quindi fare clic su **Regole**.  
  
3.  Per abilitare o disabilitare un avviso, selezionare o deselezionare la casella di controllo accanto all'**ID** e al nome dell'avviso.  
  
4.  Per specificare il livello di avviso di una regola, fare clic sulla cella **Azione** accanto alla regola e quindi fare clic sul livello di avviso.  
  
    -   **Disabilitato**: disabilita la regola ed equivale a deselezionare la casella di controllo accanto all'ID della regola.  
  
    -   **Avviso**: visualizza la regola come avviso.  
  
    -   **Errore**: interrompe l'esecuzione della profilatura e visualizza la regola come errore.  
  
    -   **Informazioni**: visualizza la regola solo a scopo informativo.