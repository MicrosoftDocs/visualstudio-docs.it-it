---
title: Distribuzione di componenti COM con ClickOnce | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 740d72f0ec339ded8ec8b721bbc2b94d706f8da7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="deploying-com-components-with-clickonce"></a>Distribuzione di componenti COM con ClickOnce
Distribuzione di componenti COM legacy è tradizionalmente difficile. I componenti devono essere registrati a livello globale e pertanto possono causare effetti collaterali indesiderati applicazioni sovrapposte. Questa situazione non è in genere un problema nelle applicazioni .NET Framework perché i componenti sono completamente isolati a un'applicazione o compatibili con side-by-side. Visual Studio consente di distribuire i componenti COM isolati in Windows XP o versioni successive del sistema operativo.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fornisce un meccanismo semplice e sicuro per la distribuzione delle applicazioni .NET. Tuttavia, se le applicazioni utilizzano componenti COM legacy, è necessario eseguire ulteriori passaggi di distribuzione. In questo argomento viene descritto come distribuire i componenti COM isolati e fanno riferimento a componenti nativi (ad esempio, da Visual Basic 6.0 o Visual C++).  
  
 Per ulteriori informazioni sulla distribuzione di componenti COM isolati, vedere "distribuzione dell'App semplificata con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM senza registrazione" in [ http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx ](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## <a name="registration-free-com"></a>COM senza registrazione  
 COM senza registrazione è una nuova tecnologia per la distribuzione e l'attivazione di componenti COM isolati. Funziona inserendo la libreria dei tipi del componente e informazioni di registrazione che viene in genere installate nel Registro di sistema in un file XML denominato manifesto, archiviato nella stessa cartella dell'applicazione.  
  
 Isolamento di un componente COM richiede che sia stata registrata nel computer dello sviluppatore, ma non deve essere registrata nel computer dell'utente finale. Per isolare un componente COM, è sufficiente impostare il relativo riferimento **Isolated** proprietà **True**. Per impostazione predefinita, questa proprietà è impostata su **False**, che indica che deve essere considerato come un riferimento COM registrato. Se questa proprietà è **True**, verrà creato un manifesto da generare per questo componente in fase di compilazione. Fa inoltre i file corrispondenti a essere copiato nella cartella dell'applicazione durante l'installazione.  
  
 Quando il generatore del manifesto incontra un riferimento COM isolato, enumera tutte le `CoClass` voci nella libreria dei tipi del componente, facendo corrispondere ogni voce con i corrispondenti dati di registrazione e la generazione di definizioni del manifesto per tutto il modello COM classi nel file di libreria del tipo.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Distribuzione di componenti COM senza registrazione tramite ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia di distribuzione è ideale per la distribuzione di componenti COM isolati, perché entrambi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM senza registrazione è necessario che un componente disponga di un manifesto.  
  
 In genere, l'autore del componente deve fornire un manifesto. In caso contrario, Visual Studio è tuttavia in grado di generare un manifesto automaticamente per un componente COM. La generazione del manifesto viene eseguita durante il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] processo di pubblicazione; per ulteriori informazioni, vedere [pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md). Questa funzionalità consente inoltre di sfruttare i componenti legacy creati in ambienti di sviluppo precedenti, ad esempio Visual Basic 6.0.  
  
 Esistono due modi che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente di distribuire i componenti COM:  
  
-   Utilizzare il programma di avvio per distribuire i componenti COM. Ciò funziona su tutte le piattaforme supportate.  
  
-   Utilizzare la distribuzione di un componente nativo isolamento (noto anche come COM senza registrazione). Tuttavia, questa impostazione funziona solo in un Windows XP o versioni successive del sistema operativo.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Esempio di isolamento e la distribuzione di un componente COM semplice  
 Per illustrare la distribuzione dei componenti COM senza registrazione, questo esempio creare un'applicazione basata su Windows in Visual Basic che fa riferimento a un componente COM nativo isolato creato con Visual Basic 6.0 e distribuirlo utilizzando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 È necessario innanzitutto creare il componente COM nativo:  
  
##### <a name="to-create-a-native-com-component"></a>Per creare un componente COM nativo  
  
1.  Utilizzando Visual Basic 6.0, il **File** menu, fare clic su **New**, quindi **progetto**.  
  
2.  Nel **nuovo progetto** la finestra di dialogo, seleziona il **Visual Basic** nodo e selezionare un **DLL ActiveX** progetto. Nella casella **Nome** digitare `VB6Hello`.  
  
    > [!NOTE]
    >  Sono supportati solo i tipi di progetto DLL ActiveX e il controllo ActiveX con COM senza registrazione. Non sono supportati i tipi di progetto EXE ActiveX e documento ActiveX.  
  
3.  In **Esplora**, fare doppio clic su **Class1. vb** per aprire l'editor di testo.  
  
4.  In Class1. vb aggiungere il codice seguente dopo il codice generato per il `New` metodo:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Compilare il componente. Dal **compilare** menu, fare clic su **Compila soluzione**.  
  
> [!NOTE]
>  COM senza registrazione supporta solo le DLL e controlla i tipi di progetto di COM. È possibile utilizzare i file exe con COM senza registrazione  
  
 È ora possibile creare un'applicazione basata su Windows e aggiungere un riferimento al componente COM.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Per creare un'applicazione basata su Windows usando un componente COM  
  
1.  Utilizzando Visual Basic, il **File** menu, fare clic su **New**, quindi **progetto**.  
  
2.  Nel **nuovo progetto** la finestra di dialogo, seleziona il **Visual Basic** nodo e selezionare **applicazione Windows**. Nella casella **Nome** digitare `RegFreeComDemo`.  
  
3.  In **Esplora**, fare clic su di **Mostra tutti i file** pulsante per visualizzare i riferimenti al progetto.  
  
4.  Fare doppio clic su di **riferimenti** nodo e selezionare **Aggiungi riferimento** dal menu di scelta rapida.  
  
5.  Nel **Aggiungi riferimento** nella finestra di dialogo fare clic su di **Sfoglia** scheda, passare a VB6Hello, quindi selezionarla.  
  
     Oggetto **VB6Hello** riferimento viene visualizzato nell'elenco di riferimenti.  
  
6.  Scegliere il **della casella degli strumenti**, selezionare un **pulsante** controllare e trascinarlo in modo che il **Form1** form.  
  
7.  Nel **proprietà** finestra, impostare il pulsante **testo** proprietà **Hello**.  
  
8.  Fare doppio clic sul pulsante per aggiungere il codice del gestore e nel file di codice, aggiungere il codice in modo che il gestore è simile alla seguente:  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Eseguire l'applicazione. Dal **Debug** menu, fare clic su **Avvia debug**.  
  
 Successivamente, è necessario isolare il controllo. Ogni componente COM che usa l'applicazione è rappresentato nel progetto come riferimento COM. Questi riferimenti sono visibili nel **riferimenti** nodo il **Esplora** finestra. (Si noti che è possibile aggiungere riferimenti a direttamente mediante il **Aggiungi riferimento** comando il **progetto** menu o indirettamente, trascinare un controllo ActiveX nel form.)  
  
 La procedura seguente viene illustrato come isolare il componente COM e pubblicare l'applicazione aggiornata che contiene il controllo di tipo isolato:  
  
##### <a name="to-isolate-a-com-component"></a>Per isolare un componente COM  
  
1.  In **Esplora**nel **riferimenti** nodo, seleziona il **VB6Hello** riferimento.  
  
2.  Nel **proprietà** finestra, modificare il valore della **Isolated** proprietà **False** per **True**.  
  
3.  Dal **compilare** menu, fare clic su **Compila soluzione**.  
  
 A questo punto, quando si preme F5, l'applicazione funzionerà come previsto, ma ora è in esecuzione in COM senza registrazione Per dimostrarlo, provare l'annullamento della registrazione del componente VB6Hello e in esecuzione RegFreeComDemo1.exe di fuori di IDE di Visual Studio. Questa volta quando si fa clic sul pulsante, il corretto funzionamento. Se si rinomina temporaneamente il manifesto dell'applicazione, ne verrà eseguito nuovamente.  
  
> [!NOTE]
>  È possibile simulare l'assenza di un componente COM da temporaneamente la registrazione. Aprire un prompt dei comandi, passare alla cartella di sistema digitando `cd /d %windir%\system32`, quindi annullare la registrazione del componente digitando `regsvr32 /u VB6Hello.dll`. È possibile registrarlo nuovamente digitando `regsvr32 VB6Hello.dll`.  
  
 Il passaggio finale consiste nel pubblicare l'applicazione utilizzando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Per pubblicare un aggiornamento dell'applicazione con un componente COM isolato  
  
1.  Dal **compilare** menu, fare clic su **Pubblica RegFreeComDemo**.  
  
     Verrà visualizzata la Pubblicazione guidata.  
  
2.  Nella pubblicazione guidata, specificare un percorso su disco del computer locale in cui è possibile accedere ed esaminare i file.  
  
3.  Fare clic su **fine** per pubblicare l'applicazione.  
  
 Se si esaminano i file, si noterà che è incluso il file Sysmon. ocx. Il controllo è completamente isolato a questa applicazione, vale a dire che, se il computer dell'utente finale è un'altra applicazione utilizza una versione diversa del controllo, non può interferire con l'applicazione.  
  
## <a name="referencing-native-assemblies"></a>Riferimenti ad assembly nativi  
 Visual Studio supporta riferimenti a nativi di Visual Basic 6.0 o assembly C++. tali riferimenti vengono chiamati i riferimenti nativi. È possibile indicare se un riferimento è nativo verificando che il relativo **tipo di File** è impostata su **nativo** o **ActiveX**.  
  
 Per aggiungere un riferimento nativo, utilizzare il **Aggiungi riferimento** comando, quindi passare al manifesto. Alcuni componenti di inserire il manifesto all'interno della DLL. In questo caso, è possibile scegliere semplicemente la DLL e Visual Studio venga aggiunta come un riferimento nativo se rileva che il componente contiene un manifesto incorporato. Visual Studio verrà inclusi automaticamente i file dipendenti elencati nel manifesto che si trovano nella stessa cartella del componente di riferimento di assembly.  
  
 Isolamento controllo COM semplifica la distribuzione di componenti COM che non dispongono già di manifesti. Tuttavia, se un componente viene fornito con un manifesto, è possibile fare riferimento il manifesto direttamente. Infatti, devono utilizzare sempre il manifesto fornito dall'autore del componente, laddove possibile, invece di usare il **Isolated** proprietà.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitazioni della distribuzione di componenti COM senza registrazione  
 COM senza registrazione offre vantaggi crittografati tramite le tecniche tradizionali di distribuzione. Tuttavia, esistono alcune limitazioni e avvertenze che è opportuno prestare attenzione. Il limite massimo è che funziona solo in Windows XP o versione successiva. L'implementazione di COM senza registrazione richiesta al modo in cui i componenti vengono caricati nel sistema operativo di base. Sfortunatamente, non vi è alcun livello di supporto di livello inferiore per COM senza registrazione  
  
 Non tutti i componenti sono un candidato idoneo per COM senza registrazione Un componente non è adatto se una delle seguenti sono vere:  
  
-   Il componente è un server out-of-process. I server EXE non sono supportati. sono supportate solo le DLL.  
  
-   Il componente fa parte del sistema operativo, o un componente di sistema, ad esempio XML, Internet Explorer o Microsoft Data Access Components (MDAC). È necessario seguire i criteri di ridistribuzione dell'autore del componente; rivolgersi al fornitore.  
  
-   Il componente è parte di un'applicazione, ad esempio Microsoft Office. Ad esempio, non tentare di isolare il modello oggetto di Microsoft Excel. Questo fa parte di Office e può essere utilizzato solo in un computer con il prodotto completo di Office installato.  
  
-   Il componente deve essere utilizzato come un componente aggiuntivo o uno snap-in, ad esempio un componente aggiuntivo di Office o un controllo in un Web browser. Tali componenti in genere richiedono un tipo di schema di registrazione definito dall'ambiente di hosting che non rientra nell'ambito del manifesto.  
  
-   Il componente gestisce un dispositivo fisico o virtuale per il sistema, ad esempio, un driver di dispositivo per uno spooler di stampa.  
  
-   Il componente è un accesso ai dati ridistribuibile. In genere, le applicazioni dati richiedono un accesso ai dati ridistribuibili da installare prima che possano eseguire. Non tentare di isolare i componenti, ad esempio il controllo dati ADO di Microsoft, Microsoft OLE DB o Microsoft Data Access Components (MDAC). In alternativa, se l'applicazione utilizza MDAC o SQL Server Express, è necessario impostarli come prerequisiti; vedere [procedura: installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
 In alcuni casi, potrebbe essere possibile per lo sviluppatore del componente, riprogettare per COM senza registrazione In caso contrario, è possibile compilare e pubblicare applicazioni che dipendono da tali tramite lo schema di registrazione standard utilizzando il programma di avvio. Per ulteriori informazioni, vedere [la creazione di pacchetti del programma di avvio](../deployment/creating-bootstrapper-packages.md).  
  
 Un componente COM può essere solo una volta isolato per ogni applicazione. Ad esempio, è possibile isolare lo stesso componente COM da due diversi **libreria di classi** progetti che fanno parte della stessa applicazione. Questa operazione provocherà un avviso di compilazione e l'applicazione non verrà caricato in fase di esecuzione. Per evitare questo problema, si consiglia di incapsulare i componenti COM in un'unica libreria.  
  
 Esistono diversi scenari di COM, la registrazione è necessaria nel computer dello sviluppatore, anche se la distribuzione dell'applicazione non richiede la registrazione. Il `Isolated` proprietà richiede che il componente COM sia registrato nel computer dello sviluppatore per generare automaticamente il manifesto durante la compilazione. Non sono disponibili funzionalità di acquisizione della registrazione messaggi che richiamano la registrazione automatica durante la compilazione. Inoltre, tutte le classi non esplicitamente definite nella libreria dei tipi non si rifletteranno nel manifesto. Quando si utilizza un componente COM con un manifesto esistente, ad esempio un riferimento nativo, il componente potrebbe non devono essere registrati in fase di sviluppo. Tuttavia, la registrazione è necessario se il componente è un controllo ActiveX e si desidera includere nella **della casella degli strumenti** e la finestra di progettazione Windows Form.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)