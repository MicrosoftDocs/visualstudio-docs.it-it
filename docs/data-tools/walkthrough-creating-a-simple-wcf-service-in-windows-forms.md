---
title: 'Procedura dettagliata: Creazione di un semplice servizio WCF in Windows Form'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 466cd777a52455207cddf6dd88a714a02624e3a3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Procedura dettagliata: Creazione di un semplice servizio WCF in Windows Form
In questa procedura dettagliata viene illustrato come creare un semplice servizio [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], testarlo e accedervi da un'applicazione Windows Form.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="creating-the-service"></a>Creazione del servizio

#### <a name="to-create-a-wcf-service"></a>Per creare un servizio WCF

1.  Scegliere **Nuovo** dal menu **File** , quindi scegliere **Progetto**.

2.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual Basic** o **Visual c#** nodo e fare clic su **WCF**, seguito da **WCF Libreria del servizio**. Fare clic su **OK** per aprire il progetto.

     ![Il progetto libreria di servizi WCF](../data-tools/media/wcf1.PNG "wcf1")

    > [!NOTE]
    >  Viene creato un servizio di lavoro che può essere testato e a cui è possibile accedere. I due passaggi seguenti mostrano come modificare il metodo predefinito per usare un tipo di dati diverso. In un'applicazione reale verrebbero aggiunte anche le funzioni dell'utente al servizio.

3.  ![Il file IService1](../data-tools/media/wcf2.png "wcf2")

     In **Esplora**, fare doppio clic su IService1. vb o IService1.cs, quindi trovare la riga seguente:

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Modificare il tipo per il `value` parametro stringa:

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     Nel codice precedente annotare gli attributi `<OperationContract()>` o `[OperationContract]`. Questi attributi sono richiesti per tutti i metodi esposti dal servizio.

4.  ![Il file Service1](../data-tools/media/wcf3.png "wcf3")

     In **Esplora**, fare doppio clic su Service1. vb o Service1.cs, quindi trovare la riga seguente:

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Modifica del tipo per il parametro del valore stringa:

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="testing-the-service"></a>Test del servizio

#### <a name="to-test-a-wcf-service"></a>Per testare un servizio WCF

1.  Premere **F5** per eseguire il servizio. Oggetto **Client di prova WCF** verrà visualizzato il modulo e il servizio verrà caricato.

2.  Nel **Client di prova WCF** form fare doppio clic su di **GetData ()** metodo sottoposto a **IService1**. Il **GetData** verrà visualizzata la scheda.

     ![Il metodo GetData&#40; &#41; metodo](../data-tools/media/wcf4.png "wcf4")

3.  Nel **richiesta** , quindi selezionare il **valore** campo e tipo `Hello`.

     ![Il campo del valore](../data-tools/media/wcf5.png "wcf5")

4.  Fare clic su di **Invoke** pulsante. Se un **avviso di sicurezza** viene visualizzata la finestra di dialogo, fare clic su **OK**. Il risultato verrà visualizzato nella **risposta** casella.

     ![Il risultato nella casella risposta](../data-tools/media/wcf6.png "wcf6")

5.  Nel **File** menu, fare clic su **uscita** per chiudere il form di test.

## <a name="accessing-the-service"></a>Accesso al servizio

#### <a name="to-reference-a-wcf-service"></a>Per fare riferimento a un servizio WCF

1.  Nel **File** dal menu **Aggiungi** e quindi fare clic su **nuovo progetto**.

2.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual Basic** o **Visual c#** nodo e selezionare **Windows**, quindi selezionare **Applicazione Windows Form**. Fare clic su **OK** per aprire il progetto.

     ![Progetto applicazione Windows Forms](../data-tools/media/wcf7.png "wcf7")

3.  Fare doppio clic su **WindowsApplication1** e fare clic su **Aggiungi riferimento al servizio**. Il **Aggiungi riferimento al servizio** verrà visualizzata la finestra di dialogo.

4.  Nel **Aggiungi riferimento al servizio** la finestra di dialogo, fare clic su **Discover**.

     ![La finestra di dialogo Aggiungi riferimento al servizio](../data-tools/media/wcf8.png "wcf8")

     **Service1** verrà visualizzato nella **Services** riquadro.

5.  Fare clic su **OK** per aggiungere il riferimento al servizio.

#### <a name="to-build-a-client-application"></a>Per compilare un'applicazione client

1.  In **Esplora**, fare doppio clic su **Form1. vb** o **Form1. cs** per aprire Progettazione Windows Form, se non è già aperto.

2.  Dal **della casella degli strumenti**, trascinare un `TextBox` (controllo), un `Label` (controllo) e un `Button` controllo nel form.

     ![Aggiunta di controlli al form](../data-tools/media/wcf9.png "wcf9")

3.  Fare doppio clic su `Button` e aggiungere il seguente codice nel gestore eventi `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  In **Esplora**, fare doppio clic su **WindowsApplication1** e fare clic su **imposta come progetto di avvio**.

5.  Premere **F5** per eseguire il progetto. Immettere del testo e fare clic sul pulsante. L'etichetta visualizza "Valore immesso:" e il testo immesso.

     ![Il modulo che mostra il risultato](../data-tools/media/wcf10.png "wcf10")

## <a name="see-also"></a>Vedere anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)