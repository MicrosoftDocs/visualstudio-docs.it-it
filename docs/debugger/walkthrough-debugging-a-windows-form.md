---
title: 'Procedura dettagliata: Debug di un Windows Form | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4e256aeef1a068ddc46d13e98b344bcce56d08b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="walkthrough-debugging-a-windows-form"></a>Procedura dettagliata: debug di un Windows Form
Un Windows Form è una delle applicazioni gestite più comuni. Un Windows Form consente di creare un'applicazione Windows standard. È possibile completare questa procedura dettagliata usando Visual Basic, c# o C++.  
  
 In primo luogo, è necessario chiudere eventuali soluzioni aperte.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Operazioni preliminari per la procedura dettagliata  
  
-   Se è già aperta una soluzione aperta, chiuderla. (Nel **File** dal menu **Chiudi soluzione**.)  
  
## <a name="create-a-new-windows-form"></a>Creare un nuovo Windows Form  
 Successivamente, si creerà un nuovo Windows Form.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Per creare il form di Windows per questa procedura dettagliata  
  
1.  Nel **File** menu, scegliere **New** e fare clic su **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Nel riquadro Tipi progetto, aprire il **Visual Basic**, **Visual c#**, o **Visual C++** nodo, quindi  
  
    1.  Per Visual Basic o Visual c#, selezionare il **Windows** nodo, quindi selezionare **applicazione Windows Form** nel **modelli** riquadro.  
  
    2.  Per Visual C++, selezionare il **CLR** nodo, quindi selezionare **applicazione Windows Form** nel **modelli** riquadro...  
  
3.  Nel **modelli** riquadro, selezionare **applicazione Windows**.  
  
4.  Nel **nome** , assegnare al progetto un nome di univoco, ad esempio, Procedura_DebugSemplice.  
  
5.  Fare clic su **OK**.  
  
     Visual Studio crea un nuovo progetto e visualizza un nuovo form nella finestra di progettazione Windows Form. Per ulteriori informazioni, vedere [Progettazione Windows Form](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6.  Nel **vista** dal menu **della casella degli strumenti**.  
  
     Verrà visualizzata la casella degli strumenti. Per altre informazioni, vedere [Casella degli strumenti](../ide/reference/toolbox.md).  
  
7.  Nella casella degli strumenti, fare clic su di **pulsante** controllare e trascinarlo nell'area di progettazione del Form. Rilasciare il pulsante sul form.  
  
8.  Nella casella degli strumenti, fare clic su di **TextBox** controllare e trascinarlo nell'area di progettazione del Form. Eliminare il **TextBox** nel form.  
  
9. Nella finestra di progettazione form fare doppio clic sul pulsante.  
  
     Verrà visualizzata la tabella codici. Il cursore deve trovarsi in `button1_Click`.  
  
10. Nella funzione `button1_Click`., aggiungere il codice seguente:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Il progetto dovrebbe essere compilato senza errori.  
  
## <a name="debug-your-form"></a>Eseguire il debug del Form  
 A questo punto, si è pronti per iniziare il debug.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Per eseguire il debug del Windows Form creato per questa procedura dettagliata  
  
1.  Nella finestra di origine, fare clic sul margine sinistro stessa riga del testo aggiunto:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Verrà visualizzato un punto di colore rosso e il testo sulla riga verrà evidenziato in rosso. Il punto di colore rosso rappresenta un punto di interruzione. Per ulteriori informazioni, vedere [i punti di interruzione](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). Quando verrà raggiunto questo punto nel codice, l'esecuzione dell'applicazione nel debugger verrà interrotta. Sarà quindi possibile visualizzare lo stato dell'applicazione ed eseguirne il debug.  
  
    > [!NOTE]
    >  È anche possibile fare doppio clic su qualsiasi riga di codice, scegliere **punto di interruzione**, quindi fare clic su **Inserisci punto di interruzione** per aggiungere un punto di interruzione riga.  
  
2.  ON il **Debug** menu, scegliere **avviare**.  
  
     Il modulo di Windows viene avviata l'esecuzione.  
  
3.  In Windows Form, fare clic sul pulsante che è stato aggiunto.  
  
     In Visual Studio, verrà visualizzata la riga in cui è impostato il punto di interruzione sulla tabella codici. Tale riga dovrebbe essere evidenziata in giallo. A questo punto è possibile visualizzare le variabili dell'applicazione e controllarne l'esecuzione. L'applicazione viene interrotta l'esecuzione, in attesa di un'azione da parte dell'utente.  
  
4.  Nel **Debug** menu, scegliere **Windows**, quindi **espressioni di controllo**, fare clic su **Watch1**.  
  
5.  Nel **Watch1** finestra, fare clic su una riga vuota. Nel **nome** colonna, tipo `textBox1.Text` (se si utilizza Visual Basic o Visual c#) o `textBox1->Text` (se si utilizza C++), quindi premere INVIO.  
  
     Il **Watch1** finestra viene visualizzato il valore di questa variabile tra virgolette:  
  
    ```  
    ""  
    ```  
  
6.  Nel **Debug** menu, scegliere **Esegui istruzione**.  
  
     Il valore di textBox1. Text il **Watch1** della finestra:  
  
    ```  
    Button was clicked!  
    ```  
  
7.  Nel **Debug** menu, scegliere **continua** per riprendere il debug del programma.  
  
8.  In Windows Form, fare clic sul pulsante.  
  
     Visual Studio interrompe l'esecuzione di nuovo.  
  
9. Fare clic sul punto rosso che rappresenta il punto di interruzione.  
  
     Consente di rimuovere il punto di interruzione dal codice.  
  
10. Nel **Debug** menu, scegliere **Termina debug**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Collegamento all'applicazione Windows Form per il debug  
 È possibile connettere il debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] a un processo in esecuzione. Se si utilizza una versione Express Edition, questa funzionalità non è supportata.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Per connettersi all'applicazione Windows Form per il debug  
  
1.  Nel progetto creato in precedenza, fare clic sul margine sinistro per impostare nuovamente un punto di interruzione in corrispondenza della riga aggiunta:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  Nel **Debug** dal menu **Avvia senza eseguire debug**.  
  
     Windows Form verrà eseguito in Windows, come se è stato fatto doppio clic con il relativo file eseguibile. Il debugger non è connesso.  
  
3.  Nel **Debug** dal menu **Connetti a processo**. (Questo comando è disponibile anche la **strumenti** menu.)  
  
     Verrà visualizzata la finestra di dialogo **Connetti a processo** .  
  
4.  Nel **processi disponibili** riquadro, trovare il nome del processo (Walkthrough_SimpleDebug.exe) nei **processo** colonna e farvi clic sopra.  
  
5.  Fare clic su di **collegamento** pulsante.  
  
6.  In Windows Form, fare clic su quello e solo pulsante.  
  
     Il debugger interrompe l'esecuzione di Windows Form nel punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)