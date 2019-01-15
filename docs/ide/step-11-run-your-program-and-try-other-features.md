---
title: 'Passaggio 11: Eseguire il programma e provare altre funzionalità'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0a00b328c85758c2be824377d04a0b3cfe122f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968245"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Passaggio 11: Eseguire il programma e provare altre funzionalità
Il programma è stato completato ed è pronto per l'esecuzione. È possibile eseguire il programma e impostare il colore di sfondo di <xref:System.Windows.Forms.PictureBox>. Per continuare a esercitarsi, provare a migliorare il programma modificando il colore del form, personalizzando i pulsanti e la casella di controllo e modificando le proprietà del form.

 Per scaricare una versione completa dell'esempio, vedere [Complete Picture Viewer tutorial sample](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8) (Esercitazione di esempio completa per un visualizzatore di immagini).

 ![Collegamento a video](../data-tools/media/playvideo.gif)Per una versione video di questo argomento, vedere [Esercitazione 1: Creare un visualizzatore di immagini in Visual Basic - Video 5](http://go.microsoft.com/fwlink/?LinkId=205216) o [Esercitazione 1: Creare un visualizzatore immagini in C# - Video 5](http://go.microsoft.com/fwlink/?LinkId=205206). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.

## <a name="to-run-your-program-and-set-the-background-color"></a>Per eseguire il programma e impostare il colore di sfondo

1.  Premere **F5** oppure scegliere **Debug** > **Avvia debug** sulla barra dei menu.

2.  Prima di aprire un'immagine, scegliere il pulsante **Imposta colore di sfondo**. Verrà visualizzata la finestra di dialogo **Colore**.

     ![Finestra di dialogo Colore](../ide/media/express_colordialog.png)
Finestra di dialogo **Colore**

3.  Scegliere un colore per impostare il colore di sfondo di PictureBox. Analizzare attentamente il metodo `backgroundButton_Click()` per capirne il funzionamento.

    > [!NOTE]
    >  È possibile caricare un'immagine da Internet incollando il relativo URL nella finestra di dialogo **Apri file**. Tentare di trovare un'immagine con uno sfondo trasparente, in modo da visualizzare il colore di sfondo scelto.

4.  Scegliere il pulsante **Cancella immagine** per assicurarsi che l'immagine venga cancellata. Uscire quindi dal programma scegliendo il pulsante **Chiudi**.

## <a name="to-try-other-features"></a>Per provare altre funzionalità

-   Modificare il colore del form e dei pulsanti tramite la proprietà **BackColor**.

-   Personalizzare i pulsanti e la casella di controllo usando le proprietà **Font** e **ForeColor**.

-   Modificare le proprietà **FormBorderStyle** e **ControlBox** del form.

-   Usare le proprietà **AcceptButton** e **CancelButton** del modulo, affinché i pulsanti vengano scelti automaticamente quando l'utente preme **INVIO** o **ESC**. Configurare il programma in modo da aprire la finestra di dialogo **Apri file** quando l'utente preme **INVIO** e chiuderla quando l'utente preme **ESC**.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

-   Per altre informazioni sulla programmazione in Visual Studio, vedere [Nozioni di base sulla programmazione](https://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).

-   Per altre informazioni su Visual Basic, vedere [Sviluppo di applicazioni con Visual Basic](/dotnet/visual-basic/developing-apps/index).

-   Per altre informazioni su Visual C#, vedere [Introduzione al linguaggio C# e a .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).

-   Per passare all'esercitazione successiva, vedere [Esercitazione 2: Creare un quiz matematico a tempo (C#)](../ide/tutorial-2-create-a-timed-math-quiz.md).

-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
