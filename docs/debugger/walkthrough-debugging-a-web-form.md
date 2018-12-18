---
title: 'Procedura dettagliata: Debug di un Web Form | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 842b52d063b5de701c74501410e3249da7358776
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-a-web-form"></a>Procedura dettagliata: debug di un Web Form
Nei passaggi di questa procedura dettagliata viene illustrato come eseguire il debug di un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], noto anche come Web Form. Viene illustrato come avviare e arrestare l'esecuzione, impostare punti di interruzione ed esaminare le variabili di **espressioni di controllo** finestra.  
  
> [!NOTE]
>  Per completare la procedura dettagliata, è necessario disporre di privilegi di amministratore per il computer server. Per impostazione predefinita, il processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], aspnet_wp.exe o w3wp.exe viene eseguito come processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Per eseguire il debug di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], è necessario disporre dei privilegi di amministratore per il computer in cui [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] viene eseguito. Per ulteriori informazioni, vedere [requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
 Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-create-the-web-form"></a>Per creare il Web Form  
  
1.  Se una soluzione è già aperta, chiuderla.  
  
2.  Nel **File** menu, fare clic su **New**e quindi fare clic su **sito Web**.  
  
     Il **nuovo sito Web** viene visualizzata la finestra di dialogo.  
  
3.  Nel **modelli** riquadro, fare clic su **sito Web ASP.NET**.  
  
4.  Nel **percorso** riga, fare clic su **HTTP** dall'elenco e nella casella di testo, digitare **http://localhost/WebSite**.  
  
5.  Nel **Language** elenco, fare clic su **Visual c#** o **Visual Basic**.  
  
6.  Fare clic su **OK**.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene creato un nuovo progetto e viene visualizzato il codice sorgente HTML predefinito. Crea inoltre una nuova directory virtuale denominata **sito Web** in **sito Web predefinito** in IIS.  
  
7.  Fare clic su di **progettazione** scheda sul margine inferiore.  
  
8.  Fare clic su di **della casella degli strumenti** scheda sul margine sinistro o selezionarla il **vista** menu.  
  
     Verrà aperta la **Casella degli strumenti** .  
  
9. Nel **della casella degli strumenti**, fare clic su di **pulsante** controllo e aggiungerlo all'area di progettazione principale Default.aspx.  
  
10. Nel **della casella degli strumenti**, fare clic su di **Textbox** controllo e trascinare il controllo per l'area di progettazione principale Default.aspx.  
  
11. Fare doppio clic sul controllo Button rilasciato.  
  
     Verrà visualizzata la tabella codici: Default.aspx.cs per C# o Default.aspx.vb per [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Il cursore dovrebbe trovarsi in corrispondenza della funzione `Button1_Click`.  
  
12. Nella funzione `Button1_Click` aggiungere il codice seguente:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Il progetto dovrebbe essere compilato senza errori.  
  
     A questo punto sarà possibile avviare il debug.  
  
### <a name="to-debug-the-web-form"></a>Per eseguire il debug del Web Form  
  
1.  Nella finestra Default.aspx.cs o Default.aspx.vb fare clic sul margine sinistro della stessa riga del testo aggiunto:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Verrà visualizzato un punto di colore rosso e il testo sulla riga verrà evidenziato in rosso. Il punto di colore rosso rappresenta un punto di interruzione. Quando verrà raggiunto questo punto nel codice, l'esecuzione dell'applicazione nel debugger verrà interrotta. Sarà quindi possibile visualizzare lo stato dell'applicazione ed eseguirne il debug. Per ulteriori informazioni, vedere [i punti di interruzione](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Scegliere **Avvia debug** dal menu **Debug**.  
  
3.  Il **debug non attivato** viene visualizzata la finestra di dialogo. Selezionare **modificare il file Web. config per abilitare il debug** opzione e fare clic su **OK**.  
  
     Verrà avviato Internet Explorer e verrà visualizzata la pagina appena progettata.  
  
4.  In Internet Explorer fare clic sul pulsante.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà visualizzata la riga in cui si imposta il punto di interruzione sulla tabella codici Default.aspx.cs o Default.aspx.vb. Tale riga dovrebbe essere evidenziata in giallo. A questo punto è possibile visualizzare le variabili dell'applicazione e controllarne l'esecuzione. L'esecuzione dell'applicazione verrà interrotta e sarà necessario eseguire un comando.  
  
5.  Nel **Debug** menu, fare clic su **Windows**, quindi fare clic su **espressioni di controllo**e quindi fare clic su **Watch1**.  
  
6.  Nel **espressioni di controllo** finestra **TextBox1**.  
  
     Il **espressioni di controllo** finestra viene visualizzato il valore della variabile `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7.  Nel **Debug** menu, fare clic su **Esegui istruzione/routine**.  
  
     Il valore di `TextBox1.Text` le modifiche di **espressioni di controllo** finestra per la lettura:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  Nel **Debug** menu, fare clic su **continua**.  
  
9. In Internet Explorer fare di nuovo clic sul pulsante.  
  
     L'esecuzione verrà nuovamente interrotta in corrispondenza del punto di interruzione.  
  
10. Nella finestra Default.aspx.cs o Default.aspx.vb fare clic sul punto di colore rosso sul margine sinistro.  
  
     Il punto di interruzione verrà rimosso.  
  
11. Nel **Debug** menu, fare clic su **Termina debug**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Per connettere il debugger al Web Form  
  
1.  È possibile connettere il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a un processo in esecuzione. Per ottimizzare l'efficacia del debug, compilare il file eseguibile come versione di debug con i file dei simboli con estensione pdb.  
  
2.  Nella finestra Default.aspx.cs o Default.aspx.vb fare clic sul margine sinistro per impostare nuovamente un punto di interruzione in corrispondenza della riga aggiunta:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  Nel **Debug** menu, fare clic su **Avvia senza eseguire debug**.  
  
     Verrà eseguito il Web Form in Internet Explorer, ma il debugger non verrà connesso.  
  
4.  Connettersi al processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Per ulteriori informazioni, vedere [debug delle applicazioni Web distribuite](../debugger/debugging-deployed-web-applications.md).  
  
5.  In Internet Explorer fare clic sul pulsante nel form.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è necessario raggiungere il punto di interruzione in Default.aspx.cs, Default.aspx.vb o Default.aspx.  
  
6.  Quando si è finito il debug, scegliere il **Debug** menu, fare clic su **Termina debug**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)