---
title: 'Area di test 7: condivisione | Microsoft Docs'
description: Questa area di test del controllo del codice sorgente copre la condivisione di elementi tra percorsi tramite il comando Condividi per il plug-in del controllo del codice sorgente di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: facfb48fbe02ff374c594f1ddadf0710c1f989d6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074353"
---
# <a name="test-area-7-share"></a>Area di test 7: Condividi
Questa area di test copre la condivisione di elementi tra percorsi tramite il comando **share** .

 Un'operazione hhare è la duplicazione apparente di file e elementi di cartella tra due o più posizioni all'interno di una gerarchia di file del controllo del codice sorgente. La duplicazione non viene effettivamente eseguita sul server, ma l'utente visualizza lo stesso file in due o più percorsi specificati. Ogni volta che vengono apportate modifiche a uno degli elementi condivisi, le modifiche vengono visualizzate in tutti gli altri percorsi condivisi.

 La condivisione in cartelle funziona se si seleziona una cartella con almeno un file nel controllo del codice sorgente. Il comando Condividi è disabilitato nelle condizioni seguenti:

- Se la cartella selezionata è vuota.

- Se è presente una cartella reale, ma non contiene alcun file del controllo del codice sorgente.

- Se è presente una cartella virtuale, se i file nel controllo del codice sorgente sono presenti o meno.

- Se è presente un progetto Web del sito remoto.

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Nei test case vengono utilizzati i percorsi dei menu Integrated Development Environment seguenti.

 Condivisione:  -> condivisione del **controllo del codice sorgente** del file -> .

## <a name="expected-behavior"></a>Comportamento previsto

- Il file condiviso viene visualizzato in un percorso condiviso.

- La visualizzazione della cronologia dell'archivio delle versioni del controllo del codice sorgente Mostra che i file sono condivisi.

- La modifica di un file condiviso modifica entrambe le posizioni del file.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati i test case specifici per l'area test di condivisione.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Condividere un file da un progetto caricato nel controllo del codice sorgente a un altro progetto caricato|1. creare un nuovo progetto.<br />2. aggiungere un secondo progetto alla soluzione.<br />3. creare un file nel secondo progetto con un nome non presente nel primo progetto.<br />4. aggiungere la soluzione al controllo del codice sorgente.<br />5. Selezionare il primo progetto.<br />6. finestra di dialogo Apri **condivisione** (  ->  **Condivisione controllo del codice sorgente** file  ->  ).<br />7. condividere il file dal secondo progetto al primo progetto.<br />8. se richiesto, accettare il **controllo** .|Comportamento previsto comune.|
|Condividere un file da un progetto a un altro|1. creare un nuovo progetto.<br />2. aggiungerlo al controllo del codice sorgente.<br />3. chiudere la soluzione.<br />4. creare un secondo progetto (nuova soluzione).<br />5. aggiungere la soluzione al controllo del codice sorgente.<br />6. Selezionare il progetto.<br />7. Aprire la finestra di dialogo **Condividi** (  ->  **Condivisione controllo del codice sorgente** file  ->  ).<br />8. condividere un file dal progetto aggiunto in precedenza al progetto aperto.<br />9. se richiesto, accettare il **controllo** .|Comportamento previsto comune.|
|Condividere un file non parte del progetto dal controllo del codice sorgente nel progetto attualmente caricato|1. creare un nuovo progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. aggiungere un file al controllo del codice sorgente che non fa parte del progetto o della soluzione.<br />4. Selezionare il progetto e aprire la finestra di dialogo **Condividi** (  ->  **Condivisione controllo del codice sorgente** file  ->  ).<br />5. Selezionare un file nella finestra di dialogo **Condividi** che non esiste all'interno del progetto o della soluzione corrente e condividerlo.<br />6. se richiesto, accettare il **controllo** .|L'archivio del controllo del codice sorgente ha eseguito un'operazione get, quindi il file è ora il percorso locale del progetto.|
|Condividere i file all'interno dello stesso progetto in un'altra cartella|1. Selezionare **Estrai automaticamente** in **strumenti**  ->  **Opzioni**  ->  **controllo del codice sorgente**.<br />2. creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />3. aggiungere una cartella al progetto.<br />4. aggiungere un file alla cartella e archiviare la cartella.<br />5. Selezionare la cartella.<br />6. finestra di dialogo Apri **condivisione** (  ->  **Condivisione controllo del codice sorgente** file  ->  ).<br />7. condividere il file nella cartella selezionata.|Comportamento previsto comune.<br /><br /> È necessario archiviare la cartella con un file al suo interno prima di poterla usare per la condivisione.|
|Condividere una cartella nel progetto caricato: ricorsivo|1. creare un nuovo progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. Selezionare il progetto.<br />4. Aprire la finestra di dialogo **Condividi** (  ->  **Condivisione controllo del codice sorgente** file  ->  ).<br />5. Selezionare una cartella.<br />6. condividere la cartella in modo ricorsivo nel progetto.|Comportamento previsto comune.|
|Condividere più file da un progetto a un altro|1. creare un nuovo progetto con più file.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. chiudere la soluzione.<br />4. creare un nuovo progetto in una nuova soluzione.<br />5. aggiungere la soluzione al controllo del codice sorgente.<br />6. Selezionare il progetto.<br />7. Aprire la finestra di dialogo **Condividi** (  ->  **Condivisione controllo del codice sorgente** file  ->  ).<br />8. condividere diversi file dal progetto creato in precedenza al progetto attualmente aperto.|Comportamento previsto comune.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
