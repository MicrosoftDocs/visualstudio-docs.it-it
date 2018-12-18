---
title: Personalizzazione dell'IDE
description: È possibile personalizzare Visual Studio per Mac in diversi modi, consentendo agli utenti di sviluppare app in un ambiente in grado di soddisfare sia le esigenze di efficienza che quelle estetiche. Questo argomento esamina i diversi modi in cui è possibile adattare Visual Studio per Mac alle proprie esigenze.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.openlocfilehash: 5139f166c23f91c3c9f4174860ed8dd6fa883240
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-the-ide"></a>Personalizzazione dell'IDE

È possibile personalizzare Visual Studio per Mac in diversi modi, consentendo agli utenti di sviluppare app in un ambiente in grado di soddisfare sia le esigenze di efficienza che quelle estetiche. Questo articolo esamina i diversi modi in cui è possibile adattare Visual Studio per Mac alle proprie esigenze.

## <a name="dark-theme"></a>Tema scuro

![Visualizzazione tema scuro](media/customizing-the-ide-image7a.png)

Per cambiare tema in Visual Studio per Mac, scegliere **Visual Studio > Preferenze > Ambiente > Stile di visualizzazione** e selezionare il tema desiderato nell'elenco a discesa **Tema dell'interfaccia utente**, come illustrato nell'immagine seguente:

 ![Selezione del tema scuro](media/customizing-the-ide-image7b.png)

## <a name="localization"></a>Localizzazione

Visual Studio per Mac è disponibile nelle 13 lingue seguenti ed è quindi accessibile a un maggior numero di sviluppatori:

* Cinese (Cina)
* Cinese (Taiwan)
* Ceco
* Francese
* Tedesco
* Inglese
* Italiano
* Giapponese
* Coreano
* Portoghese (Brasile)
* Russo
* Spagnolo
* Turco

Per cambiare la lingua visualizzata da Visual Studio per Mac, scegliere **Visual Studio > Preferenze > Ambiente > Stile di visualizzazione** e selezionare la lingua desiderata nell'elenco a discesa **Lingua dell'interfaccia utente**, come illustrato nell'immagine seguente:


![Selezione lingua](media/customizing-the-ide-image11a.png)

## <a name="author-information"></a>Informazioni sull'autore

Il pannello Informazioni sull'autore consente all'utente di aggiungere informazioni personali pertinenti manualmente, ad esempio il nome, l'indirizzo di posta elettronica, il titolare del copyright per il lavoro, la società e il marchio:

 ![Sezione di modifica delle informazioni sull'autore](media/customizing-the-ide-image9a.png)

Queste informazioni vengono usate per popolare le intestazioni standard dei file, ad esempio le licenze, che è possibile aggiungere ai nuovi file:

 ![Opzioni per le intestazioni standard](media/customizing-the-ide-image8a.png)


I campi **Nome** e **Posta elettronica** vengono usati in tutti i commit eseguiti tramite il controllo della versione in Visual Studio per Mac. Se questi campi non sono popolati, Visual Studio per Mac chiede di farlo quando si tenta di usare il controllo della versione.

## <a name="key-bindings"></a>Tasti di scelta rapida

I tasti di scelta rapida consentono di adattare l'ambiente di sviluppo in modo da rendere più efficienti gli spostamenti all'interno di Visual Studio per Mac. Sono disponibili tasti di scelta rapida familiari presenti nelle interfacce IDE più diffuse, ad esempio Visual Studio (Windows), ReSharper, Visual Studio Code e Xcode.

Per impostare tasti di scelta rapida, passare a **Visual Studio > Preferenze > Ambiente > Tasti di scelta rapida**, come illustrato nell'immagine seguente:

 ![Impostare tasti di scelta rapida](media/customizing-the-ide-image10a.png)

Da qui è possibile cercare combinazioni di tasti di scelta rapida, visualizzare tasti di scelta rapida in conflitto, aggiungere nuovi tasti di scelta rapida e modificare quelli esistenti.

## <a name="workspace-layout"></a>Layout area di lavoro

L'area di lavoro di Visual Studio per Mac è costituita da un'area principale (in genere l'editor, l'area di progettazione o il file di opzioni), circondata da *riquadri* liberi che contengono informazioni utili per l'accesso ai file, al test e al debug dell'applicazione e per la gestione di questi.

 ![Layout area di lavoro](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-pads"></a>Visualizzazione e organizzazione dei riquadri

Quando si apre una nuova soluzione o un nuovo file in Visual Studio per Mac, è possibile notare la presenza nell'area di lavoro di alcuni *riquadri*, ad esempio Soluzione, Struttura documento ed Errori:

![Riquadri della soluzione](media/customizing-the-ide-image2a.png)

Visual Studio per Mac offre alcuni riquadri contenenti informazioni e strumenti di lavoro e di esplorazione aggiuntivi. Per accedere a questi riquadri, scegliere **Vista > Riquadri** e selezionare il riquadro da aggiungere:

 ![Selezionare un nuovo riquadro](media/customizing-the-ide-image3a.png)

È anche possibile aprire i riquadri automaticamente tramite vari comandi, ad esempio **Cerca nei file** (Maiusc + Cmd + F), che apre un riquadro scollegato di risultati della ricerca.

I riquadri possono essere spostati e disposti in tutto il flusso di lavoro nel modo più utile per l'utente. Ad esempio, possono essere ancorati a qualsiasi lato dell'editor di documenti, posizionati accanto, sopra o sotto altri riquadri o impostati come set di riquadri a schede, per consentire di passare rapidamente dall'uno all'altro.

I riquadri usati di frequente possono anche essere completamente scollegati dalla finestra di Visual Studio per Mac e inseriti in una finestra separata.

È possibile nascondere e chiudere i riquadri tramite i pulsanti nell'angolo superiore destro di ogni riquadro:

![Nascondere e chiudere riquadri](media/customizing-the-ide-image5a.png)

I riquadri nascosti automaticamente sono ancorati ai lati dell'area di lavoro. Sono quindi facilmente accessibili quando necessario. Quando si posiziona il mouse su un riquadro nascosto, questo viene visualizzato nuovamente e viene nascosto quando lo stato attivo viene spostato altrove tramite il mouse o la tastiera.


### <a name="organizing-layouts"></a>Organizzazione dei layout

I riquadri costantemente visualizzati variano a seconda del contesto. Se si usa la finestra di progettazione visiva, ad esempio, i riquadri casella degli strumenti e griglia delle proprietà sono i più importanti, mentre durante il debug i riquadri del debugger sono utili per visualizzare lo stack e le variabili locali.

Lo stato dei riquadri aperti è rappresentato da un *layout*. È possibile passare da un layout a un altro manualmente tramite il menu Vista, come illustrato nell'immagine seguente, o automaticamente quando si esegue un'azione, ad esempio il debug o l'apertura di uno storyboard:

![Selezione di nuovi layout](media/customizing-the-ide-image6b.png)

C'è sempre un layout attivo e qualsiasi modifica eseguita in un layout, ad esempio l'aggiunta o il riposizionamento di un riquadro, modifica solo il layout attivo. Quando si esce da Visual Studio per Mac, le modifiche apportate non vengono salvate.


È tuttavia possibile creare un nuovo layout tramite la voce di menu **Vista > Salva Layout**. Il layout corrente verrà aggiunto al menu e sarà possibile selezionarlo in qualsiasi momento:

![Salva layout corrente](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>Supporto della modifica affiancata

Visual Studio per Mac consente di affiancare diversi editor di testo aperti o di visualizzare un editor in una finestra mobile scollegata.

È possibile abilitare la modalità a due colonne tramite la voce di menu Vista selezionando **Vista > Colonne editor > Due colonne** o trascinando una scheda dell'editor su uno dei bordi dell'area dell'editor:

 ![Modalità due colonne affiancate](media/customizing-the-ide-sbs.png)

Le schede dell'editor possono essere trascinate fuori dall'area del documento per creare una finestra dell'editor mobile. Anche la finestra mobile supporta editor affiancati e può contenere diverse schede dell'editor:

 ![Creare una nuova finestra](media/customizing-the-ide-sbs1.png)

 ![Due colonne affiancate con schede aggiuntive](media/customizing-the-ide-sbs2.png)

Per tornare a un solo editor aperto, selezionare **Vista > Colonne editor > Una colonna**.
