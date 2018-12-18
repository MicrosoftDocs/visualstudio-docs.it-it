---
title: Composizione di un test codificato dell'interfaccia utente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c449c0e23fa3effa693059ed6d0b6c4a61b8470c
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="anatomy-of-a-coded-ui-test"></a>Composizione di un test codificato dell'interfaccia utente

Quando si crea un test codificato dell'interfaccia utente in un progetto di test codificato dell'interfaccia utente, vengono aggiunti alcuni file alla soluzione. In questo argomento, si userà un test codificato dell'interfaccia utente di esempio per esaminare questi file.  
  
 **Requisiti**  
  
-   Visual Studio Enterprise  
  
## <a name="contents-of-a-coded-ui-test"></a>Contenuto di un test codificato dell'interfaccia utente  
 Quando si crea un test codificato dell'interfaccia utente, il **Generatore di test codificati dell'interfaccia utente** crea una mappa dell'interfaccia utente sottoposta a test, oltre ai metodi di test, ai parametri e alle asserzioni per tutti i test. Crea anche un file di classe per ogni test.  
  
|File|Sommario|Modificabile?|  
|----------|--------------|---------------|  
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Sezione delle dichiarazioni](#UIMapDesignerFile)<br /><br /> [Classe UIMap](#UIMapClass) (parziale, generata automaticamente)<br /><br /> [Metodi](#UIMapMethods)<br /><br /> [Proprietà](#UIMapProperties)|No|  
|[UIMap.cs](#UIMapCS)|[Classe UIMap](#UIMapCS) (parziale)|Yes|  
|[CodedUITest1.cs](#CodedUITestCS)|[Classe CodedUITest1](#CodedUITestCS)<br /><br /> [Metodi](#CodedUITestMethods)<br /><br /> [Proprietà](#CodedUITestProperties)|Yes|  
|[UIMap.uitest](#UIMapuitest)|Mappa XML dell'interfaccia utente per il test.|No|  
  
###  <a name="UIMapDesignerFile"></a> UIMap.Designer.cs  
 Questo file contiene il codice creato automaticamente dal **Generatore di test codificati dell'interfaccia utente** quando viene creato un test. Questo file viene ricreato ogni volta che un test viene modificato e quindi non è un file in cui si possa aggiungere o modificare il codice.  
  
#### <a name="declarations-section"></a>Sezione delle dichiarazioni  
 Questa sezione include le seguenti dichiarazioni per un'interfaccia utente di Windows.  
  
```csharp  
using System;  
using System.CodeDom.Compiler;  
using System.Collections.Generic;  
using System.Drawing;  
using System.Text.RegularExpressions;  
using System.Windows.Input;  
using Microsoft.VisualStudio.TestTools.UITest.Extension;  
using Microsoft.VisualStudio.TestTools.UITesting;  
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;  
using MouseButtons = System.Windows.Forms.MouseButtons;  
```  
  
 Lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> viene incluso per un'interfaccia utente di Windows (UI). Per l'interfaccia utente di una pagina Web, lo spazio dei nomi sarebbe <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>, mentre per un'interfaccia utente di Windows Presentation Foundation, sarebbe <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.  
  
####  <a name="UIMapClass"></a> Classe UIMap  
 La sezione successiva del file è la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>.  
  
```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public partial class UIMap  
```
  
Il codice della classe inizia con <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> applicato alla classe, che viene dichiarata come classe parziale. Si noterà che l'attributo viene applicato anche a ogni classe in questo file. L'altro file che può contenere altro codice per questa classe è `UIMap.cs`, di cui si parlerà più avanti.  

La classe `UIMap` generata include il codice per ogni metodo specificato quando è stato registrato il test.  

```csharp
public void LaunchCalculator()  
public void AddItems()  
public void VerifyTotal()  
public void CleanUp()  
```

Questa parte della classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> include anche il codice generato per ogni proprietà necessaria ai metodi.

```csharp
public virtual LaunchCalculatorParams LaunchCalculatorParams  
public virtual AddItemsParams AddItemsParams  
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues  
public virtual CalculateItemsParams CalculateItemsParams  
public virtual VerifyMathAppTotalExpectedValues   
    VerifyMathAppTotalExpectedValues  
public UIStartMenuWindow UIStartMenuWindow  
public UIRunWindow UIRunWindow  
public UICalculatorWindow UICalculatorWindow  
public UIStartWindow UIStartWindow  
public UIMathApplicationWindow UIMathApplicationWindow  
```
  
#####  <a name="UIMapMethods"></a> Metodi UIMap  
 Ogni metodo ha una struttura simile a quella del metodo `AddItems()`. Questo è illustrato più dettagliatamente nel codice, che viene presentato con le interruzioni di riga per maggiore chiarezza.

```csharp
/// <summary>  
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.  
/// </summary>  
public void AddItems()  
{  
    #region Variable Declarations  
    WinControl uICalculatorDialog =   
        this.UICalculatorWindow.UICalculatorDialog;  
    WinEdit uIItemEdit =   
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;  
    #endregion  
  
    // Type '{NumPad7}' in 'Calculator' Dialog  
    Keyboard.SendKeys(uICalculatorDialog,   
        this.AddItemsParams.UICalculatorDialogSendKeys,   
        ModifierKeys.None);  
  
    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    Keyboard.SendKeys(uIItemEdit,   
        this.AddItemsParams.UIItemEditSendKeys,   
        ModifierKeys.None);  
}
```

Il commento summary per la definizione di ogni metodo indica quale classe usare per i valori dei parametri di quel metodo. In questo caso, si tratta della classe `AddItemsParams`, che viene definita più avanti nel file `UIMap.cs` ed è anche il tipo di valore restituito dalla proprietà `AddItemsParams`.  
  
 All'inizio del codice del metodo è presente un'area `Variable Declarations` che definisce le variabili locali per gli oggetti dell'interfaccia utente che verranno usati dal metodo.  
  
 In questo metodo, sia `UIItemWindow` che `UIItemEdit` sono proprietà accessibili usando la classe `UICalculatorWindow`, che viene definita più avanti nel file `UIMap.cs`.  
  
 Poi vengono le righe che inviano il testo dalla tastiera all'applicazione Calculator usando le proprietà dell'oggetto `AddItemsParams`.  
  
 Il metodo `VerifyTotal()` ha una struttura molto simile e include il codice di asserzione seguente.  

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '  
Assert.AreEqual(  
    this.VerifyTotalExpectedValues.UIItemEditText,   
    uIItemEdit.Text);  
```

 Il nome della casella di testo risulta sconosciuto perché lo sviluppatore dell'applicazione Windows Calculator non ha fornito un nome disponibile pubblicamente per il controllo. Il metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> ha esito negativo quando il valore effettivo non è uguale al valore previsto, il che potrebbe causare la mancata riuscita del test. Si noti inoltre che il valore previsto include un separatore decimale seguito da uno spazio. Se si dovesse modificare la funzionalità di questo particolare test, sarà necessario consentire il separatore decimale lo spazio.  
  
#####  <a name="UIMapProperties"></a> Proprietà UIMap  
 Il codice per ogni proprietà è anche standard in tutta la classe. Il seguente codice per la proprietà `AddItemsParams` viene usato nel metodo `AddItems()`.  
  
```csharp
public virtual AddItemsParams AddItemsParams  
{  
    get  
    {  
        if ((this.mAddItemsParams == null))  
        {  
            this.mAddItemsParams = new AddItemsParams();  
        }  
        return this.mAddItemsParams;  
    }  
}
```

 Si noti che la proprietà usa una variabile locale privata denominata `mAddItemsParams` per contenere il valore prima di restituirlo. Il nome della proprietà e il nome della classe per l'oggetto restituito sono gli stessi. La classe viene definita più avanti nel file `UIMap.cs`.  
  
 Ogni classe restituita da una proprietà è strutturata in modo analogo. La seguente è la classe `AddItemsParams`.  

```csharp
/// <summary>  
/// Parameters to be passed into 'AddItems'  
/// </summary>  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public class AddItemsParams  
{  
    #region Fields  
    /// <summary>  
    /// Type '{NumPad7}' in 'Calculator' Dialog  
    /// </summary>  
    public string UICalculatorDialogSendKeys = "{NumPad7}";  
  
    /// <summary>  
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    /// </summary>  
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";  
    #endregion  
}
```

Come tutte le classi nel file `UIMap.cs`, anche questa inizia con <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. In questa piccola classe è presente un'area `Fields` che definisce le stringhe da usare come parametri per il metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> usato nel metodo `UIMap.AddItems()` illustrato in precedenza. È possibile scrivere il codice per sostituire i valori in questi campi delle stringhe prima che venga chiamato il metodo in cui sono usati questi parametri.  

###  <a name="UIMapCS"></a> UIMap.cs  
 Per impostazione predefinita, questo file contiene una classe `UIMap` parziale senza metodi o proprietà.  
  
#### <a name="uimap-class"></a>Classe UIMap  
 In questa classe è possibile creare il codice personalizzato per estendere la funzionalità della classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>. Il codice creato in questo file non verrà rigenerato dal **Generatore di test codificati dell'interfaccia utente** ogni volta che un test viene modificato.  
  
 Tutte le parti di <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> possono usare i metodi e le proprietà di qualsiasi altra parte della classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>.  
  
###  <a name="CodedUITestCS"></a> CodedUITest1.cs  
 Questo file viene generato dal **Generatore di test codificati dell'interfaccia utente**, ma non viene ricreato ogni volta che il test viene modificato, di conseguenza il codice presente in questo file è modificabile. Il nome del file viene generato dal nome specificato per il test quando è stato creato.  
  
#### <a name="codeduitest1-class"></a>Classe CodedUITest1

Per impostazione predefinita, questo file contiene la definizione per una sola classe.

```csharp
[CodedUITest]  
public class CodedUITest1  
```

<xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute> viene automaticamente applicato alla classe. In questo modo il framework di test può riconoscerlo come estensione di test. Si noti inoltre che non si tratta di una classe parziale. Tutto il codice della classe è contenuto in questo file.  
  
#####  <a name="CodedUITestProperties"></a> Proprietà di CodedUITest1  
 La classe contiene due proprietà predefinite che si trovano nella parte inferiore del file. Non devono essere modificate.  
  
```csharp
/// <summary>  
/// Gets or sets the test context which provides  
/// information about and functionality for the current test run.  
///</summary>  
public TestContext TestContext  
public UIMap UIMap  
```
  
#####  <a name="CodedUITestMethods"></a> Metodi di CodedUITest1  
 Per impostazione predefinita, la classe contiene solo un metodo.  

```csharp
public void CodedUITestMethod1()  
```

 Questo metodo chiama ogni metodo `UIMap` specificato quando è stato registrato il test, descritto nella sezione [Classe UIMap](#UIMapClass).  
  
 Un'area denominata `Additional test attributes`, se non commentata, contiene due metodi facoltativi.  
  
```csharp
// Use TestInitialize to run code before running each test   
[TestInitialize()]  
public void MyTestInitialize()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.LaunchCalculator();  
}  
  
// Use TestCleanup to run code after each test has run  
[TestCleanup()]  
public void MyTestCleanup()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.CloseCalculator();  
}
```

 Al metodo `MyTestInitialize()` è applicato <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>, che indica al framework di test di chiamare questo metodo prima di qualsiasi altro metodo di test. Analogamente, al metodo `MyTestCleanup()` è applicato <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>, che indica al framework di test di chiamare questo metodo dopo che sono stati chiamati tutti gli altri metodi di test. L'uso di questi metodi è facoltativo. Per questo test, il metodo `UIMap.LaunchCalculator()` potrebbe essere chiamato da `MyTestInitialize()` e il metodo `UIMap.CloseCalculator()` potrebbe essere chiamato da `MyTestCleanup()` invece che da `CodedUITest1Method1()`.  
  
 Se si aggiungono altri metodi a questa classe usando <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>, il framework di test chiamerà ogni metodo durante il test.  
  
###  <a name="UIMapuitest"></a> UIMap.uitest  
 Esiste un file XML che rappresenta la struttura della registrazione del test codificato dell'interfaccia utente e di tutte le sue parti, che includono le azioni e le classi oltre ai metodi e alle proprietà di tali classi. Il file [UIMap.Designer.cs](#UIMapDesignerFile) contiene il codice generato dal Generatore di test codificati dell'interfaccia utente per riprodurre la struttura del test e fornisce la connessione al framework di test.  
  
 Il file `UIMap.uitest` non è modificabile direttamente. È però possibile usare il Generatore di test codificati dell'interfaccia utente per modificare il test, che modifica automaticamente il file `UIMap.uitest` e il file [UIMap.Designer.cs](#UIMapDesignerFile).  
  
## <a name="see-also"></a>Vedere anche

<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>   
<xref:System.CodeDom.Compiler.GeneratedCodeAttribute>   
<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>   
<xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>   
<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>   
<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>   
[Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)   
[Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md)   
[Procedure consigliate per i test codificati dell'interfaccia utente](../test/best-practices-for-coded-ui-tests.md)   
[Test di un'applicazione di grandi dimensioni con più mappe dell'interfaccia utente](../test/testing-a-large-application-with-multiple-ui-maps.md)   
[Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
