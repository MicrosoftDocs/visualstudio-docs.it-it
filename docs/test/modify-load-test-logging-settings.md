---
title: Impostazioni di registrazione dei test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 7f33d25f471e683a50fd37eab669917a319cf60a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="modify-load-test-logging-settings"></a>Modificare le impostazioni di registrazione dei test di carico

I risultati relativi al test di carico completato contengono gli esempi di contatori delle prestazioni e le informazioni sugli errori raccolti in un log periodicamente dai computer sottoposti a test. Nel corso dell'esecuzione di un test di carico può essere raccolto un numero elevato di esempi di contatori delle prestazioni. La quantità di dati sulle prestazioni raccolti durante un test di carico dipende dalla durata dell'esecuzione del test, dall'intervallo di campionamento, dal numero di computer sottoposti a test e dal numero di contatori da raccogliere. Per un test di carico di grandi dimensioni, la quantità raccolta di dati relativi alle prestazioni può facilmente raggiungere diversi gigabyte; considerare pertanto di modificare la frequenza di salvataggio dei dati nel log. Vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

Durante l'esecuzione del test di carico, il *test controller* effettua lo spooling di tutti i dati di esempio del test di carico raccolti in un log di database. Dopo il completamento del test, nel database vengono caricati dati aggiuntivi quali dettagli sugli errori e di intervallo.

|Attività|Argomenti correlati|
|----------|-----------------------|
|**Specificare la frequenza di salvataggio dei log durante l'esecuzione di un test di carico:** è possibile specificare la frequenza di salvataggio del log di test quando viene eseguito il test di carico.|-   [Procedura: Specificare la frequenza di salvataggio dei log di test](../test/how-to-specify-how-frequently-test-logs-are-saved.md)|
|**Salvare i log se un test di carico non riesce:** è possibile specificare se si vuole salvare il log di test quando un test di carico non riesce.|-   [Procedura: Specificare se i test non superati vengono salvati in log di test](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Impostare le dimensioni massime per il file di log:** è possibile modificare il file di configurazione XML associato al servizio del test controller per specificare le dimensioni massime da usare per il file di log.|[Procedura: Impostare la dimensione massima per il file di log](../test/how-to-specify-the-maximum-size-for-the-log-file.md)|

## <a name="related-tasks"></a>Attività correlate

Una proprietà correlata è **Intervallo archiviazione dettagli**. Per altre informazioni, vedere [Procedura: Configurare la raccolta di dettagli completi per abilitare il grafico attività utente virtuale](../test/how-to-configure-load-tests-to-collect-full-details.md).

## <a name="see-also"></a>Vedere anche

- [Configurazione delle impostazioni esecuzione test di carico](../test/configure-load-test-run-settings.md)