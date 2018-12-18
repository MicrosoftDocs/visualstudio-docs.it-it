---
title: Aggiungere impostazioni di esecuzione a un test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: ff4a023f7bed6e182c6807b68a1ed918aee034df
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Procedura: aggiungere ulteriori impostazioni di esecuzione test a un test di carico

Le impostazioni esecuzione test di un test di carico determinano una varietà di altre impostazioni, tra cui la durata del test, il livello di dettaglio dell'insieme dei risultati e gli insiemi di contatori raccolti durante le esecuzioni dei test. È possibile creare e archiviare più impostazioni di esecuzione per ogni test di carico e selezionare una determinata impostazioni da usare durante l'esecuzione del test. Quando si crea un test di carico utilizzando la Creazione guidata test di carico, al test viene aggiunta un'impostazione esecuzione test iniziale.

 È possibile aggiungere altre impostazioni di esecuzione al test di carico con impostazioni di proprietà differenti, per poter eseguire il test di carico con condizioni diverse. Ad esempio, è possibile aggiungere una nuova impostazione test e usare una frequenza di campionamento diversa o specificare una durata dell'esecuzione più lunga. È possibile utilizzare una sola impostazione esecuzione test per volta ed è necessario specificare quale impostazione esecuzione test utilizzare contrassegnandola come attiva.

## <a name="to-add-another-run-setting"></a>Per aggiungere un'ulteriore impostazione di esecuzione

1.  Aprire un test di carico.

2.  (Facoltativo) Espandere la cartella **Impostazioni di esecuzione**.

3.  Fare clic con il pulsante destro del mouse sulla cartella **Impostazioni di esecuzione** e scegliere **Aggiungi impostazione di esecuzione**.

     Viene aggiunta una nuova impostazione di esecuzione alla cartella **Impostazioni di esecuzione**.

4.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Verrà visualizzata la Finestra Proprietà con le proprietà relative all'impostazione di esecuzione selezionata.

5.  Nella finestra Proprietà usare la casella di testo relativa alla proprietà **Nome** per assegnare alla nuova impostazione esecuzione test un nome che ne descriva lo scopo, ad esempio **Impostazione esecuzione test: Esecuzione in cinque minuti**.

6.  Utilizzare la Finestra Proprietà per modificare le impostazioni di esecuzione. Modificare, ad esempio, la durata dell'esecuzione in **00:05:00** per eseguire il test per cinque minuti.

    > [!NOTE]
    > Per un elenco completo delle proprietà delle impostazioni esecuzione test e delle relative descrizioni, vedere [Proprietà delle impostazioni esecuzione test di carico](../test/load-test-run-settings-properties.md).

     A questo punto è possibile specificare che si desidera utilizzare l'impostazione esecuzione test aggiunta impostandola su attiva. Per altre informazioni, vedere [Procedura: Selezionare l'impostazione di esecuzione test attiva per un test di carico](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Vedere anche

- [Configurazione delle impostazioni esecuzione test di carico](../test/configure-load-test-run-settings.md)
- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)