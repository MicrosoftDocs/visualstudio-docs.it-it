---
title: 'Errore: RPC richiede autenticazione | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.rpc_requires_authentication
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
ms.openlocfilehash: 214dafa5acc925434cf3569570f20ab7f3331bfb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-rpc-requires-authentication"></a>Errore: RPC richiede autenticazione
Il debugger di Visual Studio non può connettersi al computer remoto. I criteri RPC abilitati sul computer locale impediscono il debug remoto.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Eseguire `\` *windir*`\system32\regedt32.exe`  
  
2.  Individuare ed eliminare `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Riavviare il computer per rendere effettiva la modifica del Registro di sistema.  
  
4.  Se il problema persiste, contattare l'amministratore di dominio di **configurazione Computer > modelli amministrativi > sistema > Remote Procedure Call > restrizioni per i client RPC non autenticati** criteri di gruppo l'impostazione.