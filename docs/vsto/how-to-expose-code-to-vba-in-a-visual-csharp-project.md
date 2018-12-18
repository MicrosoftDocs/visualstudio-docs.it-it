---
title: 'Procedura: esporre il codice a VBA in un progetto Visual c# | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 1b750137a52d30688f69c825f83f72c7cbeebe45
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Procedura: esporre il codice a VBA in un progetto Visual C#
  Se si desidera che i due tipi di codice per interagire tra loro, è possibile esporre codice in un progetto di Visual Basic in Visual c# per il codice Applications (VBA).  
  
 Il processo di Visual c# è diverso dal processo di Visual Basic. Per ulteriori informazioni, vedere [procedura: esporre il codice a VBA in un progetto di Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="exposing-code-in-a-visual-c-project"></a>Esposizione di codice in un progetto Visual c#  
 Per consentire al codice VBA chiamare codice in un progetto Visual c#, modificare il codice in modo che sia visibile a COM e quindi impostare il **ReferenceAssemblyFromVbaProject** proprietà **True** nella finestra di progettazione.  
  
 Per una procedura dettagliata viene illustrato come chiamare un metodo in un progetto Visual c# da VBA, vedere [procedura dettagliata: chiamata di codice da VBA in un Visual C &#35; Progetto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Per esporre il codice in un progetto Visual c# da VBA  
  
1.  Aprire o creare un progetto a livello di documento che si basa su un documento di Word, cartella di lavoro di Excel o modello di Excel che supporta le macro e che contiene già codice VBA.  
  
     Per ulteriori informazioni sui formati di file del documento che supportano le macro, vedere [combinazione di VBA e le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Questa funzionalità non può essere usata nei progetti Modello di Word,  
  
2.  Verificare che il codice VBA nel documento è possibile eseguire senza chiedere conferma all'utente di attivare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.  
  
3.  Aggiungere il membro che si desidera esporre a VBA a una classe pubblica nel progetto e dichiarare il nuovo membro come **pubblica**.  
  
4.  Applicare la seguente istruzione <xref:System.Runtime.InteropServices.ComVisibleAttribute> e <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributi alla classe che si sta esponendo a VBA. Questi attributi rendono visibile la classe a COM, ma senza generare un'interfaccia di classe.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Eseguire l'override di **GetAutomationObject** metodo di una classe di elementi host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA:  
  
    -   Se si sta esponendo a VBA una classe dell'elemento host, eseguire l'override di **GetAutomationObject** metodo che appartiene a questa classe e restituisce l'istanza corrente della classe.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Se si espone una classe che non è un elemento host su VBA, eseguire l'override di **GetAutomationObject** metodo di qualsiasi host elemento nel progetto e restituire un'istanza della classe di elementi non host. Ad esempio, il codice seguente si presuppone che si sta esponendo a una classe denominata `DocumentUtilities` a VBA.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Per altre informazioni sugli elementi host, vedere [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Estrarre un'interfaccia dalla classe che si sta esponendo a VBA. Nel **Estrai interfaccia** finestra di dialogo, selezionare i membri pubblici che si desidera includere nella dichiarazione di interfaccia. Per ulteriori informazioni, vedere [Estrai interfaccia Refactoring](../ide/reference/extract-interface.md).
  
7.  Aggiungere il **pubblica** parola chiave per la dichiarazione di interfaccia.  
  
8.  Rendere visibile a COM l'interfaccia aggiungendo quanto segue <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributo all'interfaccia.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Aprire il documento (per Word) o un foglio di lavoro (per Excel) nella finestra di progettazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.  
  
    > [!NOTE]  
    >  Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, si riceverà un messaggio di errore quando si imposta la **ReferenceAssemblyFromVbaProject** proprietà **True**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.  
  
11. Fare clic su **OK** nel messaggio visualizzato. Questo messaggio per ricordare che se si aggiungono VBA nella cartella di lavoro di codice o documento quando si esegue il progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il codice VBA andranno persi la volta successiva che si compila il progetto. Questo avviene perché il documento nella compilazione output cartella viene sovrascritto ogni volta che si compila il progetto.  
  
     A questo punto, Visual Studio configura il progetto in modo che il progetto VBA è possibile chiamare nell'assembly. Visual Studio aggiunge anche un metodo denominato `GetManagedClass` al progetto VBA. È possibile chiamare questo metodo ovunque nel progetto VBA per accedere alla classe esposta a VBA.  
  
12. Compilare il progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Procedura dettagliata: Chiamata codice da VBA in un Visual C &#35; Progetto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Procedura: Esporre il codice a VBA in un progetto Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  