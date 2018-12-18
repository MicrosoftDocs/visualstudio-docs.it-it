---
title: 'Procedura: pubblicare un''applicazione WPF con gli stili visuali abilitati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: bab4660d0e76e467bc95c373002a9035a4ccd672
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Procedura: pubblicare un'applicazione WPF per la quale sono attivati gli stili di visualizzazione
Gli stili di visualizzazione attiva l'aspetto dei controlli comuni di modificare in base al tema scelto dall'utente. Per impostazione predefinita, gli stili di visualizzazione non abilitati per le applicazioni Windows Presentation Foundation (WPF), pertanto è necessario abilitare manualmente. Tuttavia, abilitare gli stili visivi per un'applicazione WPF e quindi la pubblicazione della soluzione genera un errore. In questo argomento viene descritto come risolvere questo errore e il processo per la pubblicazione di un'applicazione WPF con gli stili visuali abilitati. Per ulteriori informazioni sugli stili, vedere [Visual Styles Overview](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Per ulteriori informazioni sul messaggio di errore, vedere [risoluzione dei problemi di errori specifici nelle distribuzioni ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Per risolvere l'errore e per pubblicare la soluzione, è necessario eseguire le attività seguenti:  
  
-   [Pubblicare la soluzione senza gli stili visuali abilitati](#BKMK_publishsolwovs).  
  
-   [Creare un file manifesto](#BKMK_CreateManifest).  
  
-   [Il file manifesto incorporato nel file eseguibile della soluzione pubblicata](#BKMK_embedmanifest).  
  
-   [Firmare i manifesti dell'applicazione e distribuzione](#BKMK_signappdeplyman).  
  
 Quindi, è possibile spostare i file nel percorso da cui si desidera agli utenti finali di installare l'applicazione.  
  
##  <a name="BKMK_publishsolwovs"></a>Pubblicare la soluzione senza gli stili visuali abilitati  
  
1.  Verificare che il progetto non ha abilitati gli stili di visualizzazione. Verificare innanzitutto i file manifesto del progetto per il codice XML seguente. Quindi, se il codice XML è presente, racchiudere il codice XML con un tag di commento.  
  
     Per impostazione predefinita, gli stili visivi non sono attivati.  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Le procedure seguenti viene illustrato come aprire il file manifesto associato al progetto.  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>Per aprire il file manifesto in un progetto Visual Basic  
  
    1.  Nella barra dei menu, scegliere **progetto**, *ProjectName***proprietà**, dove *ProjectName* è il nome del progetto WPF.  
  
         Vengono visualizzate le pagine delle proprietà per il progetto WPF.  
  
    2.  Nel **applicazione** scegliere **impostazioni di Windows Vista**.  
  
         Aprire il file app. manifest nel **Editor di codice**.  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>Per aprire il file manifesto in un progetto c#  
  
    1.  Nella barra dei menu, scegliere **progetto**, *ProjectName***proprietà**, dove *ProjectName* è il nome del progetto WPF.  
  
         Vengono visualizzate le pagine delle proprietà per il progetto WPF.  
  
    2.  Nel **applicazione** scheda, prendere nota del nome visualizzato nel campo del manifesto. Questo è il nome del manifesto è associato al progetto.  
  
        > [!NOTE]
        >  Se **Incorpora manifesto con impostazioni predefinite** o **Crea applicazione senza manifesto** visualizzato nel campo del manifesto, non sono abilitati gli stili di visualizzazione. Se il nome di un file manifesto viene visualizzato nel campo del manifesto, procedere al passaggio successivo in questa procedura.  
  
    3.  In **Esplora**, scegliere **Mostra tutti i file** ().  
  
         Questo pulsante consente di visualizzare tutti gli elementi di progetto, inclusi quelli che sono stati esclusi e quelli che sono normalmente nascosti. Il file manifesto viene visualizzato come elemento di progetto.  
  
2.  Compilare e pubblicare la soluzione. Per ulteriori informazioni su come pubblicare la soluzione, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a>Creare un file manifesto  
  
1.  Incollare il seguente codice XML in un file di blocco note.  
  
     Questo codice XML descrive l'assembly che contiene i controlli che supportano gli stili di visualizzazione.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  Nel blocco note, fare clic su **File**, quindi fare clic su **Salva con nome**.  
  
3.  Nel **Salva con nome** della finestra di dialogo di **Salva come** elenco a discesa, seleziona **tutti i file**.  
  
4.  Nel **nome File** denominare il file e aggiungere **manifest** alla fine del nome del file. Ad esempio: **themes.manifest**.  
  
5.  Scegliere il **Sfoglia cartelle** pulsante, selezionare una cartella e quindi fare clic su **salvare**.  
  
    > [!NOTE]
    >  Le procedure rimanenti si presuppongono che il nome di questo file è **themes.manifest** e che il file viene salvato nella directory C:\temp del computer.  
  
##  <a name="BKMK_embedmanifest"></a>Il file manifesto incorporato nel file eseguibile della soluzione pubblicata  
  
1.  Aprire il **prompt dei comandi di Visual Studio**.  
  
     Per ulteriori informazioni su come aprire la **prompt dei comandi di Visual Studio**, vedere [prompt dei comandi](/dotnet/framework/tools/developer-command-prompt-for-vs).  
  
    > [!NOTE]
    >  I passaggi rimanenti supposizioni sulla soluzione con il seguente:  
    >   
    >  -   Il nome della soluzione è **MyWPFProject**.  
    > -   La soluzione si trova nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
    >   
    >      La soluzione viene pubblicata nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
    > -   La versione più recente dei file dell'applicazione pubblicata si trova nella directory seguente:`%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  Non è necessario utilizzare il nome o i percorsi delle directory descritti in precedenza. Il nome e i percorsi descritti sopra vengono utilizzati solo per illustrare i passaggi necessari per pubblicare la soluzione.  
  
2.  Al prompt dei comandi, modificare il percorso della directory che contiene la versione più recente dei file dell'applicazione pubblicata. Nell'esempio seguente viene illustrato questo passaggio.  
  
    ```  
    cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  Al prompt dei comandi, eseguire il comando seguente per incorporare il file manifesto nel file eseguibile dell'applicazione.  
  
    ```  
    mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a>Firmare i manifesti dell'applicazione e di distribuzione  
  
1.  Al prompt dei comandi, eseguire il comando seguente per rimuovere il `.deploy` estensione dal file eseguibile nella directory corrente.  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  Questo esempio si presuppone che un solo file con il `.deploy` estensione di file. Assicurarsi di rinominare tutti i file in questa directory che hanno il `.deploy` estensione di file.  
  
2.  Al prompt dei comandi, eseguire il comando seguente per firmare il manifesto dell'applicazione.  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Questo esempio si presuppone che il manifesto si accede utilizzando la `.pfx` file del progetto. Se non si firmano il manifesto, è possibile omettere il `-cf` parametro utilizzato in questo esempio. Se si firmano il manifesto con un certificato che richiede una password, specificare il `-password` opzione (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`).  
  
3.  Al prompt dei comandi, eseguire il comando seguente per aggiungere il `.deploy` estensione nel nome del file che è stato rinominato in un passaggio precedente di questa procedura.  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  Questo esempio si presuppone che un solo file aveva un `.deploy` estensione di file. Assicurarsi di rinominare tutti i file in questa directory che in precedenza era il `.deploy` estensione di file.  
  
4.  Al prompt dei comandi, eseguire il comando seguente per firmare il manifesto di distribuzione.  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Questo esempio si presuppone che il manifesto si accede utilizzando la `.pfx` file del progetto. Se non si firmano il manifesto, è possibile omettere il `-cf` parametro utilizzato in questo esempio. Se si firmano il manifesto con un certificato che richiede una password, specificare il `-password` opzione, come nel seguente esempio:`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`.  
  
 Dopo avere eseguito questi passaggi, è possibile spostare i file nel percorso da cui si desidera agli utenti finali di installare l'applicazione. Se si prevede di aggiornare spesso la soluzione, è possibile spostare questi comandi in uno script ed eseguire lo script ogni volta che si pubblica una nuova versione.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi a errori specifici nelle distribuzioni ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Panoramica di stili di visualizzazione](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Abilitazione degli stili](https://msdn.microsoft.com/library/bb773175.aspx)   
 [Prompt dei comandi](/dotnet/framework/tools/developer-command-prompt-for-vs)