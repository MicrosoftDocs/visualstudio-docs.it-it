---
title: 'Procedura: eseguire il Debug di client e server mediante il debug RPC COM | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1404d81502aaa0579c20511f3eecafa86607df0d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Procedura: eseguire il debug di client e server COM mediante il debug RPC
È possibile utilizzare il debug RPC (Remote Procedure Call, chiamata a procedura remota) per eseguire il debug delle applicazioni client/server COM. Per utilizzare tale debug, è necessario attivarlo. Quando si chiama il server dal client con il debug RPC attivato, il debugger si connette al server e consente di eseguire il debug del codice. Una volta stabilita la connessione al server, è possibile utilizzare tutte le funzionalità del debugger per i processi del client e del server.  
  
### <a name="to-enable-rpc-debugging"></a>Per attivare il debug RPC  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **opzioni** la finestra di dialogo, fare clic su di **debug** cartella.  
  
3.  Fare clic su di **nativo** pagina.  
  
4.  Selezionare il **il debug RPC** casella di controllo.  
  
    > [!NOTE]
    >  Per eseguire il debug delle chiamate RPC, è necessario disporre dei privilegi di tipo Administrator o Power User.  
  
    > [!NOTE]
    >  L'esecuzione di chiamate RPC a un server remoto che esegue Microsoft Windows Vista funzionerà solo se un debugger nativo è connesso al server remoto. In caso contrario, la chiamata RPC non verrà eseguita senza restituire alcun messaggio di errore oppure verrà completata, ma non funzionerà.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei server e dei contenitori COM](../debugger/com-server-and-container-debugging.md)  
 [Debug in Visual Studio](../debugger/index.md) [Tour delle funzionalità del Debugger](../debugger/debugger-feature-tour.md)