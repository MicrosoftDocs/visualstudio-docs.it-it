---
title: Configurazione delle impostazioni esecuzione test di carico
description: Informazioni sulle impostazioni di esecuzione, che sono proprietà che influenzano la modalità di esecuzione di un test di carico. Sono organizzate in categorie nella finestra Proprietà.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a606f2cb9547250db79de9defba57dc95a402bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868088"
---
# <a name="configure-load-test-run-settings"></a>Configurare le impostazioni esecuzione test di carico

Le *impostazioni esecuzione test* sono un set di proprietà che determinano la modalità di esecuzione di un test di carico. Sono organizzate in categorie nella finestra **Proprietà**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

In un test di carico si possono avere più impostazioni di esecuzione test. È tuttavia possibile attivarne solo una per ogni esecuzione. Le altre impostazioni esecuzione test consentono di selezionare in modo rapido un'impostazione alternativa da utilizzare per le successive esecuzioni dei test.

L'impostazione esecuzione test iniziale viene creata quando si crea un test di carico tramite la **Creazione guidata test di carico**.

![Impostazioni di esecuzione dei test di carico](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-|-|
|**Aggiungere altre impostazioni esecuzione test al test di carico:** oltre all'impostazione esecuzione test creata al momento dell'esecuzione della **Creazione guidata test di carico**, è possibile aggiungere altre impostazioni esecuzione al test di carico per poter eseguire il test in condizioni diverse.|-   [Procedura: Aggiungere altre impostazioni esecuzione test a un test di carico](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Specificare l'impostazione esecuzione test attiva da usare con il test di carico:** è possibile selezionare l'impostazione esecuzione test che si vuole usare con il test di carico tramite l'Editor test di carico. L'impostazione esecuzione test attiva è identificata dal suffisso "[Active]".|-   [Procedura: selezionare l'impostazione di esecuzione test attiva per un test di carico](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Modificare le proprietà delle impostazioni di esecuzione:** È possibile modificare le proprietà delle impostazioni di esecuzione per elementi come le opzioni di registrazione (vedere più avanti), determinare la lunghezza del test, la durata di riscaldamento, il numero massimo di dettagli dell'errore segnalati, la frequenza di campionamento, il modello di connessione (solo test delle prestazioni Web), il tipo di archiviazione dei risultati, il livello di convalida e la traccia SQL. Le impostazioni di esecuzione devono riflettere gli obiettivi del test di carico.|-   [Proprietà delle impostazioni di esecuzione del test di carico](../test/load-test-run-settings-properties.md)<br />-   [Modifica delle proprietà delle impostazioni di esecuzione](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Specificare il numero di iterazioni test nelle impostazioni esecuzione test di carico:** È possibile specificare il numero di volte in cui eseguire tutte le prestazioni Web e gli unit test in tutti gli scenari dei test di carico configurando la proprietà **iterazioni test** .|-   [Procedura: Specificare il numero di iterazioni test in un'impostazione di esecuzione](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Specificare la frequenza di campionamento per un'impostazione esecuzione test di carico:** è possibile specificare la frequenza con cui tramite il test di carico vengono raccolti i dati del contatore delle prestazioni configurando la proprietà **Frequenza campionamento**.|-   [Procedura: Specificare la frequenza di campionamento](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Specificare l'opzione relativa all'intervallo archiviazione dettagli:** è possibile specificare la modalità con cui salvare i dettagli del test di carico configurando la proprietà **Intervallo archiviazione dettagli**.|-   [Procedura: specificare la proprietà Intervallo archiviazione dettagli](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Specificare il tempo di conservazione delle risorse di test:** accelerare il ciclo test > correzione> ripetizione test conservando le risorse di test per un periodo specificato dalla proprietà **Tempo di conservazione risorse**.|-   [Retain the resources to speed up load testing](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts&preserve-view=true) (Conservare le risorse per accelerare il test di carico)|
|**Usare parametri di contesto:** è possibile usare parametri di contesto per impostare parametri per una stringa. Se, ad esempio, il test di carico contiene un test delle prestazioni Web che usa un server Web con parametri, è possibile aggiungere un parametro di contesto alle impostazioni esecuzione test per eseguire il mapping a un server diverso.|-   [Procedura: Aggiungere parametri di contesto a un'impostazione di esecuzione](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Configurazione delle proprietà di registrazione dei test:** è possibile configurare la frequenza con la quale vengono scritti i dati nel log associato alle impostazioni esecuzione test di carico. Questa operazione può essere importante quando si esegue un test di carico di grandi dimensioni o complesso in quanto le dimensioni del log potrebbero raggiungere diversi gigabyte.<br /><br /> È inoltre possibile configurare il salvataggio automatico del file di log qualora il test di carico non risulti utile nel debug e nell'analisi dell'applicazione.|-   [Modifica delle impostazioni di registrazione dei test di carico](../test/modify-load-test-logging-settings.md)|