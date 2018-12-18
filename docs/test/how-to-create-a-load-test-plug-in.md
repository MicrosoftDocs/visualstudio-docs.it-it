---
title: Creare un plug-in test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6e585fe66bde573f8bb133b0c8cda0900b0d6d16
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-load-test-plug-in"></a>Procedura: creare un plug-in test di carico

È possibile creare un plug-in test di carico per eseguire il codice in momenti diversi durante l'esecuzione del test di carico. Si crea un plug-in per espandere o modificare le funzioni incorporate del test di carico. È ad esempio possibile scrivere codice per un plug-in test di carico per impostare o modificare il modello del test di carico durante l'esecuzione del test di carico. A tale scopo, è necessario creare una classe che erediti l'interfaccia <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Tale classe deve implementare il metodo <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> dell'interfaccia. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!NOTE]
> È anche possibile creare plug-in per i test Web. Per altre informazioni, vedere [Procedura: Creare un plug-in di test prestazioni Web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="to-create-a-load-test-plug-in-by-using-visual-c"></a>Per creare un plug-in test di carico utilizzando Visual C#

1.  Aprire un progetto di test di carico e prestazioni Web che contenga un test delle prestazioni Web.

2.  Aggiungere un test di carico al progetto di test e configurarlo per eseguire un test Web.

     Per altre informazioni, vedere [Avvio rapido: Creare un progetto di test di carico](../test/quickstart-create-a-load-test-project.md).

3.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione, selezionare **Aggiungi**, quindi scegliere **Nuovo progetto**.

     Viene visualizzata la finestra di dialogo **Aggiungi nuovo progetto**.

4.  In **Modelli installati** selezionare **Visual C#**.

5.  Nell'elenco dei modelli selezionare **Libreria di classi**.

6.  Nella casella di testo **Nome** digitare un nome per la classe.

7.  Scegliere **OK**.

8.  Il nuovo progetto di libreria di classi viene aggiunto a Esplora soluzioni e la nuova classe viene visualizzata nell'Editor del codice.

9. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella **Riferimenti** nella nuova libreria di classi e selezionare **Aggiungi riferimento**.

10. Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

11. Scegliere la scheda **.NET**, scorrere verso il basso, quindi selezionare **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

12. Scegliere **OK**.

     Il riferimento a **Microsoft.VisualStudio.QualityTools.LoadTestFramework** viene aggiunto alla cartella **Riferimenti** in Esplora soluzioni.

13. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo principale del progetto di test di carico e prestazioni Web contenente il test di carico al quale aggiungere il plug-in test di carico e selezionare **Aggiungi riferimento**.

14. Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

15. Scegliere la scheda **Progetti** e selezionare il progetto di libreria di classi.

16. Scegliere **OK**.

17. Nell'Editor di codice aggiungere un'istruzione `using` per lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

18. Implementare l'interfaccia <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> per la classe creata nel progetto Libreria di classi. Per un'implementazione di esempio, vedere la sezione seguente relativa all'esempio.

19. Una volta scritto il codice, compilare il nuovo progetto.

20. Fare clic con il pulsante destro del mouse sul nodo principale del test di carico e scegliere **Aggiungi plug-in test di carico**.

     Viene visualizzata la finestra di dialogo **Aggiungi plug-in test di carico**.

21. In **Seleziona un plug-in** selezionare la classe del plug-in del test di carico.

22. Nel riquadro **Proprietà per il plug-in selezionato** impostare i valori iniziali per il plug-in da usare in fase di esecuzione.

    > [!NOTE]
    > È possibile esporre il numero di proprietà desiderato dai plug-in; è sufficiente renderle pubbliche, impostabili e di un tipo di base quale Integer, Boolean o String. È anche possibile modificare le proprietà del plug-in di test delle prestazioni Web in un secondo momento utilizzando la finestra Proprietà.

23. Scegliere **OK**.

     Il plug-in viene aggiunto alla cartella **Plug-in test di carico**.

    > [!WARNING]
    > Quando si esegue un test delle prestazioni Web o un test di carico in cui viene utilizzato il plug-in, è possibile che venga visualizzato un errore simile a quello seguente:
    >
    > **Richiesta non riuscita: Eccezione in \<plug-in> event: Impossibile caricare il file o l'assembly '\<"Plug-in name".dll file>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' o una delle relative dipendenze. Il sistema non riesce a trovare il file specificato.**
    >
    > L'errore si verifica se si effettuano modifiche al codice di uno qualsiasi dei plug-in e si crea una nuova versione del file DLL **(Version=0.0.0.0)**, ma il plug-in fa ancora riferimento alla versione originale. Per risolvere il problema, attenersi ai passaggi riportati di seguito:
    >
    > 1.  Nei riferimenti del progetto di test di carico e prestazioni Web sarà presente un avviso. Rimuovere e aggiungere nuovamente il riferimento alla DLL del plug-in.
    > 2.  Rimuovere il plug-in dal test o dal percorso appropriato, quindi aggiungerlo di nuovo.

## <a name="example"></a>Esempio

Nel codice seguente viene illustrato un plug-in test di carico in cui viene eseguito il codice personalizzato dopo un evento LoadTestFinished. Se questo codice viene eseguito in un agente di test in un computer remoto e l'agente di test non dispone di un servizio SMTP localhost, lo stato del test di carico rimarrà indicato come "In corso" dal momento che verrà visualizzata una casella di messaggio.

> [!NOTE]
>  Per il codice seguente è necessaria l'aggiunta di un riferimento a System.Windows.Forms.

```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

A un test di carico sono associati otto eventi che possono essere gestiti nel plug-in test di carico per eseguire il codice personalizzato con il test di carico. Di seguito è riportato un elenco degli eventi che consentono di accedere a stadi diversi dell'esecuzione del test di carico:

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Creare codice personalizzato e plug-in per test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Procedura: Creare un plug-in di test prestazioni Web](../test/how-to-create-a-web-performance-test-plug-in.md)