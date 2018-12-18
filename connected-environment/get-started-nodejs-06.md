---
title: 'Creare un ambiente di sviluppo Node.js con i contenitori usando Kubernetes nel cloud con Visual Studio - Passaggio 6: Informazioni sullo sviluppo in team | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 4db1d71c96da29a06884e562a277a7ca427910d4
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introduzione a Connected Environment con Node.js

Passaggio precedente: [Chiamare un servizio in esecuzione in un contenitore separato](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Eccolo in azione:
1. Passare alla finestra di Visual Studio Code per `mywebapi` e apportare una modifica al codice per il gestore predefinito `/` GET, ad esempio:

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [avanti](get-started-nodejs-07.md)

