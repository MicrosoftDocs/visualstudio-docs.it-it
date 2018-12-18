---
title: "Procedura: Specificare la frequenza di campionamento per un'impostazione di esecuzione test di carico in Visual Studio | Microsoft Docs"
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: ece9a2d6842caa82ec8eb79721bb678b562b95e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Procedura: specificare la frequenza di campionamento per un'impostazione di esecuzione test di carico

Dopo aver creato il test di carico usando la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà in modo da soddisfare le necessità e gli obiettivi di test.

Usando l'**Editor test di carico** è possibile modificare il valore della proprietà **Frequenza di campionamento** dell'impostazione di esecuzione test nella finestra **Proprietà**. Per un elenco completo delle proprietà delle impostazioni di esecuzione test e delle relative descrizioni, vedere [Proprietà delle impostazioni di esecuzione test di carico](../test/load-test-run-settings-properties.md).

Scegliere un valore appropriato per la proprietà **Frequenza di campionamento** per l'impostazione di esecuzione test di carico in base alla lunghezza del test di carico. Una frequenza di campionamento inferiore, ad esempio il valore predefinito di cinque secondi, richiede più spazio nel database dei risultati del test di carico. Per i test di carico più lunghi, l'aumento della frequenza di campionamento riduce la quantità di dati raccolti. Per altre informazioni, vedere [Procedura: Specificare la frequenza di campionamento per un'impostazione esecuzione test di carico](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Di seguito sono riportate alcune linee guida per le frequenze di campionamento:

|Durata test di carico|Frequenza di campionamento consigliata|
|------------------------|-----------------------------|
|\< 1 ora|5 secondi|
|1 - 8 ore|15 secondi|
|8 - 24 ore|30 secondi|
|> 24 ore|60 secondi|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Per specificare frequenza di campionamento del contatore delle prestazioni in un'impostazione esecuzione test

1.  Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzato l'albero del test di carico.

2.  Nella cartella **Impostazioni esecuzione test** dell'albero del test di carico scegliere le impostazioni esecuzione test per cui si vuole specificare la frequenza di campionamento.

3.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà delle impostazioni esecuzione test di carico verranno visualizzate nella finestra Proprietà.

4.  Nella proprietà **Frequenza di campionamento** immettere un valore che indica la frequenza alla quale il test di carico raccoglierà dati del contatore delle prestazioni.

5.  Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Frequenza di campionamento**.

## <a name="see-also"></a>Vedere anche

- [Configurazione delle impostazioni esecuzione test di carico](../test/configure-load-test-run-settings.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)