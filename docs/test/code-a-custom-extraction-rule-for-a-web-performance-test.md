---
title: Codifica di una regola di estrazione personalizzata per un test delle prestazioni Web in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 748b1f726a74fd0af1545a5bdb9c620b1ffb2a4d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="coding-a-custom-extraction-rule-for-a-web-performance-test"></a>Codifica di una regola di estrazione personalizzata per un test delle prestazioni Web

È possibile creare proprie regole di estrazione. A tale scopo, derivare le proprie regole da una classe di regole di estrazione. Le regole di estrazione derivano dalla classe di base <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>.

> [!NOTE]
> È possibile anche creare regole di convalida personalizzate. Per altre informazioni, vedere [Creare codice personalizzato e plug-in per i test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md).

## <a name="to-create-a-custom-extraction-rule"></a>Per creare una regola di estrazione personalizzata

1.  Aprire un progetto di test contenente un test Web.

2.  (Facoltativo) Creare un progetto Libreria di classi distinto in cui archiviare la regola di estrazione.

    > [!IMPORTANT]
    > È possibile creare la classe nello stesso progetto in cui si trovano i test. Tuttavia, se si desidera riutilizzare la regola, è preferibile creare un progetto Libreria di classi distinto in cui archiviarla. Se si crea un progetto distinto, è necessario completare i passaggi facoltativi di questa procedura.

3.  (Facoltativo) Nel progetto Libreria di classi aggiungere un riferimento alla dll Microsoft.VisualStudio.QualityTools.WebTestFramework.

4.  Creare una classe che derivi dalla classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>. Implementare i membri <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> e <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*>.

5.  (Facoltativo) Compilare il nuovo progetto Libreria di classi.

6.  (Facoltativo) Nel progetto di test aggiungere un riferimento al progetto Libreria di classi che contiene la regola di estrazione personalizzata.

7.  Nel progetto di test aprire un test delle prestazioni Web nell'**Editor test prestazioni Web**.

8.  Per aggiungere la regola di estrazione personalizzata, fare clic con il pulsante destro del mouse su una richiesta di test delle prestazioni Web e scegliere **Aggiungi regola di estrazione**.

     Verrà visualizzata la finestra di dialogo **Aggiungi regola di estrazione**. La regola di convalida personalizzata sarà disponibile nell'elenco **Selezionare una regola**, insieme alle regole di convalida predefinite. Selezionare la regola di estrazione personalizzata e scegliere **OK**.

9. Eseguire il test Web.

## <a name="example"></a>Esempio

Nell'esempio di codice seguente viene illustrata un'implementazione di una regola di estrazione personalizzata, che estrae il valore da un campo di input specificato. Utilizzare questo esempio come punto di partenza per le regole di estrazione personalizzate.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

Il metodo <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> contiene le funzionalità principali di una regola di estrazione. Il metodo <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> nell'esempio precedente assume il valore <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs> che fornisce la risposta generata dalla richiesta coperta da questa regola di estrazione. La risposta contiene <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> che contiene tutti i tag nella risposta. I tag di input vengono filtrati da <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>. In ogni tag di input viene cercato un attributo denominato `name` il cui valore è uguale all'utente che ha specificato il valore della proprietà `Name`. Se viene rilevato un tag con questo attributo corrispondente, viene eseguito un tentativo di estrarre un valore contenuto nell'attributo `value`, se esiste. Se presenti, il nome e il valore del tag vengono estratti e aggiunti al contesto del test Web. La regola di estrazione viene passata.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Codifica di una regola di convalida personalizzata per un test delle prestazioni Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)