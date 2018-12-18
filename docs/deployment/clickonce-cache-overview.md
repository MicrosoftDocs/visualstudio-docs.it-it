---
title: Cenni preliminari sulla Cache di ClickOnce | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ff72cd106f39b4573a0e1d61715dad4f8c65140
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-cache-overview"></a>Cenni preliminari sulla cache di ClickOnce
Tutti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni, se vengono installati in locale o ospitati online, vengono archiviate nel computer client in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]applicazione *cache*. Oggetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache è una famiglia di sottodirectory nascoste nella directory delle impostazioni locali della cartella Documents and Settings dell'utente corrente. Questa cache contiene tutti i file dell'applicazione, inclusi gli assembly, i file di configurazione dell'applicazione e le impostazioni utente e directory dei dati. La cache è inoltre responsabile per la migrazione di directory dei dati dell'applicazione per la versione più recente. Per ulteriori informazioni sulla migrazione dei dati, vedere [l'accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Fornendo un'unica posizione per l'archiviazione di applicazioni, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] assume il compito di gestire l'installazione fisica di un'applicazione da parte dell'utente. La cache consente inoltre di isolare le applicazioni, mantenendo i file di dati per tutte le applicazioni e assembly e le relative versioni separano uno da altro. Ad esempio, quando si aggiorna un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione, che vengono fornite versione e le risorse di dati con le rispettive directory nella cache.  
  
## <a name="cache-storage-quota"></a>Quota di archiviazione della cache  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni ospitate in linea sono limitate nella quantità di spazio che può essere occupata da una quota che limita le dimensioni del [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] della cache. La dimensione della cache si applica a tutte le applicazioni dell'utente online. una singola applicazione parzialmente attendibile, in linea è limitata a metà la quota di spazio occupata. Le applicazioni installate non sono limitate dalla dimensione della cache e non vengono conteggiate rispetto al limite della cache. Per tutti i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente di mantenere applicazioni, la cache solo la versione corrente e la versione installata in precedenza.  
  
 Per impostazione predefinita, i computer client sono in linea 250 MB di spazio di archiviazione per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni. File di dati non vengono conteggiati per questo limite. Un amministratore di sistema possibile ingrandire o ridurre questa quota su un computer client specifico modificando la chiave del Registro di sistema, HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, ovvero un valore DWORD che indica le dimensioni della cache in kilobyte. Ad esempio, per ridurre le dimensioni della cache a 50 MB, si sarebbe impostare questo valore su 51200.  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)