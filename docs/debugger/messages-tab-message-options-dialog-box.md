---
title: Scheda messaggi, finestra di dialogo Opzioni messaggio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b7c9d533d73039de699f59c2343f3f91f888710c
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="messages-tab-message-options-dialog-box"></a>Scheda Messaggi, Finestra di dialogo Opzioni messaggio
Utilizzare il **messaggi** tab per selezionare quali tipi di elenco nel messaggio [visualizzazione messaggi](../debugger/messages-view.md)e per specificare i criteri di ricerca di messaggi. Per visualizzare il [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md), scegliere **messaggi di Log** dal **Spy** menu.  
  
 In genere, prima selezionare **gruppi di messaggi**e quindi ottimizzare la selezione selezionando singoli **messaggi alla visualizzazione**. Il **tutti** pulsante Seleziona tutti i tipi di messaggio e **Nessuno** pulsante Cancella tutti i tipi.  
  
 Le impostazioni seguenti sono disponibili sul **messaggi** scheda:  
  
 **Messaggi alla visualizzazione**  
 Selezionare i messaggi specifici per la visualizzazione. Quando si crea una nuova finestra messaggi, è possibile visualizzare tutti i messaggi. Quando si filtrano i messaggi dal **messaggi** scheda, tale filtro si applica solo ai nuovi messaggi e non quelli che sono già stati visualizzati nella visualizzazione delle finestre.  
  
 **Gruppi di messaggi**  
 Selezionare i gruppi di messaggi per la visualizzazione. I gruppi disponibili includono:  
  
-   WM_USER: con un codice maggiore di o uguale a WM_USER  
  
-   Registrato: registrato con il **RegisterWindowMessage** chiamare  
  
-   Sconosciuto: messaggi sconosciuti nell'intervallo da 0 a (WM_USER - 1)  
  
 Si noti che queste **gruppi di messaggi** non corrispondono alle voci specifiche sotto **messaggi da visualizzare**. Quando si seleziona un gruppo, la selezione viene applicata direttamente al flusso di messaggi.  
  
 All'interno di una casella di controllo disabilitata **gruppi di messaggi** indica che il **messaggi da visualizzare** casella di riepilogo è stato modificato per i messaggi in tale gruppo, sono selezionati tutti i tipi di messaggio in tale gruppo.  
  
 **Salvare le impostazioni come predefinite**  
 Salvare le impostazioni correnti per un utilizzo successivo come opzioni di ricerca di messaggi. Queste impostazioni vengono salvate anche quando si esce da Spy + +.