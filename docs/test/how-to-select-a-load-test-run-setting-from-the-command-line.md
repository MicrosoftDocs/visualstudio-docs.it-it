---
title: Selezionare le impostazioni di esecuzione test di carico di Visual Studio dalla riga di comando | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: f5a45733da51f98618b4af36a0be0ea9120837ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Procedura: selezionare un'impostazione di esecuzione test di carico dalla riga di comando

In un test di carico possono essere contenute una o più *impostazioni esecuzione test*, ovvero un set di proprietà che determinano la modalità di esecuzione del test di carico. Sono organizzate in categorie nella finestra Proprietà. Quando si esegue un test di carico, viene utilizzata l'impostazione esecuzione test impostata correntemente come attiva.

 Se nel test di carico è contenuta un'unica impostazione esecuzione test, si tratta sempre del nodo attivo. Se nel test di carico sono contenuti più nodi di impostazioni esecuzione test, è possibile selezionare quello da utilizzare per l'esecuzione di un test di carico dalla riga di comando. Vedere [Procedura: Aggiungere impostazioni di esecuzione a un test di carico](../test/how-to-add-additional-run-settings-to-a-load-test.md).

## <a name="to-change-the-run-setting-from-the-command-line"></a>Per modificare l'impostazione esecuzione test dalla riga di comando

1.  Se si vuole usare impostazioni esecuzione test diverse dalla riga di comando per sfruttare la strategia dei parametri di contesto, usare il comando seguente:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2.  Eseguire il test di carico utilizzando mstest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Vedere anche

- [Configurazione delle impostazioni esecuzione test di carico](../test/configure-load-test-run-settings.md)
- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Procedura: Aggiungere altre impostazioni esecuzione test a un test di carico](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Procedura: Selezionare l'impostazione di esecuzione test attiva per un test di carico](../test/how-to-select-the-active-run-setting-for-a-load-test.md)