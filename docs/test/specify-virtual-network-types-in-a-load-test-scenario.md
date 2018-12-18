---
title: Specifica dei tipi di rete virtuale in uno scenario di test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, adding networks
- load tests, removing networks
- load tests, virtual networks
- network mix
ms.assetid: 3c4f7874-081a-4ec4-9510-4d6d7d863a11
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: f40c1d26d1b8f28fd72bbcc5eb4842724e2d1e89
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Specificare i tipi di rete virtuale in uno scenario di test di carico

La *combinazione di reti* consente di simulare il carico in maniera più realistica in uno scenario di test di carico. Il carico viene generato usando una combinazione di reti eterogenea anziché un solo tipo di rete. Viene creata una maggiore approssimazione dell'interazione degli utenti finali con le applicazioni.

 Una combinazione di reti consente di specificare le probabilità che un utente virtuale esegua un determinato *profilo di rete*. Un profilo di rete è una simulazione di larghezza della banda della rete a livello dell'applicazione. Non viene simulata la latenza.

 Quando si crea un test di carico, è possibile simulare che il carico viene generato da uno o più tipi di connessione di reti. La combinazione di reti offre diversi tipi di rete. Le diverse reti sono simulate. Quando si sceglie un'opzione, ad esempio `Cable-DSL 1.5Mbps`, i tempi di attesa vengono inseriti nel test per simulare la larghezza di banda selezionata.

 La combinazione di reti ha le stesse modalità di altre opzioni di combinazioni. Un tipo di rete viene selezionato a caso e associato a un utente virtuale, in base alla combinazione di reti. I test di quell'utente vengono eseguiti utilizzando un determinato tipo di rete, in base alla probabilità specificata nella combinazione.

 Una volta specificata una combinazione di reti, sarà possibile aggiungere e rimuovere tipi di rete. È inoltre possibile cambiare la distribuzione della combinazione di reti utilizzando il controllo combinazione.

 Con il controllo combinazione è possibile regolare facilmente la distribuzione delle reti in uno scenario.

 Per altre informazioni, vedere [Informazioni sul controllo combinazione](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

## <a name="true-network-emulation"></a>Emulazione di rete reale

 Visual Studio usa l'emulazione di rete reale basata sul software per tutti i tipi di test, inclusi i test di carico. L'emulazione di rete reale simula le condizioni della rete tramite manipolazione diretta dei pacchetti di rete. L'emulatore di rete reale è in grado di emulare il comportamento di reti cablate e wireless tramite un collegamento fisico affidabile, ad esempio un cavo Ethernet. Gli attributi di rete seguenti sono incorporati nell'emulazione di rete reale:

-   Tempo di round trip nella rete (latenza)

-   Quantità di larghezza di banda disponibile

-   Comportamento di accodamento

-   Perdita di pacchetti

-   Riordinamento dei pacchetti

-   Propagazioni degli errori

L'emulazione di rete reale offre anche flessibilità di filtro dei pacchetti di rete in base agli indirizzi IP o ai protocolli, ad esempio TCP, UDP e ICMP.

L'emulazione di rete reale può essere utilizzata dai tester e dagli sviluppatori di applicazioni basate sulla rete per emulare un ambiente di test desiderato, valutare le prestazioni, stimare l'impatto delle modifiche o prendere decisioni relative all'ottimizzazione della tecnologia. Rispetto ai dispositivi di test hardware, l'emulazione di rete reale è una soluzione molto più economica e flessibile.

## <a name="to-add-new-networks-to-a-scenario"></a>Per aggiungere nuove reti a uno scenario

1.  Durante il processo di specifica della combinazione di reti per uno scenario, scegliere **Aggiungi**.

     Una nuova voce di rete verrà aggiunta alla griglia.

    > [!NOTE]
    > Per visualizzare la finestra di dialogo **Modifica combinazione di reti** fare clic con il pulsante destro del mouse su uno scenario esistente e quindi scegliere **Modifica combinazione di reti**.

2.  Nella colonna **Tipo rete** scegliere la freccia relativa alla nuova voce. Scegliere il tipo di rete desiderato.

3.  (Facoltativo) Modificare il controllo combinazione per specificare la distribuzione dei test. Per altre informazioni, vedere [Informazioni sul controllo combinazione](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4.  Al termine dell'aggiunta delle reti, scegliere **OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Per rimuovere reti da uno scenario

1.  Aprire un test di carico.

2.  Fare clic con il pulsante destro del mouse sullo scenario dal quale si intende rimuovere una rete e scegliere **Modifica combinazione di reti**. Verrà visualizzata la finestra di dialogo **Modifica combinazione di reti**.

3.  Selezionare la rete nella griglia e scegliere **Rimuovi**.

4.  (Facoltativo) Modificare il controllo combinazione per specificare la distribuzione dei test. Per altre informazioni, vedere [Informazioni sul controllo combinazione](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5.  Al termine della rimozione delle reti, scegliere **OK**.

## <a name="about-the-mix-control"></a>Informazioni sul controllo combinazione

 Con il controllo combinazione è possibile regolare la percentuale di carico distribuita tra test, tipi di browser o tipi di rete in uno scenario di test di carico. Per regolare i valori percentuali, spostare i dispositivi di scorrimento. Con la regolazione della combinazione di tipi di rete viene specificata la probabilità che un utente virtuale esegua un profilo di rete specifico in uno scenario di test di carico.

 Quando si sposta un dispositivo di scorrimento, i valori in percentuale di tutti gli elementi disponibili variano. Se gli elementi sono più di due, la quantità aggiunta o rimossa viene distribuita in modo uniforme tra gli altri elementi. È possibile eseguire l'override di questo comportamento. Se si seleziona la casella di controllo nella colonna del blocco per un particolare elemento, il valore percentuale specificato per tale elemento verrà bloccato. Quindi, quando si sposta un dispositivo di scorrimento, il quantità aggiunta o rimossa viene applicata solo agli eventuali elementi non bloccati rimanenti.

 Il pulsante **Distribuisci** viene usato per allocare uniformemente i valori percentuali tra tutti gli elementi. In presenza di tre elementi, ad esempio, se si sceglie **Distribuisci** le percentuali verranno impostate su 34, 33 e 33.

> [!WARNING]
> Il pulsante **Distribuisci** esegue l'override degli eventuali elementi bloccati.

 È anche possibile digitare direttamente i valori percentuali nella colonna **%** anziché usare i dispositivi di scorrimento. Se si immette direttamente un valore in percentuale, gli altri elementi non verranno regolati automaticamente.

> [!NOTE]
> I dispositivi di scorrimento sono disabilitati se il totale non è pari al 100% o se i valori immessi nella colonna **%** sono decimali.

Quando si immettono manualmente le percentuali, assicurarsi che la somma di tutti gli elementi sia 100%. Quando si salva una combinazione, se la somma non è pari al 100%, verrà richiesto di accettare i valori percentuali così come sono o di tornare indietro e regolarli. Se si sceglie di accettarle così come sono, le percentuali verranno ripartite proporzionalmente al 100%.  Se ad esempio si dispone di due elementi che sono stati impostati manualmente su 80% e 40%, il primo elemento verrà impostato su 66,67% (80 diviso 120) mentre il secondo su 33,33% (40 diviso 120).