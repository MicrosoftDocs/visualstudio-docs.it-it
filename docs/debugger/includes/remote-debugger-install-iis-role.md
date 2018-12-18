---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: dbc9d727dc412e3d354d806a45c352eef810cd99
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
Procedura mostra solo una configurazione di base di IIS. Per ulteriori informazioni o per installare in un computer Desktop Windows, vedere [la pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) o [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Per i sistemi operativi Windows Server, utilizzare il **Aggiungi ruoli e funzionalità** guidata tramite la **Gestisci** collegamento o **Dashboard** sul collegamento nella **diServerManager**. Nel passaggio **Ruoli del server** selezionare la casella per **Server Web (IIS)**.

![Il ruolo Server Web IIS viene selezionato nel passaggio dei ruoli del server Selezionare.](../media/remotedbg-server-roles-ws2012.png)

Nel passaggio **Servizi ruolo** selezionare i servizi ruolo IIS desiderato o accettare i servizi ruolo predefiniti forniti.

Procedere con la procedura di conferma per installare il ruolo server web e servizi. Un riavvio del server/IIS non è necessario dopo l'installazione del ruolo Server Web (IIS).