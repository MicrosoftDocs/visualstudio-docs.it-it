---
title: Scrittura di codice nelle soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c6119db86fdd67079b63434a6bb494cb04cd31d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="writing-code-in-office-solutions"></a>Scrittura di codice nelle soluzioni Office
  Alcuni aspetti della scrittura del codice nei progetti di Office presentano delle differenze rispetto ad altri tipi di progetti in Visual Studio. Molte di queste differenze riguardano la modalità di esposizione dei modelli a oggetti di Office al codice gestito. Le altre differenze sono correlate alla creazione di progetti di Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="managed-code-and-office-programming"></a>Codice gestito e programmazione di Office  
 La tecnologia fondamentale che consente di creare una soluzione Microsoft Office integrata è costituita dall'automazione, che fa parte della tecnologia COM (Component Object Model). Grazie all'automazione è possibile usare codice per creare e controllare gli oggetti software esposti da qualsiasi applicazione, DLL o controllo ActiveX in grado di supportare le interfacce programmatiche.  
  
### <a name="understanding-primary-interop-assemblies"></a>Informazioni sugli assembly di interoperabilità primari  
 La maggior parte delle funzionalità delle applicazioni di Microsoft Office viene esposta all'automazione. Tuttavia, non è possibile usare direttamente il codice gestito (ad esempio Visual Basic o C#) per automatizzare le applicazioni di Office. Per automatizzare le applicazioni di Office mediante il codice gestito, è necessario usare gli assembly di interoperabilità primari di Office. Gli assembly di interoperabilità primari consentono l'interazione tra il codice gestito e il modello a oggetti COM delle applicazioni di Office.  
  
 Ogni applicazione di Microsoft Office dispone di un assembly di interoperabilità primario. Quando si crea un progetto di Office in Visual Studio, al progetto viene automaticamente aggiunto un riferimento all'assembly di interoperabilità primario appropriato. Per automatizzare le funzionalità di altre applicazioni di Office dal progetto, è necessario aggiungere manualmente un riferimento all'assembly di interoperabilità primario appropriato. Per altre informazioni, vedere [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
### <a name="using-primary-interop-assemblies-at-design-time-and-run-time"></a>Uso degli assembly di interoperabilità primari in fase di progettazione ed esecuzione  
 Per eseguire la maggior parte delle attività di sviluppo, gli assembly di interoperabilità primari di Office devono essere installati e registrati nella Global Assembly Cache del computer di sviluppo. Per altre informazioni, vedere [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 Gli assembly di interoperabilità primari di Office non sono richiesti per l'esecuzione di soluzioni Office sui computer degli utenti finali che dispongono di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive. Per altre informazioni, vedere [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="using-types-in-primary-interop-assemblies"></a>Uso dei tipi negli assembly di interoperabilità primari  
 Gli assembly di interoperabilità primari di Office contengono una combinazione di tipi che espongono il modello a oggetti delle applicazioni di Office e i tipi aggiuntivi dell'infrastruttura che non possono essere usati direttamente nel codice. Per una panoramica dei tipi negli assembly di interoperabilità primari di Office, vedere [Panoramica su classi e interfacce negli assembly di interoperabilità primari](http://msdn.microsoft.com/en-us/da92dc3c-8209-44de-8095-a843659368d5).  
  
 Poiché i tipi negli assembly di interoperabilità primari di Office corrispondono ai tipi nei modelli a oggetti COM, la modalità di utilizzo di questi tipi spesso è differente dagli altri tipi gestiti. Ad esempio, la modalità di chiamata dei metodi che hanno parametri facoltativi in un assembly di interoperabilità primario di Office varia in base al linguaggio di programmazione che si sta usando nel progetto. Per altre informazioni, vedere i seguenti argomenti:  
  
-   [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md).  
  
-   [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).  
  
## <a name="programming-model-of-office-projects"></a>Modello di programmazione di progetti di Office  
 Tutti i progetti di Office includono una o più classi generate che forniscono il punto di ingresso per il codice. Queste classi forniscono anche accesso al modello a oggetti dell'applicazione host e accesso a funzionalità quali riquadri azioni e riquadri attività personalizzati.  
  
### <a name="understanding-the-generated-classes"></a>Informazioni sulle classi generate  
 In progetti a livello di documento per Excel e Word, la classe generata assomiglia a un oggetto di primo livello nel modello a oggetti dell'applicazione. Ad esempio, la classe generata `ThisDocument` di un progetto a livello di documento di Word fornisce gli stessi membri della classe <xref:Microsoft.Office.Interop.Word.Document> nel modello a oggetti di Word. Per altre informazioni sulle classi generate nei progetti a livello di documento, vedere [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 I progetti di componente aggiuntivo VSTO forniscono una classe generata denominata `ThisAddIn`. Questa classe non assomiglia a una classe del modello a oggetti dell'applicazione host. Al contrario, questa classe rappresenta il componente aggiuntivo VSTO stesso e fornisce membri che è possibile usare per accedere al modello a oggetti dell'applicazione host e ad altre funzionalità disponibili per i componenti aggiuntivi VSTO. Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Tutte le classi generate nei progetti di Office includono gestori eventi `Startup` e `Shutdown` . Per iniziare a scrivere codice, in genere viene aggiunto codice a tali gestori eventi. Per inizializzare il componente aggiuntivo VSTO, è possibile aggiungere codice al gestore eventi `Startup` . Per pulire le risorse usate dal componente aggiuntivo VSTO, è possibile aggiungere codice al gestore eventi `Shutdown` . Per altre informazioni, vedere [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
### <a name="accessing-the-generated-classes-at-run-time"></a>Accesso alle classi generate in fase di esecuzione  
 Quando viene caricata una soluzione Office, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea un'istanza di ognuna delle classi generate nel progetto. È possibile accedere a questi oggetti da qualsiasi codice del progetto tramite la classe `Globals` . Ad esempio, è possibile usare la classe `Globals` per chiamare codice nella classe `ThisAddIn` da un gestore eventi di un pulsante della barra multifunzione in un componente aggiuntivo VSTO.  
  
 Per ulteriori informazioni, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="namespace-considerations-in-office-solutions"></a>Considerazioni dello spazio dei nomi nelle soluzioni Office  
 Non è possibile modificare lo *spazio dei nomi predefinito* (o *spazio dei nomi radice* in Visual Basic) di un progetto di Office dopo averlo creato. Lo spazio dei nomi predefinito corrisponderà sempre al nome del progetto specificato durante la creazione del progetto. Se si rinomina il progetto, lo spazio dei nomi predefinito non viene modificato. Per ulteriori informazioni su spazio dei nomi predefinito nei progetti, vedere [pagina applicazione, Progettazione progetti &#40;C&#35; &#41; ](/visualstudio/ide/reference/application-page-project-designer-csharp) e [pagina applicazione, Progettazione progetti &#40;Visual Basic&#41; ](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
### <a name="changing-the-namespace-of-host-item-classes-in-c-projects"></a>Modifica dello spazio dei nomi delle classi dell'elemento host in progetti C#  
 Le classi dell'elemento host (ad esempio, le classi `ThisAddIn`, `ThisWorkbook`o `ThisDocument` ) hanno spazi dei nomi specifici nei progetti di Office di Visual C#. Per impostazione predefinita, lo spazio dei nomi per gli elementi host nel progetto corrisponde al nome del progetto specificato durante la creazione del progetto.  
  
 Per modificare lo spazio dei nomi degli elementi host in un progetto di Office di Visual C#, usare la proprietà **Spazio dei nomi per elemento host** . Per ulteriori informazioni, vedere [proprietà nei progetti di Office](../vsto/properties-in-office-projects.md).  
  
## <a name="supported-programming-languages-in-office-projects"></a>Linguaggi di programmazione supportati nei progetti di Office  
 I modelli di progetto di Office in Visual Studio supportano solo i linguaggi di programmazione Visual Basic e Visual C#. Pertanto, questi modelli di progetto sono disponibili solo in corrispondenza dei nodi **Visual Basic** e **Visual C#** della finestra di dialogo **Nuovo progetto** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="language-choice-and-office-programming"></a>Scelta del linguaggio e programmazione di Office  
 Microsoft Office e VBA (Visual Basic, Applications Edition) sono stati sviluppati per l'integrazione al fine di ottimizzare il flusso di lavoro di personalizzazione delle applicazioni. Visual Basic ha ereditato alcuni di tali sviluppi. Ad esempio, in Visual Basic vengono supportati i parametri facoltativi e quindi si scrive meno codice quando si chiamano alcuni metodi negli assembly di interoperabilità primari di Microsoft Office rispetto a Visual C#.  
  
## <a name="programming-with-visual-basic-vs-visual-c-in-office-solutions"></a>Programmazione con Visual Basic e  Visual C# nelle soluzioni Office  
 È possibile creare soluzioni Office usando Visual Basic o Visual C#. Poiché i modelli a oggetti di Microsoft Office sono stati progettati per l'utilizzo con Microsoft VBA (Visual Basic, Applications Edition), gli sviluppatori di Visual Basic possono usare agevolmente gli oggetti esposti dalle applicazioni di Microsoft Office. Gli sviluppatori di Visual C# possono usare gran parte delle stesse funzionalità usate dagli sviluppatori di Visual Basic, ma in alcuni casi devono scrivere codice aggiuntivo per usare i modelli a oggetti di Office. Esistono inoltre alcune differenze tra le funzionalità di programmazione di base usate nello sviluppo di applicazioni per Office e il codice gestito scritto in Visual Basic e C#.  
  
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Differenze principali tra Visual Basic e Visual C#  
 Nella tabella seguente sono illustrate le differenze principali tra Visual Basic e Visual C# nello sviluppo di applicazioni per Office.  
  
|Funzionalità|Descrizione|Supporto in Visual Basic|Supporto in Visual C#|  
|-------------|-----------------|--------------------------|------------------------|  
|Parametri facoltativi|Molti metodi di Microsoft Office hanno parametri che non sono richiesti quando si chiama il metodo. Se per il parametro non viene passato alcun valore, verrà usato un valore predefinito.|Visual Basic supporta i parametri facoltativi.|Visual C# supporta i parametri facoltativi nella maggior parte dei casi. Per ulteriori informazioni, vedere [parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Passaggio di parametri per riferimento|I parametri facoltativi nella maggior parte degli assembly di interoperabilità primari di Microsoft Office possono essere passati per valore. Tuttavia, in alcuni assembly di interoperabilità primari i parametri facoltativi che accettano i tipi riferimento devono essere passati per riferimento.<br /><br /> Per ulteriori informazioni sui parametri di tipo valore e riferimento, vedere [il passaggio di argomenti per valore e per riferimento &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (per Visual Basic) e [passaggio di parametri &#40;C&#35; Guida per programmatori&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Non è richiesta alcuna attività aggiuntiva per il passaggio di parametri in base al riferimento. Il compilatore di Visual Basic passa automaticamente i parametri per riferimento quando necessario.|Nella maggior parte dei casi, il compilatore di Visual C# passa automaticamente i parametri per riferimento quando necessario. Per ulteriori informazioni, vedere [parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Proprietà con parametri|Alcune proprietà accettano parametri e fungono da funzioni di sola lettura.|Visual Basic supporta le proprietà che accettano parametri.|Visual C# supporta le proprietà che accettano parametri.|  
|Associazione tardiva|L'associazione tardiva comporta la determinazione delle proprietà degli oggetti in fase di esecuzione, anziché eseguire il cast delle variabili al tipo di oggetto in fase di progettazione.|Visual Basic esegue l'associazione tardiva quando **Option Strict** non è attiva. Quando **Option Strict** è attiva, è necessario convertire in modo esplicito gli oggetti e usare i tipi nello spazio dei nomi <xref:System.Reflection> per accedere ai membri ad associazione tardiva. Per altre informazioni, vedere [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).|Visual C# esegue l'associazione tardiva in progetti che hanno come destinazione [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Per altre informazioni, vedere [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).|  
  
## <a name="key-differences-between-office-development-and-managed-code"></a>Principali differenze tra lo sviluppo di applicazioni per Office e il codice gestito  
 Nella tabella seguente sono illustrate le differenze principali tra lo sviluppo di applicazioni per Office e il codice gestito scritto in Visual Basic e Visual C#.  
  
|Funzionalità|Descrizione|Supporto in Visual Basic e Visual C#|  
|-------------|-----------------|-----------------------------------------|  
|Indici di matrice|Il limite di matrice inferiore delle raccolte nelle applicazioni di Microsoft Office inizia con 1. Visual Basic e Visual C# usano matrici in base 0. Per altre informazioni, vedere [Array &#40;C&#35; Guida per programmatori&#41; ](/dotnet/csharp/programming-guide/arrays/index) e [matrici in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Per accedere al primo elemento di una raccolta del modello a oggetti di un'applicazione di Microsoft Office, usare l'indice 1 anziché 0.|  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Eventi nei progetti di Office](../vsto/events-in-office-projects.md)   
 [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)   
 [Sviluppo collaborativo di soluzioni Office](../vsto/collaborative-development-of-office-solutions.md)  
  
  