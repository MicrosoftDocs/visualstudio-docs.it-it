---
title: Salvataggio dei log di test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 9ac88d8a-4777-462c-aa0e-244dadb2cfd1
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: d5c41f358ae3990b768014a97a8b1d27420359d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-how-frequently-test-logs-are-saved-using-the-load-test-editor"></a>Procedura: specificare la frequenza di salvataggio dei log di test tramite l'Editor test di carico

Dopo aver creato il test di carico usando la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà del test di carico in modo da soddisfare le necessità e gli obiettivi di test. Per altre informazioni, vedere [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md).

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni di esecuzione test e delle relative descrizioni, vedere [Proprietà delle impostazioni di esecuzione test di carico](../test/load-test-run-settings-properties.md).

È possibile specificare la frequenza di salvataggio del log di test in un test di carico usando l'Editor test di carico per modificare la proprietà **Frequenza di salvataggio del log per i test completati** nella finestra Proprietà.

## <a name="to-specify-the-frequency-for-saving-the-test-log-in-a-load-test"></a>Per specificare la frequenza di salvataggio del log di test in un test di carico

1.  Aprire un test di carico.

     Verrà visualizzato l'Editor test di carico. Nell'editor viene visualizzato l'albero del test di carico.

2.  Nella cartella **Impostazioni esecuzione test** dell'albero del test di carico scegliere il nodo delle impostazioni di esecuzione dei test per le quali si vuole specificare la frequenza di salvataggio del log di test.

3.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario verranno visualizzate nella finestra Proprietà.

4.  Nella casella di testo relativa alla proprietà **Frequenza di salvataggio del log per i test completati** digitare un numero per indicare la frequenza di scrittura del log di test. Il numero indica che nel log di test verrà salvato un test ogni numero di test corrispondente al numero immesso. Immettendo, ad esempio, il valore dieci, nel test di log vengono salvati il decimo, il ventesimo, il trentesimo test e così via.

    > [!NOTE]
    > Usando un valore 0 per la proprietà **Frequenza di salvataggio del log per i test completati** è possibile specificare che non deve essere salvato alcun log di test.

5.  Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**.

     È possibile visualizzare i dati salvati nel log utilizzando la visualizzazione Tabelle dell'analizzatore test di carico. Per altre informazioni, vedere [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Vedere anche

- [Modifica di uno scenario di test di carico](../test/edit-load-test-scenarios.md)
- [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md)
- [Modifica di uno scenario di test di carico](../test/edit-load-test-scenarios.md)
- [Procedura: Specificare se i test non superati vengono salvati in log di test](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)
- [Procedura: Configurare la raccolta di dettagli completi per abilitare il grafico attività utente virtuale](../test/how-to-configure-load-tests-to-collect-full-details.md)