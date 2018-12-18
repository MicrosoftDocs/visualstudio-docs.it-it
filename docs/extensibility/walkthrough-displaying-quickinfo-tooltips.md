---
title: 'Procedura dettagliata: Visualizzazione delle descrizioni comandi informazioni rapide | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9cd3e9d5e10e6946b4cae8ce02a5a39511e4baaf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Procedura dettagliata: Visualizzazione delle descrizioni comandi informazioni rapide
Informazioni rapide è una funzionalità di IntelliSense che consente di visualizzare le firme del metodo e le descrizioni quando l'utente sposta il puntatore su un nome di metodo. È possibile implementare funzionalità basate sul linguaggio, come informazioni rapide definendo gli identificatori per il quale si desidera fornire le descrizioni di informazioni rapide e quindi la creazione di una descrizione comando in cui visualizzare il contenuto. È possibile definire informazioni rapide nel contesto di un servizio di linguaggio, è possibile definire il tipo di estensione e il contenuto di nome file e visualizzare le informazioni rapide per quel tipo o è possibile visualizzare informazioni rapide per un tipo di contenuto esistente (ad esempio "text"). Questa procedura dettagliata viene illustrato come visualizzare informazioni rapide per il tipo di contenuto "text".  
  
 Nell'esempio di informazioni rapide in questa procedura dettagliata consente di visualizzare le descrizioni comandi quando si sposta il puntatore del mouse su un nome di metodo. Questa progettazione è necessario implementare queste quattro interfacce:  
  
-   interfaccia di origine  
  
-   interfaccia del provider di origine  
  
-   interfaccia controller  
  
-   interfaccia del provider controller  
  
 I provider di origine e i controller sono parti componente Managed Extensibility Framework (MEF) e sono responsabili per l'esportazione le classi di origine e il controller, l'importazione dei servizi e di connessione, ad esempio il <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, che consente di creare il testo della descrizione comando buffer e <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, che avvia la sessione di informazioni rapide.  
  
 In questo esempio, l'origine di informazioni rapide utilizza un elenco hardcoded di nomi di metodo e le descrizioni, ma in implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabili per fornire tale contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo Seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `QuickInfoTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementazione dell'origine di informazioni rapide  
 L'origine di informazioni rapide è responsabile per la raccolta di set di identificatori e le relative descrizioni e aggiungendo il contenuto del buffer di testo della descrizione comando quando uno degli identificatori viene rilevato. In questo esempio, gli identificatori e le relative descrizioni vengono aggiunti solo nel costruttore di origine.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Per implementare l'origine di informazioni rapide  
  
1.  Aggiungere un file di classe e assegnargli il nome `TestQuickInfoSource`.  
  
2.  Aggiungere un riferimento a Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Aggiungere i seguenti.  
  
     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>e denominarla `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Aggiungere campi per il provider di origine di informazioni rapide, il buffer di testo e un set di nomi di metodi e le firme del metodo. In questo esempio, i nomi di metodo e le firme vengono inizializzate le `TestQuickInfoSource` costruttore.  
  
     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Aggiungere un costruttore che imposta il provider di origine di informazioni rapide e il buffer di testo e consente di popolare il set di nomi di metodo e firme dei metodi e le descrizioni.  
  
     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. In questo esempio, il metodo trova la parola corrente o la parola precedente, se il cursore si trova alla fine di una riga o di un buffer di testo. Se la parola è uno dei nomi di metodo, la descrizione di tale nome viene aggiunto per il contenuto di informazioni rapide.  
  
     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  È inoltre necessario implementare un metodo Dispose (), poiché <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementa <xref:System.IDisposable>:  
  
     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementazione di un Provider di origine di informazioni rapide  
 Il provider dell'origine di informazioni rapide serve principalmente per esportare se stessa come componente MEF e creare un'istanza di origine di informazioni rapide. Poiché è un componente MEF, è possibile importare altri parti componente MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Per implementare un provider di origine di informazioni rapide  
  
1.  Dichiarare un provider di origine di informazioni rapide denominato `TestQuickInfoSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "Origine di informazioni rapide di descrizione comandi," un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di Before = "default" e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text".  
  
     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importare i due servizi di editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, come proprietà di `TestQuickInfoSourceProvider`.  
  
     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> per restituire un nuovo `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementazione di un Controller di informazioni rapide  
 Informazioni rapide controller determinano quando deve essere visualizzato informazioni rapide. In questo esempio, informazioni rapide viene visualizzata quando il puntatore è su una parola che corrisponde a uno dei nomi di metodo. Il controller di informazioni rapide implementa un gestore eventi di passaggio del mouse che attiva una sessione di informazioni rapide.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Per implementare un controller di informazioni rapide  
  
1.  Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>e denominarla `TestQuickInfoController`.  
  
     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Aggiungere campi privati per la visualizzazione di testo, i buffer di testo rappresentati in visualizzazione di testo, la sessione di informazioni rapide e il provider di informazioni rapide controller.  
  
     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Aggiungere un costruttore che imposta i campi e aggiunge il gestore dell'evento del mouse al passaggio del mouse.  
  
     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Aggiungere il gestore dell'evento del mouse al passaggio del mouse che attiva la sessione di informazioni rapide.  
  
     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodo in modo che rimuove il gestore dell'evento del mouse al passaggio del mouse quando il controller viene disconnesso dalla visualizzazione di testo.  
  
     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> (metodo) e <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodi vuoti per questo esempio il metodo.  
  
     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementazione del Provider di informazioni rapide Controller  
 Il provider del controller di informazioni rapide serve principalmente per esportare se stessa come componente MEF e creare un'istanza del controller di informazioni rapide. Poiché è un componente MEF, è possibile importare altri parti componente MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Per implementare il provider di controller di informazioni rapide  
  
1.  Dichiarare una classe denominata `TestQuickInfoControllerProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "Descrizione comando informazioni rapide Controller" e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text":  
  
     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importazione di <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> come una proprietà.  
  
     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metodo creando un'istanza del controller di informazioni rapide.  
  
     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione QuickInfoTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Per compilare e testare la soluzione QuickInfoTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e tipo di testo che include le parole "Aggiungi" e "sottrazione".  
  
4.  Spostare il puntatore su una delle occorrenze di "Aggiungi". La firma e la descrizione di `add` (metodo) deve essere visualizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)