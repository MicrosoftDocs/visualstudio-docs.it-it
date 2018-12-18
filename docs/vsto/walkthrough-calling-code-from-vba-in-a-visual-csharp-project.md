---
title: 'Procedura dettagliata: Chiamata di codice da VBA in un progetto Visual c# | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 109ae2e89cf30078c910ff313ea203c576906037
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-calling-code-from-vba-in-a-visual-c-project"></a>Procedura dettagliata: chiamata di codice da VBA in un progetto Visual C#
  Questa procedura dettagliata illustra come chiamare un metodo in una personalizzazione a livello di documento di Microsoft Office Excel da codice Visual Basic, Applications Edition (VBA) contenuto nella cartella di lavoro. La procedura comporta tre passaggi di base: aggiungere un metodo alla classe dell'elemento host `Sheet1` , esporre il metodo al codice VBA nella cartella di lavoro e quindi chiamare il metodo dal codice VBA contenuto nella cartella di lavoro.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Benché questa procedura dettagliata usi Excel in modo specifico, i concetti illustrati sono applicabili anche ai progetti a livello di documento di Word.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di una cartella di lavoro che contiene codice VBA.  
  
-   Concessione dell'attendibilità al percorso della cartella di lavoro tramite il Centro protezione di Excel.  
  
-   Aggiunta di un metodo alla classe dell'elemento host `Sheet1` .  
  
-   Estrazione di un'interfaccia dalla classe dell'elemento host `Sheet1` .  
  
-   Esposizione del metodo al codice VBA.  
  
-   Chiamata del metodo dal codice VBA.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-a-workbook-that-contains-vba-code"></a>Creazione di una cartella di lavoro che contiene codice VBA.  
 Il primo passaggio consiste nel creare una cartella di lavoro con attivazione macro contenente una macro VBA semplice. Prima di potere esporre codice in una personalizzazione a VBA, è necessario che la cartella di lavoro includa già codice VBA. In caso contrario, Visual Studio non può modificare il progetto VBA per consentire al codice VBA di eseguire chiamate nell'assembly di personalizzazione.  
  
 Se si ha già una cartella di lavoro contenente codice VBA che si vuole usare, è possibile ignorare questo passaggio.  
  
#### <a name="to-create-a-workbook-that-contains-vba-code"></a>Per creare una cartella di lavoro contenente codice VBA  
  
1.  Avviare Excel.  
  
2.  Salvare il documento attivo come un **cartella di lavoro (\*xlsm)** con il nome **WorkbookWithVBA**. Salvarla in un percorso a propria scelta, ad esempio, il desktop.  
  
3.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Nel gruppo **Codice** , selezionare **Visual Basic**.  
  
     Viene aperto Microsoft Visual Basic Editor.  
  
5.  Nella finestra, **Progetto** , fare doppio clic su **ThisWorkbook**.  
  
     Viene aperto il file di codice relativo all'oggetto `ThisWorkbook` .  
  
6.  Aggiungere il codice VBA seguente al file di codice. Questo codice definisce una funzione semplice che non esegue alcuna operazione. L'unico scopo di questa funzione è garantire l'esistenza di un progetto VBA nella cartella di lavoro. Tale requisito dovrà essere soddisfatto in alcuni passaggi successivi di questa procedura dettagliata.  
  
    ```  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Salvare il documento e uscire da Excel.  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 A questo punto è possibile creare un progetto a livello di documento di Excel che usa la cartella di lavoro con attivazione macro appena creata.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro Modelli espandere, **Visual C#**quindi espandere **Office/SharePoint**.  
  
4.  Selezionare il nodo **Componenti aggiuntivi di Office** .  
  
5.  Nell'elenco di modelli di progetto selezionare il progetto **Cartella di lavoro di Excel 2010** o **Cartella di lavoro di Excel 2013** .  
  
6.  Nella casella **Nome** digitare **CallingCodeFromVBA**.  
  
7.  Fare clic su **OK**.  
  
     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .  
  
8.  Selezionare **Copia un documento esistente**e, nella casella **Percorso completo del documento esistente** , specificare il percorso della cartella di lavoro **WorkbookWithVBA** creata in precedenza. Se si ha già una cartella di lavoro con attivazione macro che si vuole usare, specificare invece il percorso di questa cartella di lavoro.  
  
9. Scegliere **Fine**.  
  
     In[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene aperta la cartella di lavoro **WorkbookWithVBA** nella finestra di progettazione e viene aggiunto il progetto **CallingCodeFromVBA** a **Esplora soluzioni**.  
  
## <a name="trusting-the-location-of-the-workbook"></a>Concessione dell'attendibilità al percorso della cartella di lavoro  
 Per poter esporre il codice contenuto nella soluzione al codice VBA contenuto nella cartella di lavoro, è necessario che quest'ultima sia impostata come attendibile per l'esecuzione. Esistono diversi modi per eseguire tale operazione. In questa esercitazione si completerà questa attività concedendo l'attendibilità al percorso della cartella di lavoro nel **Centro protezione** in Excel.  
  
#### <a name="to-trust-the-location-of-the-workbook"></a>Per concedere l'attendibilità al percorso della cartella di lavoro  
  
1.  Avviare Excel.  
  
2.  Scegliere la scheda **File** .  
  
3.  Fare clic sul pulsante **Opzioni di Excel** .  
  
4.  Nel riquadro delle categorie fare clic su **Centro protezione**.  
  
5.  Nel riquadro dei dettagli fare clic su Impostazioni **Centro protezione**.  
  
6.  Nel riquadro delle categorie fare clic su **Percorsi attendibili**.  
  
7.  Nel riquadro dei dettagli fare clic su **Aggiungi nuovo percorso**.  
  
8.  Nella finestra di dialogo **Percorso attendibile di Microsoft Office** passare alla cartella contenente il progetto **CallingCodeFromVBA** .  
  
9. Selezionare **Considera attendibili anche le sottocartelle di questo percorso**.  
  
10. Nella finestra di dialogo **Percorso attendibile di Microsoft Office** fare clic su **OK**.  
  
11. Scegliere **OK** nella finestra di dialogo **Centro protezione**.  
  
12. Scegliere **OK** nella finestra di dialogo **Opzioni di Excel**.  
  
13. Uscire da **Excel**.  
  
## <a name="adding-a-method-to-the-sheet1-class"></a>Aggiunta di un metodo alla classe Sheet1  
 Ora che il progetto VBA è configurato, aggiungere un metodo pubblico alla classe dell'elemento host `Sheet1` che è possibile chiamare dal codice VBA.  
  
#### <a name="to-add-a-method-to-the-sheet1-class"></a>Per aggiungere un metodo alla classe Sheet1  
  
1.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **Sheet1.cs**, quindi scegliere **Visualizza codice**.  
  
     Il file **Sheet1.cs** verrà aperto nell'editor del codice.  
  
2.  Aggiungere il codice seguente alla classe `Sheet1` . Il metodo `CreateVstoNamedRange` crea un nuovo oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> in corrispondenza dell'intervallo specificato. Verrà creato anche un gestore eventi per l'evento <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> della classe <xref:Microsoft.Office.Tools.Excel.NamedRange>. Più avanti nella procedura dettagliata il metodo `CreateVstoNamedRange` verrà chiamato dal codice VBA contenuto nel documento.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]  
  
3.  Aggiungere il metodo seguente alla classe `Sheet1` . Questo metodo esegue l'override del metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> per restituire l'istanza corrente della classe `Sheet1` .  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]  
  
4.  Applicare gli attributi seguenti prima della prima riga della dichiarazione della classe `Sheet1` . Questi attributi rendono visibile la classe a COM, ma senza generare un'interfaccia di classe.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]  
  
## <a name="extracting-an-interface-for-the-sheet1-class"></a>Estrazione di un'interfaccia dalla classe Sheet1  
 Prima di potere esporre il metodo `CreateVstoNamedRange` al codice VBA, è necessario creare un'interfaccia pubblica che definisce questo metodo ed esporre l'interfaccia a COM.  
  
#### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Per estrarre un'interfaccia per la classe Sheet1  
  
1.  Nel file di codice **Sheet1.cs** fare clic in un punto qualsiasi nella classe `Sheet1` .  
  
2.  Scegliere **Estrai interfaccia** dal menu **Effettua refactoring**.  
  
3.  Nella casella **Selezionare i membri pubblici per l'interfaccia** della finestra di dialogo **Estrai interfaccia** fare clic sulla voce relativa al metodo `CreateVstoNamedRange` .  
  
4.  Fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] genera una nuova interfaccia denominata `ISheet1`e modifica la definizione della classe `Sheet1` , in modo che implementi l'interfaccia `ISheet1` . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre anche il file **ISheet1.cs** nell'editor di codice.  
  
5.  Nel file **ISheet1.cs** sostituire la dichiarazione di interfaccia `ISheet1` con il codice seguente. Questo codice rende pubblica l'interfaccia `ISheet1` e applica l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> per rendere visibile l'interfaccia a COM.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]  
  
6.  Compilare il progetto.  
  
## <a name="exposing-the-method-to-vba-code"></a>Esposizione del metodo al codice VBA  
 Per esporre il metodo `CreateVstoNamedRange` al codice VBA nella cartella di lavoro, impostare la proprietà **ReferenceAssemblyFromVbaProject** dell'elemento host `Sheet1` su **True**.  
  
#### <a name="to-expose-the-method-to-vba-code"></a>Per esporre il metodo al codice VBA  
  
1.  In **Esplora soluzioni**fare doppio clic su **Sheet1.cs**.  
  
     Il file **WorkbookWithVBA** verrà aperto nella finestra di progettazione, con Sheet1 visibile.  
  
2.  Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.  
  
3.  Fare clic su **OK** nel messaggio visualizzato.  
  
4.  Compilare il progetto.  
  
## <a name="calling-the-method-from-vba-code"></a>Chiamata del metodo dal codice VBA  
 A questo punto è possibile chiamare il metodo `CreateVstoNamedRange` dal codice VBA contenuto nella cartella di lavoro.  
  
> [!NOTE]  
>  Questa procedura dettagliata prevede l'aggiunta di codice VBA alla cartella di lavoro durante l'esecuzione del debug del progetto. Se si ricompila il progetto, il codice VBA aggiunto a questo documento verrà sovrascritto. Infatti, Visual Studio sostituisce il documento contenuto nella cartella dell'output di compilazione con una copia del documento contenuto nella cartella del progetto principale. Se si vuole salvare il codice VBA è possibile copiarlo nel documento contenuto nella cartella del progetto. Per altre informazioni, vedere [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### <a name="to-call-the-method-from-vba-code"></a>Per chiamare il metodo dal codice VBA  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Nella scheda **Sviluppatore** fare clic su **Visual Basic** nel gruppo **Codice**.  
  
     Viene aperto Microsoft Visual Basic Editor.  
  
3.  Scegliere **Modulo** dal menu **Inserisci**.  
  
4.  Aggiungere al nuovo modulo il codice seguente.  
  
     Questo codice chiama il metodo `CreateTable` nell'assembly di personalizzazione. La macro accede a questo metodo usando il metodo globale `GetManagedClass` per accedere alla classe `Sheet1` dell'elemento host esposta al codice VBA. Il metodo `GetManagedClass` è stato generato automaticamente nel passaggio precedente della procedura dettagliata in cui è stata impostata la proprietà **ReferenceAssemblyFromVbaProject** .  
  
    ```  
    Sub CallVSTOMethod()  
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1  
        Set VSTOSheet1 = GetManagedClass(Sheet1)  
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")  
    End Sub  
    ```  
  
5.  Premere F5.  
  
6.  Nella cartella di lavoro aperta fare clic sulla cella **A1** in **Sheet1**. Verificare che venga visualizzata la finestra di messaggio.  
  
7.  Uscire da Excel senza salvare le modifiche.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Altre informazioni su come chiamare elementi di codice in soluzioni Office da VBA sono disponibili negli argomenti seguenti:  
  
-   Chiamare il codice in un elemento host in una personalizzazione di Visual Basic da VBA. Questo processo è diverso dal processo usato per Visual C#. Per ulteriori informazioni, vedere [procedura dettagliata: chiamata di codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  
  
-   Chiamare codice in un componente aggiuntivo VSTO da VBA. Per ulteriori informazioni, vedere [procedura dettagliata: chiamata di codice in un componente aggiuntivo VSTO da VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [How to: Expose Code to VBA in a Visual Basic Project](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Procedura: esporre il codice a VBA in un Visual C &#35; Progetto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Procedura dettagliata: chiamata di codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
  