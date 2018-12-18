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
ms.openlocfilehash: 81b58a2162d7240e32e1fb2d45e462ec551155e7
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2017
---
1. Se si prevede di distribuire le applicazioni con distribuzione Web in Visual Studio, installare la versione più recente di distribuzione Web nel server.

    Per installare distribuzione Web, utilizzare il [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Trovare distribuzione Web nella scheda applicazioni. È anche possibile ottenere direttamente da un programma di installazione di [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Verificare che la distribuzione Web è in esecuzione correttamente aprendo **Pannello di controllo > sistema e sicurezza > Strumenti di amministrazione > servizi** e verificare che **servizio agente distribuzione Web** è in esecuzione (la nome del servizio è diverso nelle versioni precedenti).

    Se il servizio dell'agente non è in esecuzione, avviarlo. Se non è presente in tutti, passare a **Pannello di controllo > programmi > Disinstalla un programma**, trovare **Microsoft Web Deploy <version>** . Scegliere di **modifica** l'installazione e assicurarsi di scegliere **verrà installata sul disco rigido locale** per i componenti di distribuzione Web. Completare i passaggi di installazione di modifica.