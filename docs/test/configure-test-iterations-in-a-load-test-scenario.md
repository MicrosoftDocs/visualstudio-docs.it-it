---
title: Configurazione delle iterazioni di test per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, sceanrios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6aac1f950bcfaf4c8308913d389d6fd3dec15c2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Configurare le iterazioni di test in uno scenario di test di carico

Per configurare le impostazioni delle iterazioni del test, modificare uno scenario di test di carico usando l'Editor test di carico e la finestra Proprietà. Per impostazione predefinita, un scenario di test di carico viene configurato senza specificare il numero massimo di iterazioni. Si ha l'opzione di configurare il numero massimo di iterazioni nello scenario e l'intervallo tra un'iterazione e l'altra.

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Specificare il numero massimo di iterazioni di test per uno scenario

È possibile specificare il numero massimo di volte che si vuole eseguire i test per uno scenario usando l'Editor test di carico per modificare la proprietà **Numero massimo di iterazioni test** nella finestra Proprietà.

La proprietà **Numero massimo di iterazioni test** controlla il numero massimo di iterazioni di test da eseguire per lo scenario. Analogamente alla proprietà **Iterazioni test** nelle impostazioni di esecuzione del test di carico, si tratta del numero massimo per tutti gli utenti in tutti gli agenti, non di un'impostazione per utente.

> [!NOTE]
> Per un elenco completo delle proprietà di scenari dei test di carico e delle relative descrizioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

 Per una combinazione di test sequenziale, un'iterazione è un passaggio in tutti i test nella combinazione. Per tutte le altre combinazioni di test, ogni esecuzione del test rappresenta un'iterazione. Per altre informazioni, vedere [Informazioni sul controllo combinazione](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

 Se il test di carico è basato sulla durata e tale durata scade prima del completamento del conteggio delle iterazioni, il test si arresterà. Se il test è basato sull'iterazione e le iterazioni di test vengono soddisfatte prima di quelle dello scenario, il test si arresterà. La durata viene configurata tramite la proprietà **Durata esecuzione** nella finestra Proprietà associata a un'impostazione di esecuzione in un test di carico.

 Quando viene soddisfatto il conteggio delle iterazioni dello scenario, l'esecuzione dello scenario verrà arrestata ma qualsiasi altro scenario attivo continuerà a essere eseguito.

> [!NOTE]
> Una proprietà correlata è la proprietà **Univoco** in un'origine dati del test Web, che comporta lo spostamento sequenziale nei dati, riga per riga, ma una sola volta per ogni record. Per altre informazioni, vedere [Aggiungere un'origine dati a un test prestazioni Web](../test/add-a-data-source-to-a-web-performance-test.md).

 La proprietà **Numero massimo di iterazioni test** è utile in diverse situazioni. Alcuni tester che si occupano di test di carico preferiscono eseguire test basati sulle iterazioni, mentre altri preferiscono i test basati sulla durata.

 ![Specifica delle iterazioni di test in uno scenario](../test/media/loadtest_prop.png "LoadTest_Prop")

### <a name="to-specify-the-maximum-test-iterations"></a>Per specificare il numero massimo di iterazioni di test

1.  Aprire un test di carico.

2.  Verrà visualizzato l'Editor test di carico. Verrà visualizzato l'albero del test di carico.

3.  Nella cartella **Scenari** dell'albero del test di carico scegliere il nodo dello scenario per il quale si vuole specificare il numero massimo di iterazioni di test.

4.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario verranno visualizzate nella finestra Proprietà.

5.  Nella casella di testo per la proprietà **Numero massimo di iterazioni test** digitare un valore che indica il numero massimo di test da eseguire per lo scenario quando viene eseguito il test di carico.

    > [!NOTE]
    > L'uso di un valore 0 per la proprietà **Numero massimo di iterazioni test** consente di specificare che non è previsto un numero massimo di interazioni.

6.  Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Numero massimo di iterazioni test**.

## <a name="specifying-think-times-between-test-iterations-for-a-scenario"></a>Specifica del tempo di interazione utente tra iterazioni di test in uno scenario

La proprietà **Tempo interazione utente tra due iterazioni test** viene impostata usando la finestra Proprietà durante la modifica delle proprietà dello scenario del test di carico nell'Editor test di carico.

La proprietà **Tempo interazione utente tra due iterazioni test** viene usata per specificare il numero di secondi di attesa prima di avviare un'iterazione test.

> [!NOTE]
> Per un elenco completo delle proprietà relative agli scenari dei test di carico e delle relative descrizioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-times-between-test-iterations"></a>Per specificare il tempo di interazione utente tra iterazioni di test

1.  Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzato l'albero del test di carico.

2.  Nella cartella **Scenari** dell'albero del test di carico scegliere il nodo dello scenario per il quale si vuole specificare gli agenti da usare.

3.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario verranno visualizzate nella finestra Proprietà.

4.  Per il valore della proprietà **Tempo interazione utente tra due iterazioni test**, immettere un numero che rappresenta il numero di secondi di attesa prima di avviare l'iterazione test successiva.

5.  Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Tempo iterazione utente tra due iterazioni test**.

## <a name="see-also"></a>Vedere anche

- [Modifica di uno scenario di test di carico](../test/edit-load-test-scenarios.md)
- [Configurare agenti di test e test controller per i test di carico](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
- [Modifica dei tempi interazione utente per simulare i ritardi di interazione umana con i siti Web](../test/edit-think-times-in-load-test-scenarios.md)