---
title: Abilitare test codificati dell'interfaccia utente per i controlli in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7c3906b84995716072d4df0a1b518930a521cdb6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Abilitare test codificati dell'interfaccia utente per i controlli

È utile implementare il supporto del framework dei test codificati dell'interfaccia utente per facilitare i test dei controlli. È possibile aggiungere gradualmente livelli crescenti di supporto. Iniziare supportando la registrazione, la riproduzione e la convalida delle proprietà. Partendo da queste basi, abilitare il generatore di test codificato dell'interfaccia utente per riconoscere le proprietà personalizzate dei controlli. Specificare classi personalizzate per accedere a tali proprietà dal codice generato. È anche possibile consentire al generatore di test codificati dell'interfaccia utente di acquisire le azioni nella modalità che più si avvicina di più allo scopo dell'azione registrata.

![CUIT&#95;Full](../test/media/cuit_full.png "CUIT_Full")

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Supportare registrazione, riproduzione e convalida delle proprietà implementando l'accessibilità

Il generatore di test codificati dell'interfaccia utente acquisisce informazioni sui controlli intercettati durante la registrazione e quindi genera il codice per riprodurre quella sessione. Se il controllo non supporta l'accessibilità, il generatore di test codificati dell'interfaccia utente acquisisce le azioni, come ad esempio i clic del mouse, usando le coordinate dello schermo. Quando il test viene riprodotto, il codice generato emette le azioni nelle stesse coordinate dello schermo. Se, quando il test viene riprodotto, il controllo viene visualizzato in un punto diverso dello schermo, l'azione da parte del codice generato non riuscirà. Se non si implementa l'accessibilità per il controllo, è possibile che i test abbiano esito negativo se vengono riprodotti in configurazioni di schermo diverse, in ambienti diversi o quando il layout dell'interfaccia utente viene modificato.

 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png "CUIT_RecordNoSupport")

 Se si implementa l'accessibilità, il generatore di test codificati dell'interfaccia utente la userà per acquisire informazioni sul controllo quando registra un test. Quindi, quando si esegue il test, il codice generato riprodurrà tali eventi sul controllo, anche se questo si trova altrove nell'interfaccia utente. Gli autori del test possono creare le asserzioni anche usando le proprietà di base del controllo.

 ![CUIT&#95;Record](../test/media/cuit_record.png "CUIT_Record")

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Per supportare registrazione e riproduzione, convalida delle proprietà e navigazione per un controllo Windows Form
 Implementare l'accessibilità per il controllo come descritto nella procedura seguente e descritto in dettaglio in <xref:System.Windows.Forms.AccessibleObject>.

 ![CUIT&#95;Accessible](../test/media/cuit_accessible.png "CUIT_Accessible")

1.  Implementare una classe che derivi da <xref:System.Windows.Forms.Control.ControlAccessibleObject> ed eseguire l'override della proprietà <xref:System.Windows.Forms.Control.AccessibilityObject%2A> per restituire un oggetto della classe.

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2.  Eseguire l'override dei metodi e delle proprietà <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> e <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> dell'oggetto accessibile.

3.  Implementare un altro oggetto accessibilità per il controllo figlio ed eseguire l'override della proprietà <xref:System.Windows.Forms.Control.AccessibilityObject%2A> del controllo figlio per restituire tale oggetto accessibilità.

4.  Eseguire l'override delle proprietà e dei metodi <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> e <xref:System.Windows.Forms.AccessibleObject.Select%2A> per l'oggetto accessibilità del controllo figlio.

> [!NOTE]
> Questo argomento inizia con l'esempio di accessibilità in <xref:System.Windows.Forms.AccessibleObject> e si basa quindi su tale esempio nelle procedure restanti. Se si vuole creare una versione funzionante dell'esempio di accessibilità, creare un'applicazione console e quindi sostituire il codice in Program.cs con il codice di esempio. Aggiungere riferimenti a oggetti Accessibility, System.Drawing e System.Windows.Forms. Modificare **Incorpora tipi di interoperabilità** per l'accessibilità impostandolo su **False** per eliminare l'avviso di compilazione. È possibile modificare il tipo di output del progetto da **Applicazione console** ad **Applicazione Windows** in modo che non venga visualizzata alcuna finestra della console quando si esegue l'applicazione.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Supportare la convalida delle proprietà personalizzate implementando un provider di proprietà

Dopo aver implementato il supporto di base per la registrazione, la riproduzione e la convalida delle proprietà, è possibile rendere disponibili le proprietà personalizzate del controllo ai test codificati dell'interfaccia utente mediante l'implementazione di un plug-in <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>. La procedura seguente, ad esempio, crea un provider di proprietà che consente ai test codificati dell'interfaccia utente di accedere alla proprietà di stato dei controlli figlio del controllo CurveLegend del grafico:

 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png "CUIT_CustomProps")

### <a name="to-support-custom-property-validation"></a>Per supportare la convalida delle proprietà personalizzate

![CUIT&#95;Props](../test/media/cuit_props.png "CUIT_Props")

1. Eseguire l'override della proprietà <xref:System.Windows.Forms.AccessibleObject.Description%2A> dell'oggetto accessibile CurveLegend per passare valori di proprietà avanzate nella stringa di descrizione. Se si specificano più valori, separarli con il punto e virgola (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add ";" and the state value to the end
                // of the curve legend's description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

1. Generare un pacchetto di estensione di test dell'interfaccia utente per il controllo creando un progetto di libreria di classi. Aggiungere riferimenti ad Accessibility, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common e Microsoft.VisualStudio.TestTools.Extension. Modificare il valore per **Incorpora tipi di interoperabilità** per l'accessibilità impostandolo su **False**.

1. Aggiungere una classe di provider di proprietà che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>:

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

1. Implementare il provider di proprietà inserendo i nomi di proprietà e i descrittori di proprietà in un oggetto <xref:System.Collections.Generic.Dictionary%602>.

1. Eseguire l'override di <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> per indicare che l'assembly fornisce supporto specifico del controllo per il controllo e per i relativi elementi figlio.

1. Eseguire l'override dei rimanenti metodi astratti di <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>

1. Aggiungere una classe del pacchetto di estensione che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Definire l'attributo `UITestExtensionPackage` per l'assembly.

1. Nella classe del pacchetto di estensione, eseguire l'override di <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> per restituire la classe del provider di proprietà, quando ne è richiesto uno.

1. Eseguire l'override delle proprietà e dei metodi astratti rimanenti dell'oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Compilare i file binari e copiarli in **%Programmi%\File comuni\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.

> [!NOTE]
> Questo pacchetto di estensione viene applicato a qualsiasi controllo di tipo "Text". Se si stanno testando più controlli dello stesso tipo, è necessario testarli separatamente in modo da poter definire quali pacchetti di estensione vengono distribuiti quando si registrano i test.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Supportare la generazione di codice implementando una classe per accedere alle proprietà personalizzate

Quando il generatore di test codificati dell'interfaccia utente genera il codice da una registrazione della sessione, usa la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> per accedere ai controlli dell'utente.

Se è stato implementato un provider di proprietà per offrire accesso alle proprietà personalizzate del controllo, è possibile aggiungere una classe specializzata per accedere a tali proprietà. L'aggiunta di una classe specializzata semplifica il codice generato.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Per aggiungere una classe specializzata per accedere al proprio controllo

![CUIT&#95;CodeGen](../test/media/cuit_codegen.png "CUIT_CodeGen")

1. Implementare una classe che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> e aggiungere il tipo del controllo alla raccolta di proprietà di ricerca nel costruttore.

1. Implementare le proprietà personalizzate del controllo come proprietà della classe.

1. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> del provider di proprietà per restituire il tipo della nuova classe per i controlli figlio dell'oggetto CurveLegend.

1. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> del provider di proprietà per restituire il tipo del metodo PropertyNames della nuova classe.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Supportare le azioni sensibili allo scopo implementando un filtro azioni

 Quando Visual Studio registra un test, acquisisce ogni evento di mouse e tastiera. Tuttavia, in alcuni casi, lo scopo dell'azione può perdersi nella serie di eventi di mouse e tastiera. Ad esempio, se il controllo supporta il completamento automatico, lo stesso set di eventi di mouse e tastiera può comportare un valore diverso quando il test viene riprodotto in un ambiente diverso. È possibile aggiungere un plug-in del filtro azioni che sostituisce la serie di eventi di mouse e tastiera con una sola azione. In questo modo, è possibile sostituire la sequenza di eventi di mouse e tastiera che seleziona un valore con una sola azione che imposta il valore. Questa operazione consente di proteggere i test codificati dell'interfaccia utente dalle differenze nel completamento automatico da un ambiente a un altro.

### <a name="to-support-intent-aware-actions"></a>Per supportare le azioni sensibili allo scopo

![CUIT&#95;Actions](../test/media/cuit_actions.png "CUIT_Actions")

1. Implementare una classe di filtro azioni che sia derivata da <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, eseguendo l'override delle proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> e <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.

1. Eseguire l'override di <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. In questo esempio si sostituisce un'azione di doppio clic con un'azione di clic singolo.

1. Aggiungere il filtro azioni al metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> del pacchetto di estensione.

1. Compilare i file binari e copiarli in %Programmi%\File comuni\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

> [!NOTE]
> Il filtro azioni non dipende dall'implementazione di accessibilità o dal provider di proprietà.

## <a name="debug-your-property-provider-or-action-filter"></a>Eseguire il debug del provider di proprietà o del filtro azioni

Il provider di proprietà e il filtro azioni vengono implementati in un pacchetto di estensione. Il generatore di test esegue il pacchetto di estensione in un processo separato dall'applicazione.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Per eseguire il debug del provider di proprietà o del filtro azioni

1.  Compilare la versione di debug del pacchetto di estensione copiare i file DLL e PDB in %Programmi%\File comuni\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

2.  Eseguire l'applicazione (non nel debugger).

3.  Eseguire il generatore di test codificati dell'interfaccia utente.

     `codedUITestBuilder.exe  /standalone`

4.  Associare il debugger al processo codedUITestBuilder.

5.  Impostare i punti di interruzione nel codice.

6.  Nel generatore di test codificati dell'interfaccia utente creare le asserzioni per verificare il provider di proprietà e registrare azioni per verificare i filtri azioni.

## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.AccessibleObject>
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)