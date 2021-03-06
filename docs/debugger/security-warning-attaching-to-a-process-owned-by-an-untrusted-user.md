---
description: Questa finestra di dialogo di avviso viene visualizzata quando si stabilisce una connessione a un processo che contiene codice parzialmente attendibile o codice di proprietà di un utente non attendibile subito prima che abbia luogo la connessione.
title: 'Avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non sono sicure, non connettersi a questo processo | Microsoft Docs'
ms.date: 1/15/2021
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fe65e753a0e825eed0c09fdefc4e93168d27ecb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160316"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo

Questa finestra di dialogo di avviso viene visualizzata quando si stabilisce una connessione a un processo che contiene codice parzialmente attendibile o codice di proprietà di un utente non attendibile subito prima che abbia luogo la connessione. Un processo non attendibile contenente codice malware può danneggiare il computer durante l'esecuzione del debug. Se si ritiene che il processo non sia attendibile, è opportuno fare clic su **Annulla** per impedire il debug.

Negli scenari IIS, è possibile che venga visualizzato questo avviso se si usa un pool di applicazioni personalizzato, che non è attendibile.

Per non visualizzare questo avviso durante il debug di uno scenario legittimo:

1. Chiudere Visual Studio.

1. Impostare il valore della `DisableAttachSecurityWarning` chiave del registro di sistema su 1.

   Trovare o creare la chiave in `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger` e impostarla su 1.

   A partire da Visual Studio 2017, se si vuole visualizzare le impostazioni complete del registro di sistema, è necessario caricare l'hive del registro di sistema privato. Per ulteriori informazioni, vedere [come esaminare il registro di sistema di Visual Studio 2017](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md). Assicurarsi di scaricare l'hive del registro di sistema privato prima di avviare Visual Studio.

1. Riavviare Visual Studio.

1. Dopo aver completato il debug dello scenario, reimpostare il valore su 0 e riavviare Visual Studio.

Tra gli utenti attendibili sono inclusi quello che esegue il debug e un set di utenti standard comunemente definiti nei computer in cui è installato .NET Framework, ad esempio `aspnet`, `localsystem`, `networkservice` e `localservice`.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

 Nome dell'assembly richiesto per il debug

 Utente corrente utente

 Connetti premere per continuare a eseguire il debug mediante connessione

 Non connettersi al processo

## <a name="see-also"></a>Vedi anche
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
