---
title: Codifica di una regola di convalida personalizzata per un test delle prestazioni Web in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- Web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 0c2e3eb6d9b0411a078c5d7531105230dfc82457
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="coding-a-custom-validation-rule-for-a-web-performance-test"></a>Codifica di una regola di convalida personalizzata per un test delle prestazioni Web

È possibile creare proprie regole di convalida. A tale scopo, è necessario derivare una classe di regola da una classe di regola di convalida. Le regole di convalida derivano dalla classe di base <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>.

> [!NOTE]
> È possibile anche creare regole di estrazione personalizzate. Per altre informazioni, vedere [Creare codice personalizzato e plug-in per i test di carico](../test/create-custom-code-and-plug-ins-for-load-tests.md).

## <a name="to-create-custom-validation-rules"></a>Per creare regole di convalida personalizzate

1.  Aprire un progetto di test contenente un test Web.

2.  (Facoltativo) Creare un progetto Libreria di classi distinto in cui archiviare la regola di convalida.

    > [!IMPORTANT]
    > È possibile creare la classe nello stesso progetto in cui si trovano i test. Tuttavia, se si desidera riutilizzare la regola, è preferibile creare un progetto Libreria di classi distinto in cui archiviarla. Se si crea un progetto distinto, è necessario completare i passaggi facoltativi di questa procedura.

3.  (Facoltativo) Nel progetto Libreria di classi aggiungere un riferimento alla DLL Microsoft.VisualStudio.QualityTools.WebTestFramework.

4.  Creare una classe che derivi dalla classe <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Implementare i membri <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*> e <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*>.

5.  (Facoltativo) Compilare il nuovo progetto Libreria di classi.

6.  (Facoltativo) Nel progetto di test aggiungere un riferimento al progetto Libreria di classi che contiene la regola di convalida personalizzata.

7.  Nel progetto di test aprire un test delle prestazioni Web nell'**Editor test prestazioni Web**.

8.  Per aggiungere una regola di convalida personalizzata a una richiesta di test delle prestazioni Web, fare clic con il pulsante destro del mouse sulla richiesta e selezionare **Aggiungi regola di convalida**.

     Verrà visualizzata la finestra di dialogo **Aggiungi regola di convalida**. La regola di convalida personalizzata sarà disponibile nell'elenco **Selezionare una regola**, insieme alle regole di convalida predefinite. Selezionare la regola di convalida personalizzata, quindi scegliere **OK**.

9. Eseguire il test Web.

## <a name="example"></a>Esempio

Nel seguente codice viene illustrata l'implementazione di una regola di convalida personalizzata. Questa regola di convalida riproduce il comportamento della regola di convalida predefinita Tag obbligatorio. Usare questo esempio come punto di partenza per le regole di convalida personalizzate.

> [!WARNING]
>  I valori delle proprietà pubbliche nel codice per un validator personalizzato non possono essere Null.

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [Codifica di una regola di estrazione personalizzata per un test delle prestazioni Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)