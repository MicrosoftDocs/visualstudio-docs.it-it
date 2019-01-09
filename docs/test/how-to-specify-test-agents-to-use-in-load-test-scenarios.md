---
title: Specificare agenti di test da usare negli scenari di test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 1f6debabdb154e091a8021ccd998bb31d8f88d28
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932259"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Procedura: Specificare agenti di test da usare negli scenari di test di carico

Dopo aver creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test specifici.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Per un elenco completo delle proprietà degli scenari di test di carico e le relative descrizioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

Gli agenti vengono specificati usando l'**Editor test di carico** per modificare la proprietà **Agenti da utilizzare** nella finestra **Proprietà**.

È possibile specificare gli agenti che si desidera vengano utilizzati nello scenario se si utilizzano controller e agenti per eseguire il test di carico in modalità remota. È, ad esempio, possibile specificare un determinato set di agenti, in modo da garantire la coerenza quando si analizzano le tendenze delle prestazioni. Gli agenti possono inoltre essere distribuiti geograficamente, in modo che vi sia affinità tra gli script eseguiti e la posizione dell'agente.

> [!TIP]
> Anziché inserire fisicamente un agente nel sito remoto, è possibile utilizzare l'emulazione di rete per emulare una rete lenta. Per altre informazioni, vedere [Specificare i tipi di rete virtuale](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Per altre informazioni, vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

Un altro motivo è legato al fatto che in alcuni agenti, ma non in tutti, potrebbe essere installato software necessario per uno scenario specifico.

È possibile controllare la selezione degli agenti per un'esecuzione del test specifica utilizzando i ruoli nelle impostazioni di test. Per altre informazioni, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

Se nel computer di un agente di test l'utilizzo della CPU è oltre il 75% o se la quantità di memoria fisica disponibile è inferiore al 10%, aggiungere più agenti al test di carico per assicurarsi che il computer dell'agente non diventi il collo di bottiglia nel test di carico.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Per specificare gli agenti da utilizzare per uno scenario

1.  Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzato l'albero del test di carico.

2.  Nella cartella **Scenari** dell'albero del test di carico scegliere il nodo dello scenario per il quale specificare gli agenti da usare.

3.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario vengono visualizzate nella finestra **Proprietà**.

4.  Nella casella di testo per la proprietà **Agenti da utilizzare** digitare l'elenco di agenti da usare per lo scenario.

     Gli agenti devono essere separati da virgole, ad esempio "**Agent1, Agent2, Agent3**". Se si lascia vuota la proprietà, significa che nello scenario dovranno essere utilizzati tutti gli agenti disponibili.

    > [!NOTE]
    > La proprietà **Agenti da utilizzare** viene ignorata per le esecuzioni locali. Per le esecuzioni remote, se non esiste alcun agente specificato in **Agenti da utilizzare**, i test nello scenario non verranno eseguiti.

5.  Dopo aver modificato la proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Agenti da utilizzare**.

## <a name="see-also"></a>Vedere anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md)
- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)