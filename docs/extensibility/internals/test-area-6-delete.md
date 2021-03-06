---
title: 'Area di test 6: eliminare | Microsoft Docs'
description: Questa area di test del controllo del codice sorgente riguarda le azioni Delete in Esplora soluzioni per il plug-in del controllo del codice sorgente di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e405df704dfbba14413bd3787a9fb9f959c62a46
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078591"
---
# <a name="test-area-6-delete"></a>Area di test 6: Eliminare
Questa area di test del plug-in del controllo del codice sorgente copre le azioni di eliminazione.

 Il controllo del codice sorgente risponde per eliminare le azioni in **Esplora soluzioni**.

 Di seguito è riportato un elenco di elementi che possono essere eliminati:

- File

- Cartelle

- Project

  A seconda del tipo di progetto, è possibile scegliere di **rimuovere** il progetto (lascia i file su disco) o **eliminare** il progetto (rimuove i file su disco). Entrambe le azioni rimuovono il progetto o l'elemento da **Esplora soluzioni**.

## <a name="expected-behavior"></a>Comportamento previsto
 Il comportamento previsto per i test case nell'area Elimina test è:

- L'elemento eliminato non è più visibile all'interno **Esplora soluzioni**.

- Il padre del progetto o dell'elemento eliminato viene estratto in base alle esigenze (possibilmente con un prompt).

- Dopo aver eliminato un elemento estratto o aggiunto, questo elemento non viene visualizzato nella finestra **archiviazioni in sospeso** .

- L'elemento è ancora presente nell'archivio del controllo del codice sorgente, anche dopo l'eliminazione e deve essere eliminato manualmente.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Eliminare un progetto client|1. creare un progetto client.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. rimuovere l'intero progetto dalla soluzione|Comportamento previsto comune.|
|Elimina un file vuoto|1. creare un progetto client.<br />2. aggiungere un file di zero byte al progetto.<br />3. aggiungere la soluzione al controllo del codice sorgente.<br />4. Selezionare il file ed eliminarlo.|Comportamento previsto comune.|
|Elimina una cartella con un file|1. creare una soluzione di progetto singolo.<br />2. aggiungere una cartella.<br />3. aggiungere un file alla cartella.<br />4. aggiungere la soluzione al controllo del codice sorgente.<br />5. vedere il progetto per evitare richieste.<br />6. eliminare la cartella.|Comportamento previsto comune.|
|Eliminare un progetto Web del file System|1. creare un progetto Web di file System (usare il pulsante Sfoglia per specificare un percorso UNC).<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. rimuovere l'intero progetto dalla soluzione.<br />4. Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercizi diversi nel codice ma con la stessa interfaccia esterna e il medesimo comportamento).|Comportamento previsto comune.|
|Eliminare un file da un progetto Web di file System|1. creare un progetto Web di file System.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. eliminare un file dal progetto.<br />4. Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercizi diversi nel codice ma con la stessa interfaccia esterna e il medesimo comportamento).|Comportamento previsto comune.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
