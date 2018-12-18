---
title: 'Errore: RPC richiede autenticazione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 73cd474d415a49b6dd9075559d8618289b1b0d21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-rpc-requires-authentication"></a>Errore: RPC richiede autenticazione
Il debugger di Visual Studio non può connettersi al computer remoto. I criteri RPC abilitati sul computer locale impediscono il debug remoto.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Eseguire `\` *windir*`\system32\regedt32.exe`  
  
2.  Individuare ed eliminare `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Riavviare il computer per rendere effettiva la modifica del Registro di sistema.  
  
4.  Se il problema persiste, contattare l'amministratore di dominio di **configurazione Computer > modelli amministrativi > sistema > Remote Procedure Call > restrizioni per i client RPC non autenticati** criteri di gruppo l'impostazione.