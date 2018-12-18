---
title: Specificare la percentuale di utenti virtuali che usano i dati della cache Web per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 76d611af76877a9638ed2815a7d8dc5f77e45c8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Procedura: specificare la percentuale di utenti virtuali che utilizzano i dati della cache Web

Dopo avere creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test. Per un elenco completo delle proprietà di scenari dei test di carico e delle relative descrizioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

La proprietà **Percentuale di nuovi utenti** viene impostata nella finestra Proprietà. Le proprietà degli scenari dei test di carico vengono modificate tramite l'Editor test di carico.

La proprietà **Percentuale di nuovi utenti** influisce sul modo in cui il test di carico simula la memorizzazione nella cache che verrebbe eseguita da un Web browser. Per impostazione predefinita, la proprietà **Percentuale di nuovi utenti** è impostata su 0%. Se il valore della proprietà **Percentuale di nuovi utenti** è impostato su 100%, ogni esecuzione dei test prestazioni Web in un test di carico viene considerata come un nuovo utente del sito Web, che non dispone nella cache del browser di alcun contenuto del sito Web ottenuto con visite precedenti. Vengono pertanto scaricate tutte le richieste del test Web, comprese tutte le richieste dipendenti come le immagini.

> [!NOTE]
> Quando la stessa risorsa memorizzabile nella cache viene richiesta più volte in un test Web, le richieste non vengono scaricate.

Se si esegue il test di carico di un sito Web caratterizzato da un numero significativo di utenti che tornano a visitarlo e che probabilmente hanno immagini e altro contenuto memorizzati nella cache locale, l'impostazione del 100% per la proprietà **Percentuale di nuovi utenti** genererà più richieste di download rispetto a quelle che potrebbero verificarsi nell'utilizzo reale. In questo caso, è necessario stimare la percentuale di visite effettuate da utenti che visitano per la prima volta il sito Web e impostare di conseguenza la proprietà **Percentuale di nuovi utenti**.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Per specificare gli agenti da utilizzare per uno scenario

1.  Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzato l'albero del test di carico.

2.  Nella cartella **Scenari** dell'albero del test di carico scegliere il nodo dello scenario per il quale specificare gli agenti da usare.

3.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario verranno visualizzate nella finestra Proprietà.

4.  Impostare il valore per la proprietà **Percentuale di nuovi utenti** immettendo un numero per la percentuale.

5.  Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore della proprietà **Percentuale di nuovi utenti**.

## <a name="see-also"></a>Vedere anche

- [Modifica di uno scenario di test di carico](../test/edit-load-test-scenarios.md)
- [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md)
- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
- [Modifica dei modelli di carico per modellare le attività utente virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md)