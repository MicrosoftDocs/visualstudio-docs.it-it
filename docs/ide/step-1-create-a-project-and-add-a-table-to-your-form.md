---
title: 'Passaggio 1: creare un progetto e aggiungere una tabella al form | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59afec50a1889b62e6115be44caa116b475a95c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Passaggio 1: creare un progetto e aggiungere una tabella al form
Il primo passaggio nella creazione di un gioco delle coppie consiste nel creare il progetto e aggiungere una tabella al form. La tabella consente di allineare le icone in una griglia ordinata 4x4. È inoltre possibile impostare diverse proprietà per migliorare l'aspetto della tavola da gioco.  
  
### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Per creare un progetto e aggiungere una tabella al form  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Se non si usa Visual Studio Express, occorre prima selezionare un linguaggio di programmazione. Nell'elenco **Modelli installati** scegliere **Visual C#** o **Visual Basic**.  
  
3.  Nell'elenco dei modelli di progetto scegliere **Applicazione Windows Form**, assegnare al progetto il nome **MatchingGame** e quindi scegliere il pulsante **OK**.  
  
4.  Nella finestra **Proprietà** impostare le proprietà del form seguenti.  
  
    1.  Modificare la proprietà **Text** del form da **Form1** a **Matching Game**. Questo testo viene visualizzato nella parte superiore della finestra del gioco.  
  
    2.  Impostare le dimensioni del form su 550 pixel di larghezza per 550 pixel di altezza. A tale scopo, impostare la proprietà **Size** su **550, 550** o trascinare l'angolo del form fino a raggiungere le dimensioni corrette nell'angolo inferiore destro dell'IDE (Integrated Development Environment).  
  
5.  Per visualizzare la casella degli strumenti, selezionare la scheda **Casella degli strumenti** sul lato sinistro dell'IDE.  
  
6.  Trascinare un controllo `TableLayoutPanel` dalla categoria **Contenitori** nella casella degli strumenti e quindi impostare le proprietà seguenti.  
  
    1.  Impostare la proprietà **BackColor** su **CornflowerBlue**. A tale scopo, aprire la finestra di dialogo **Colore sfondo** scegliendo la freccia a discesa accanto alla proprietà **BackColor** nella finestra **Proprietà**.  Quindi, scegliere la scheda **Web** nella finestra di dialogo **Colore sfondo** per visualizzare un elenco di nomi di colore disponibili.  
  
        > [!NOTE]
        >  I colori non sono in ordine alfabetico e CornflowerBlue è vicino alla fine dell'elenco.  
  
    2.  Impostare la proprietà **Dock** su **Fill** scegliendo il pulsante a discesa accanto alla proprietà, quindi il pulsante grande al centro. La tabella verrà espansa per includere l'intero form.  
  
    3.  Impostare la proprietà **CellBorderStyle** su **Inset**. Verranno creati bordi visivi tra ogni cella nella lavagna.  
  
    4.  Scegliere il pulsante triangolare nell'angolo superiore destro di TableLayoutPanel per visualizzarne il menu delle attività.  
  
    5.  Nel menu delle attività scegliere **Aggiungi riga** due volte per aggiungere altre due righe, quindi scegliere **Aggiungi colonna** due volte per aggiungere altre due colonne.  
  
    6.  Nel menu delle attività scegliere **Modifica righe e colonne** per aprire la finestra **Stili di riga e colonna**. Scegliere ognuna delle colonne, fare clic sul pulsante di opzione **%** e quindi impostare la larghezza di ogni colonna sul 25% della larghezza totale. Selezionare quindi **Righe** dalla casella a discesa nella parte superiore della finestra e impostare l'altezza di ogni riga su 25%. Al termine, scegliere il pulsante **OK**.  
  
     TableLayoutPanel dovrebbe essere ora costituito da una griglia 4x4 con sedici celle quadrate di dimensioni uguali. In queste righe e colonne appariranno in un secondo momento le immagini icona.  
  
7.  Accertarsi che TableLayoutPanel sia selezionato nell'editor del form. A tale scopo, verificare che **tableLayoutPanel1** sia visualizzato nella parte superiore della finestra **Proprietà**. Se non è già selezionato, scegliere TableLayoutPanel nel form oppure nel controllo a discesa nella parte superiore della finestra **Proprietà**.  
  
     Mentre TableLayoutPanel è selezionato, aprire la casella degli strumenti e aggiungere un controllo **Etichetta** (che si trova nella categoria **Controlli comuni**) alla cella superiore sinistra di TableLayoutPanel. Il controllo `Label` dovrebbe ora apparire selezionato nell'IDE. Impostare le proprietà indicate di seguito.  
  
    1.  Verificare che la proprietà **BackColor** dell'etichetta sia impostata su **CornflowerBlue**.  
  
    2.  Impostare la proprietà **AutoSize** su **False**.  
  
    3.  Impostare la proprietà **Dock** su **Fill**.  
  
    4.  Impostare la proprietà **TextAlign** su **MiddleCenter** scegliendo il pulsante a discesa accanto alla proprietà, quindi il pulsante al centro. In questo modo l'icona verrà visualizzata al centro della cella.  
  
    5.  Scegliere la proprietà **Font**. Verrà visualizzato un pulsante con i puntini di sospensione (...).  
  
    6.  Scegliere il pulsante con i puntini di sospensione e impostare **Tipo di carattere** su **Webdings**, **Stile** su **Grassetto** e **Dimensione** su **72**.  
  
    7.  Impostare la proprietà **Text** dell'etichetta sulla lettera **c**.  
  
         La cella superiore sinistra in TableLayoutPanel dovrebbe ora contenere un riquadro nero al centro su uno sfondo blu.  
  
        > [!NOTE]
        >  Il tipo di carattere Webdings include una serie di icone ed è fornito con il sistema operativo Windows. Nel gioco delle coppie, il giocatore deve riuscire ad accoppiare le icone, per cui si utilizza questo tipo di carattere per visualizzare le icone da accoppiare. Anziché inserire **c** nella proprietà **Text**, provare a immettere lettere diverse per vedere quali icone vengono visualizzate. Il punto esclamativo equivale a un ragno, la N maiuscola a un occhio e la virgola a un peperoncino.  
  
8.  Scegliere il controllo dell'etichetta e copiarlo nella cella successiva in TableLayoutPanel. Premere i tasti CTRL+C oppure scegliere **Modifica**, **Copia** nella barra dei menu. Quindi incollarlo Premere i tasti CTRL+V oppure scegliere **Modifica**, **Incolla** nella barra dei menu. Nella seconda cella di TableLayoutPanel verrà visualizzata una copia della prima etichetta. Incollarlo nuovamente: un'altra etichetta sarà visualizzata nella terza cella. Continuare a incollare controlli `Label` fino a riempire tutte le celle.  
  
    > [!NOTE]
    >  Se si incolla troppe volte, IDE aggiunge una nuova riga a TableLayoutPanel in modo da avere il posto per aggiungere il nuovo controllo etichetta. L'azione può essere annullata. Per rimuovere la nuova cella, premere i tasti CTRL+Z oppure scegliere **Modifica**, **Annulla** nella barra dei menu.  
  
     Ora il form è strutturato e deve apparire come l'immagine seguente.  
  
     ![Form iniziale del gioco di abbinamenti](../ide/media/express_tut4step1.png "Express_Tut4Step1")  
Form iniziale del gioco di abbinamenti  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 2: aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
-   Per tornare all'argomento introduttivo, vedere [Esercitazione 3: creare un gioco delle coppie](../ide/tutorial-3-create-a-matching-game.md).