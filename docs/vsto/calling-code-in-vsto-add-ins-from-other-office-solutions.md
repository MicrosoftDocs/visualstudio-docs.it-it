---
title: Chiamata di codice nei componenti aggiuntivi VSTO da altre soluzioni Office | Documenti Microsoft
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
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c21ea9555a125503230faa92a5e6508c192a8175
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="calling-code-in-vsto-add-ins-from-other-office-solutions"></a>Chiamata di codice nei componenti aggiuntivi VSTO da altre soluzioni Office
  È possibile esporre un oggetto del componente aggiuntivo VSTO in altre soluzioni, ad esempio in altre soluzioni Microsoft Office. Questa funzionalità è utile se il componente aggiuntivo VSTO fornisce un servizio che si vuole usare anche in altre soluzioni. Ad esempio, se un componente aggiuntivo VSTO per Microsoft Office Excel esegue calcoli sui dati finanziari da un servizio Web, altre soluzioni possono eseguire tali calcoli chiamando il componente aggiuntivo VSTO di Excel in fase di esecuzione.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Questo processo prevede due passaggi principali:  
  
-   Nel componente aggiuntivo VSTO esporre un oggetto ad altre soluzioni.  
  
-   In un'altra soluzione accedere all'oggetto esposto dal componente aggiuntivo VSTO e chiamare i membri dell'oggetto.  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Tipi di soluzioni che possono chiamare il codice di un componente aggiuntivo  
 Un oggetto in un componente aggiuntivo VSTO può essere esposto ai tipi di soluzioni seguenti:  
  
-   Codice Visual Basic, Applications Edition (VBA) di un documento caricato nello stesso processo dell'applicazione del componente aggiuntivo VSTO.  
  
-   Personalizzazioni a livello di documento caricate nello stesso processo dell'applicazione del componente aggiuntivo VSTO.  
  
-   Altri componenti aggiuntivi VSTO creati usando i modelli di progetto di Office in Visual Studio.  
  
-   Componenti aggiuntivi VSTO COM, ovvero componenti aggiuntivi VSTO che implementano direttamente l'interfaccia <xref:Extensibility.IDTExtensibility2> .  
  
-   Qualsiasi soluzione in esecuzione in un processo diverso dal componente aggiuntivo VSTO. Questi tipi di soluzioni sono detti anche *client out-of-process*. Sono incluse le applicazioni che automatizzano un'applicazione di Office, ad esempio Windows Form o un'applicazione console, e i componenti aggiuntivi VSTO caricati in un processo diverso.  
  
## <a name="exposing-objects-to-other-solutions"></a>Esposizione di oggetti ad altre soluzioni  
 Per esporre un oggetto del componente aggiuntivo VSTO ad altre soluzioni, eseguire la procedura seguente nel componente aggiuntivo:  
  
1.  Definire una classe da esporre ad altre soluzioni.  
  
2.  Eseguire l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> nella classe `ThisAddIn` . Restituire un'istanza della classe da esporre ad altre soluzioni.  
  
### <a name="defining-the-class-you-want-to-expose-to-other-solutions"></a>Definizione della classe da esporre ad altre soluzioni  
 Questa classe deve essere almeno pubblica, deve avere l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su **true**e deve esporre l'interfaccia [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) .  
  
 Il metodo consigliato per esporre l'interfaccia [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) consiste nell'eseguire la procedura seguente:  
  
1.  Definire un'interfaccia che dichiari i membri da esporre ad altre soluzioni. È possibile definire questa interfaccia nel progetto di componente aggiuntivo VSTO. È tuttavia consigliabile definire l'interfaccia in un progetto di libreria di classi separato, se si vuole esporre la classe a soluzioni non VBA. In questo modo, le soluzioni che chiamano il componente aggiuntivo VSTO possono fare riferimento all'interfaccia senza fare riferimento al progetto di componente aggiuntivo VSTO.  
  
2.  Applicare l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> a questa interfaccia e impostarlo su **true**.  
  
3.  Modificare la classe per implementare l'interfaccia.  
  
4.  Applicare il <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo alla classe e si imposta questo attributo su None valore il <xref:System.Runtime.InteropServices.ClassInterfaceType> enumerazione.  
  
5.  Se si vuole esporre la classe a client out-of-process, potrebbe anche essere necessario eseguire le operazioni seguenti:  
  
    -   Derivare la classe da <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Per altre informazioni, vedere [Esposizione di classi a client out-of-process](#outofproc).  
  
    -   Impostare la proprietà **Registra per interoperabilità COM** nel progetto in cui si definisce l'interfaccia. Questo passaggio è necessario solo se si vuole consentire ai client di usare l'associazione anticipata per effettuare chiamate nel componente aggiuntivo VSTO.  
  
 L'esempio di codice seguente illustra una classe `AddInUtilities` con un metodo `ImportData` che è possibile chiamare da altre soluzioni. Per visualizzare questo codice nel contesto di una procedura dettagliata più estesa, vedere [procedura dettagliata: chiamata di codice in un componente aggiuntivo VSTO da VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
 [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="exposing-classes-to-vba"></a>Esposizione di classi a VBA  
 Quando si esegue la procedura riportata sopra, il codice VBA può chiamare solo i metodi dichiarati nell'interfaccia. Il codice VBA non può chiamare altri metodi della classe, inclusi i metodi che la classe ottiene dalle classi base, ad esempio <xref:System.Object>.  
  
 In alternativa, è possibile esporre il [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) interfaccia impostando il <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo del valore AutoDispatch o AutoDual tra il <xref:System.Runtime.InteropServices.ClassInterfaceType> enumerazione. Se si esegue questa operazione, non è necessario dichiarare i metodi in un'interfaccia separata. Il codice VBA può tuttavia chiamare qualsiasi metodo pubblico e non statico della classe, inclusi i metodi ottenuti dalle classi base, ad esempio <xref:System.Object>. Inoltre, i client out-of-process che usano l'associazione anticipata non possono chiamare la classe.  
  
###  <a name="outofproc"></a> Esposizione di classi a client out-of-process  
 Per esporre una classe del componente aggiuntivo VSTO a client out-of-process, è necessario derivare la classe da <xref:System.Runtime.InteropServices.StandardOleMarshalObject> per assicurarsi che i client out-of-process possano chiamare l'oggetto componente aggiuntivo VSTO esposto. In caso contrario, i tentativi di ottenere un'istanza dell'oggetto esposto in un client out-of-process potrebbero non riuscire in modo imprevisto.  
  
 Questa situazione si verifica perché tutte le chiamate al modello a oggetti di un'applicazione di Office devono essere effettuate nel thread principale dell'interfaccia utente, mentre le chiamate da un client out-of-process all'oggetto arrivano in un thread RPC (Remote Procedure Call) arbitrario. Il meccanismo di marshalling COM in .NET Framework non cambia thread e tenta invece di effettuare il marshalling della chiamata all'oggetto nel thread RPC in ingresso anziché nel thread principale dell'interfaccia utente. Se l'oggetto è un'istanza di una classe che deriva da <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, viene effettuato automaticamente il marshalling delle chiamate in ingresso all'oggetto in relazione al thread in cui è stato creato l'oggetto esposto, che sarà il thread principale dell'interfaccia utente dell'applicazione host.  
  
 Per altre informazioni sull'uso dei thread nelle soluzioni Office, vedere [Threading Support in Office](../vsto/threading-support-in-office.md).  
  
### <a name="overriding-the-requestcomaddinautomationservice-method"></a>Override del metodo RequestComAddInAutomationService  
 L'esempio di codice seguente illustra come eseguire l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> nella classe `ThisAddIn` del componente aggiuntivo VSTO. Questo esempio presuppone che sia stata definita una classe denominata `AddInUtilities` da esporre ad altre soluzioni. Per visualizzare questo codice nel contesto di una procedura dettagliata più estesa, vedere [procedura dettagliata: chiamata di codice in un componente aggiuntivo VSTO da VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 Quando il componente aggiuntivo VSTO viene caricato, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama il metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Il runtime assegna l'oggetto restituito alla proprietà <xref:Microsoft.Office.Core.COMAddIn.Object%2A> di un oggetto <xref:Microsoft.Office.Core.COMAddIn> che rappresenta il componente aggiuntivo VSTO. Questo oggetto <xref:Microsoft.Office.Core.COMAddIn> è disponibile per altre soluzioni Office e per soluzioni che automatizzano Office.  
  
## <a name="accessing-objects-from-other-solutions"></a>Accesso agli oggetti da altre soluzioni  
 Per chiamare l'oggetto esposto del componente aggiuntivo VSTO, eseguire i passaggi seguenti nella soluzione client:  
  
1.  Ottenere l'oggetto <xref:Microsoft.Office.Core.COMAddIn> che rappresenta il componente aggiuntivo VSTO esposto. Client possono accedere tutti i disponibili componenti aggiuntivi VSTO usando la proprietà Application. COMAddIns nel modello a oggetti dell'applicazione host di Office.  
  
2.  Accedere alla proprietà <xref:Microsoft.Office.Core.COMAddIn.Object%2A> dell'oggetto <xref:Microsoft.Office.Core.COMAddIn> . Questa proprietà restituisce l'oggetto esposto dal componente aggiuntivo VSTO.  
  
3.  Chiamare i membri dell'oggetto esposto.  
  
 La modalità con cui si usa il valore restituito della proprietà <xref:Microsoft.Office.Core.COMAddIn.Object%2A> è diversa per i client VBA e i client non VBA. Per i client out-of-process, il codice aggiuntivo è necessario per evitare una possibile race condition.  
  
### <a name="accessing-objects-from-vba-solutions"></a>Accesso agli oggetti da soluzioni VBA  
 L'esempio di codice seguente illustra come usare VBA per chiamare un metodo esposto da un componente aggiuntivo VSTO. Questa macro VBA chiama un metodo denominato `ImportData` definito in un componente aggiuntivo VSTO denominato **ExcelImportData**. Per visualizzare questo codice nel contesto di una procedura dettagliata più estesa, vedere [procedura dettagliata: chiamata di codice in un componente aggiuntivo VSTO da VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
```  
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="accessing-objects-from-non-vba-solutions"></a>Accesso agli oggetti da soluzioni non VBA  
 In una soluzione non VBA è necessario eseguire il cast del valore della proprietà <xref:Microsoft.Office.Core.COMAddIn.Object%2A> all'interfaccia che viene implementata e quindi è possibile chiamare i metodi esposti nell'oggetto interfaccia. L'esempio di codice seguente illustra come chiamare il metodo `ImportData` da un componente aggiuntivo VSTO diverso creato usando gli strumenti di sviluppo per Office in Visual Studio.  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 In questo esempio, se si tenta di eseguire il cast del valore della proprietà <xref:Microsoft.Office.Core.COMAddIn.Object%2A> alla classe `AddInUtilities` invece che all'interfaccia `IAddInUtilities` , viene generata una <xref:System.InvalidCastException>.  
  
## <a name="see-also"></a>Vedere anche  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Procedura dettagliata: Chiamata di codice in un componente aggiuntivo VSTO da VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Personalizzazione delle funzionalità dell'interfaccia utente tramite le interfacce di estensibilità](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  