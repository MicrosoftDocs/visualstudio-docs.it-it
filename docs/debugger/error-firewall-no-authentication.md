---
title: 'Errore: Nessuna autenticazione del Firewall | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a6a15196445555e883ebc76541f486d7de454b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="error-firewall-no-authentication"></a>Errore: nessuna autenticazione del firewall
Nel computer remoto Windows Firewall non è configurato in modo da consentire il debug remoto. Per il debug remoto con `No Authentication` è necessario aggiungere msvsmon.exe all'elenco delle eccezioni. Potrebbe inoltre essere necessario aprire alcune porte IPSEC.  
  
> [!NOTE]
>  Il debugger remoto esegue automaticamente la configurazione di Windows Firewall. Quando si utilizza un firewall diverso da Windows Firewall, ad esempio un firewall hardware o software di terze parti, è necessario configurarlo manualmente per consentire il debug remoto. A tale scopo, consentire il traffico sulle porte TCP/IP su cui msvsmon.exe è in ascolto. Per impostazione predefinita, si tratta delle porte 4018 e 4019, dove la 4018 è utilizzata in tutti i sistemi operativi e la 4019 è utilizzata solo in Windows x64 per consentire i processi di debug x86.  
  
 Per ulteriori informazioni, vedere [il debug remoto](../debugger/remote-debugging.md).