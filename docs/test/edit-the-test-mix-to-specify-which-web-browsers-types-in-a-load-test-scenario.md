---
title: Combinazione di test dei browser per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: be0bd036c907f852028f6a9cccc798742e624184
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Modificare la combinazione di test per specificare quali tipi di Web browser includere in uno scenario di test di carico

La *combinazione di browser* consente di simulare il carico in maniera più realistica in uno scenario di test di carico. Il carico viene generato utilizzando una combinazione eterogenea di Web browser anziché un singolo Web browser. Viene quindi creata una migliore approssimazione dei Web browser che saranno utilizzati nelle applicazioni.

 Una combinazione di browser consente di specificare la probabilità che un utente virtuale esegua un determinato tipo di Web browser in uno scenario di test di carico. Quando si crea un test di carico, è possibile simulare che il carico venga generato da uno o più Web browser. Quando si aggiunge un tipo di Web browser alla combinazione dal set di Web browser forniti, a ciascuna richiesta HTTP inoltrata da un test delle prestazioni Web viene aggiunto un set di intestazioni associate relative ai Web browser selezionati.

 La combinazione di browser ha le stesse modalità di altre opzioni di combinazioni. Un tipo di Web browser viene casualmente associato a un utente virtuale, in base alla combinazione di browser. I test di tale utente vengono eseguiti in un determinato Web browser, in base alla probabilità specificata nella combinazione.

 Una volta specificata una combinazione di browser, sarà possibile in seguito aggiungere e rimuovere tipi di Web browser dalla combinazione. È inoltre possibile cambiare la distribuzione della combinazione di browser utilizzando il controllo combinazione. Il controllo combinazione consente di regolare facilmente la distribuzione dei browser in uno scenario.

## <a name="adding-new-browsers-to-a-scenario"></a>Aggiunta di nuovi browser a uno scenario

### <a name="to-add-new-browsers-to-a-scenario"></a>Per aggiungere nuovi browser a uno scenario

1.  Durante il processo di specifica della combinazione di browser per uno scenario, scegliere **Aggiungi**.

     Una nuova voce di browser verrà aggiunta alla griglia.

    > [!NOTE]
    > Per visualizzare la finestra di dialogo **Modifica combinazioni di browser**, fare clic con il pulsante destro del mouse su uno scenario esistente e quindi scegliere **Modifica combinazioni di browser**.

2.  Nella colonna **Tipo browser** scegliere la freccia relativa alla nuova voce, quindi scegliere il tipo di browser desiderato.

3.  (Facoltativo) Modificare il controllo combinazione per specificare la distribuzione dei test.

4.  Al termine dell'aggiunta dei browser, scegliere **OK**.

##  <a name="EditingTestMixSpecifyBrowserRemovingBrowserTypes"></a> Rimozione di browser da uno scenario

### <a name="to-remove-browsers-from-a-scenario"></a>Per rimuovere browser da uno scenario

1.  Aprire un test di carico.

2.  Fare clic con il pulsante destro del mouse sullo scenario dal quale si vuole rimuovere un browser e scegliere **Modifica combinazioni di browser**.

     Verrà visualizzata la finestra di dialogo **Modifica combinazioni di browser**.

3.  Selezionare il browser nella griglia e scegliere **Rimuovi**.

4.  (Facoltativo) Modificare il controllo combinazione per specificare la distribuzione dei test.

5.  Al termine della rimozione dei browser, scegliere **OK**.

## <a name="about-the-mix-control"></a>Informazioni sul controllo combinazione

 Il controllo Mix consente di regolare la percentuale di carico distribuita tra test, tipi di browser o tipi di rete in uno scenario di test di carico. I valori percentuali vengono modificati spostando i dispositivi di scorrimento. Con la regolazione della combinazione dei tipi di browser si specifica la probabilità che un utente virtuale esegua un determinato tipo di browser in uno scenario di test di carico.

 Quando si sposta un dispositivo di scorrimento, i valori in percentuale di tutti gli elementi disponibili variano. Se gli elementi sono più di due, la quantità aggiunta o rimossa viene distribuita in modo uniforme tra gli altri elementi. È possibile eseguire l'override di questo comportamento. Se si seleziona la casella di controllo nella colonna del blocco per un particolare elemento, il valore percentuale specificato per tale elemento verrà bloccato. Quindi, quando si sposta un dispositivo di scorrimento, il quantità aggiunta o rimossa viene applicata solo agli eventuali elementi non bloccati rimanenti.

 Il pulsante **Distribuisci** viene usato per allocare uniformemente i valori percentuali tra tutti gli elementi. In presenza di tre elementi, ad esempio, se si sceglie **Distribuisci** le percentuali verranno impostate su 34, 33 e 33.

> [!WARNING]
> Il pulsante **Distribuisci** esegue l'override degli eventuali elementi bloccati.

 È anche possibile digitare direttamente i valori percentuali nella colonna **%** anziché usare i dispositivi di scorrimento. Se si immette direttamente un valore in percentuale, gli altri elementi non verranno regolati automaticamente.

> [!NOTE]
> I dispositivi di scorrimento sono disabilitati se il totale non è pari al 100% o se i valori immessi nella colonna **%** sono decimali.

 Quando si immettono manualmente le percentuali, assicurarsi che la somma di tutti gli elementi sia 100%. Quando si salva una combinazione, se la somma non è pari al 100%, verrà richiesto di accettare i valori percentuali così come sono o di tornare indietro e regolarli. Se si sceglie di accettarle così come sono, le percentuali verranno ripartite proporzionalmente al 100%.  Se ad esempio si dispone di due elementi che sono stati impostati manualmente su 80% e 40%, il primo elemento verrà impostato su 66,67% (80 diviso 120) mentre il secondo su 33,33% (40 diviso 120).

## <a name="see-also"></a>Vedere anche

- [Modifica di uno scenario di test di carico](../test/edit-load-test-scenarios.md)