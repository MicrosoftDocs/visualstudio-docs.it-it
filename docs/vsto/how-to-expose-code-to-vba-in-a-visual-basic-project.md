---
title: 'Procedura: esporre il codice a VBA in un progetto di Visual Basic | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 39dc659f7c8841bcf350249332278091232a32d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Procedura: esporre il codice a VBA in un progetto Visual Basic
  È possibile esporre codice in un [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] progetto di Visual Basic Applications Edition (VBA) se si desidera che i due tipi di codice per interagire tra loro.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Il processo di Visual Basic è diverso dal processo di Visual c#. Per altre informazioni, vedere [procedura: esporre il codice a VBA in un Visual C&#35; progetto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Il processo è diverso da quello per il codice in altre classi per il codice in una classe dell'elemento host:  
  
-   [Esposizione di codice in una classe dell'elemento host](#HostItemCode)  
  
-   [Esposizione di codice che non è in una classe dell'elemento host](#NonHostItem)  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [modo in cui si ricerca per categorie: chiamata di codice VSTO da VBA?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> Esposizione di codice in una classe dell'elemento Host  
 Per consentire al codice VBA di chiamare il codice Visual Basic in una classe dell'elemento host, impostare il **EnableVbaCallers** proprietà dell'elemento host su **True**.  
  
 Per una procedura dettagliata che illustra come esporre un metodo di una classe dell'elemento host e quindi chiamarlo da VBA, vedere [procedura dettagliata: chiamata di codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Per altre informazioni sugli elementi host, vedere [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Per esporre il codice in un elemento host a VBA  
  
1.  Aprire o creare un livello di documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] progetto basato su un documento di Word, cartella di lavoro di Excel o modello di Excel che supporta le macro e che contiene già codice VBA.  
  
     Per ulteriori informazioni sui formati di file del documento che supportano le macro, vedere [combinazione di VBA e le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Questa funzionalità non può essere usata nei progetti Modello di Word,  
  
2.  Verificare che il codice VBA nel documento è possibile eseguire senza chiedere conferma all'utente di attivare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.  
  
3.  Aggiungere la proprietà, un metodo o un evento che si desidera esporre a VBA a una delle classi dell'elemento host del progetto e dichiarare il nuovo membro come **pubblica**. Il nome della classe dipende dall'applicazione:  
  
    -   Un progetto, la classe dell'elemento host è denominata `ThisDocument` per impostazione predefinita.  
  
    -   In un progetto di Excel, le classi dell'elemento host sono denominate `ThisWorkbook`, `Sheet1`, `Sheet2`, e `Sheet3` per impostazione predefinita.  
  
4.  Impostare il **EnableVbaCallers** proprietà per l'elemento host **True**. Questa proprietà è disponibile nel **proprietà** finestra quando l'elemento host è aperto nella finestra di progettazione.  
  
     Dopo aver impostato questa proprietà, Visual Studio imposta automaticamente il **ReferenceAssemblyFromVbaProject** proprietà **True**.  
  
    > [!NOTE]  
    >  Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, si riceverà un messaggio di errore quando si imposta la **EnableVbaCallers** proprietà **True**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.  
  
5.  Fare clic su **OK** nel messaggio visualizzato. Questo messaggio per ricordare che se si aggiunge codice VBA alla cartella di lavoro o al documento mentre si eseguono il progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il codice VBA andranno perso alla successiva compilazione del progetto. Questo avviene perché il documento nella cartella di output di compilazione viene sovrascritto ogni volta che si compila il progetto.  
  
     A questo punto, Visual Studio configura il progetto in modo che il progetto VBA è possibile chiamare nell'assembly. Visual Studio aggiunge anche una proprietà denominata `CallVSTOAssembly` per il `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, o `Sheet3` modulo nel progetto VBA. È possibile utilizzare questa proprietà per accedere ai membri pubblici della classe esposta a VBA.  
  
6.  Compilare il progetto.  
  
##  <a name="NonHostItem"></a> Esposizione di codice che non è in una classe dell'elemento Host  
 Per consentire al codice VBA di chiamare il codice di Visual Basic che non è in una classe dell'elemento host, modificare il codice è visibile a VBA.  
  
#### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Per esporre il codice che non è in una classe dell'elemento host a VBA  
  
1.  Aprire o creare un livello di documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] progetto basato su un documento di Word, cartella di lavoro di Excel o modello di Excel che supporta le macro e che contiene già codice VBA.  
  
     Per ulteriori informazioni sui formati di file del documento che supportano le macro, vedere [combinazione di VBA e le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Questa funzionalità non può essere usata nei progetti Modello di Word,  
  
2.  Verificare che il codice VBA nel documento è possibile eseguire senza chiedere conferma all'utente di attivare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.  
  
3.  Aggiungere il membro che si desidera esporre a VBA a una classe pubblica nel progetto e dichiarare il nuovo membro come **pubblica**.  
  
4.  Applicare la seguente istruzione <xref:System.Runtime.InteropServices.ComVisibleAttribute> e <xref:Microsoft.VisualBasic.ComClassAttribute> attributi alla classe che si sta esponendo a VBA. Questi attributi rendono visibile a VBA la classe.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Eseguire l'override del metodo **GetAutomationObject** di una classe di elementi host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA. L'esempio di codice seguente presuppone che si sta esponendo a una classe denominata `DocumentUtilities` a VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Aprire il documento (per Word) o una finestra di progettazione del foglio di lavoro (per Excel) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.  
  
    > [!NOTE]  
    >  Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, si riceverà un messaggio di errore quando si imposta la **ReferenceAssemblyFromVbaProject** proprietà **True** . Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.  
  
8.  Fare clic su **OK** nel messaggio visualizzato. Questo messaggio per ricordare che se si aggiunge codice VBA alla cartella di lavoro o al documento mentre si eseguono il progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il codice VBA andranno perso alla successiva compilazione del progetto. Questo avviene perché il documento nella cartella di output di compilazione viene sovrascritto ogni volta che si compila il progetto.  
  
     A questo punto, Visual Studio configura il progetto in modo che il progetto VBA è possibile chiamare nell'assembly. Visual Studio aggiunge anche un metodo denominato `GetManagedClass` al progetto VBA. È possibile chiamare questo metodo ovunque nel progetto VBA per accedere alla classe esposta a VBA.  
  
9. Compilare il progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinazione di VBA con le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Procedura dettagliata: Chiamata di codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Procedura: esporre il codice a VBA in un Visual C&#35; progetto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  