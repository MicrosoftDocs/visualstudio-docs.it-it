---
title: Proprietà personalizzate del documento nei servizi di linguaggio legacy
description: Informazioni su come creare proprietà del documento personalizzate visualizzate in Visual Studio Finestra Proprietà, come parte di un servizio di linguaggio legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e154ba5e6ce4c85f597957b1d6704ca341b3c4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091149"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Proprietà personalizzate del documento in un servizio di linguaggio legacy
Le proprietà del documento possono essere visualizzate nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestra **Proprietà** . I linguaggi di programmazione non dispongono in genere di proprietà associate a singoli file di origine. Tuttavia, XML supporta le proprietà del documento che interessano la codifica, lo schema e il foglio di stile.

## <a name="discussion"></a>Discussione
 Se il linguaggio in uso richiede proprietà personalizzate del documento, è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe e implementare le proprietà necessarie nella classe derivata.

 Inoltre, le proprietà del documento vengono in genere archiviate nel file di origine. Questa operazione richiede che il servizio di linguaggio analizzi le informazioni sulle proprietà dal file di origine per la visualizzazione nella finestra **Proprietà** e per aggiornare il file di origine quando viene apportata una modifica alle proprietà del documento nella finestra **Proprietà** .

## <a name="customize-the-documentproperties-class"></a>Personalizzare la classe DocumentProperties
 Per supportare le proprietà personalizzate dei documenti, è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe e aggiungere tutte le proprietà necessarie. È inoltre necessario specificare gli attributi utente per organizzarli nella finestra **Proprietà** . Se una proprietà dispone solo di una `get` funzione di accesso, viene visualizzata come di sola lettura nella finestra **Proprietà** . Se una proprietà ha entrambe `get` `set` le funzioni di accesso e, la proprietà può essere aggiornata anche nella finestra **proprietà** .

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio di classe derivato da <xref:Microsoft.VisualStudio.Package.DocumentProperties> , che mostra due proprietà, `Filename` e `Description` . Quando una proprietà viene aggiornata, viene chiamato un metodo personalizzato sulla <xref:Microsoft.VisualStudio.Package.LanguageService> classe per scrivere la proprietà nel file di origine.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestDocumentProperties : DocumentProperties
    {
        private string m_filename;
        private string m_description;

        public TestDocumentProperties(CodeWindowManager mgr)
            : base(mgr)
        {
        }

        // Helper function to initialize this property without
        // going through the FileName property (which does a lot
        // more than we need when the filename is set).
        public void SetFileName(string filename)
        {
            m_filename = filename;
        }

        // Helper function to initialize this property without
        // going through the Description property (which does a lot
        // more than we need when the description is set).
        public void SetDescription(string description)
        {
            m_description = description;
        }

        ////////////////////////////////////////////////////////////
        // The document properties

        [CategoryAttribute("General")]
        [DescriptionAttribute("Name of the file")]
        [DisplayNameAttribute("Filename")]
        public string FileName
        {
            get { return m_filename; }
            set
            {
               if (value != m_filename)
               {
                    m_filename = value;
                    SetPropertyValue("Filename", m_filename);
               }
            }
        }

        [CategoryAttribute("General")]
        [DescriptionAttribute("Description of the file")]
        [DisplayNameAttribute("Description")]
        public string Description
        {
            get { return m_description; }
            set
            {
                if (value != m_description)
                {
                    m_description = value;
                    SetPropertyValue("Description", m_description);
                }
            }
        }

        ///////////////////////////////////////////////////////////
        // Private methods.

        private void SetPropertyValue(string propertyName, string propertyValue)
        {
            Source src = this.GetSource();
            if (src != null)
            {
                TestLanguageService service = src.LanguageService as TestLanguageService;
                if (service != null)
                {
                    // Set the property in to the source file.
                    service.SetPropertyValue(src, propertyName, propertyValue);
                }
            }
        }
    }
}
```

## <a name="instantiate-the-custom-documentproperties-class"></a>Creare un'istanza della classe DocumentProperties personalizzata
 Per creare un'istanza della classe proprietà del documento personalizzato, è necessario eseguire l'override del <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> metodo nella versione della <xref:Microsoft.VisualStudio.Package.LanguageService> classe per restituire una singola istanza della <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe.

### <a name="example"></a>Esempio

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        private TestDocumentProperties m_documentProperties;

        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)
        {
            if (m_documentProperties == null)
            {
                m_documentProperties = new TestDocumentProperties(mgr);
            }
            return m_documentProperties;
        }
    }
}
```

## <a name="properties-in-the-source-file"></a>Proprietà nel file di origine
 Poiché le proprietà del documento sono in genere specifiche del file di origine, i valori vengono archiviati nel file di origine. È necessario il supporto del parser del linguaggio o dello scanner per definire queste proprietà. Le proprietà di un documento XML, ad esempio, vengono archiviate nel nodo radice. I valori sul nodo radice vengono modificati quando vengono modificati i valori della finestra **Proprietà** e il nodo radice viene aggiornato nell'editor.

### <a name="example"></a>Esempio
 Questo esempio archivia le proprietà `Filename` e `Description` nelle prime due righe del file di origine, incorporate in un'intestazione di commento speciale, come segue:

```
//!Filename = file.testext
//!Description = A sample file
```

 In questo esempio vengono illustrati i due metodi necessari per ottenere e impostare le proprietà del documento dalle prime due righe del file di origine, nonché la modalità di aggiornamento delle proprietà se l'utente modifica direttamente il file di origine. Il `SetPropertyValue` metodo nell'esempio illustrato di seguito è lo stesso chiamato dalla `TestDocumentProperties` classe, come illustrato nella sezione *personalizzazione della classe DocumentProperties* .

 Questo esempio usa lo scanner per determinare il tipo di token nelle prime due righe. Questo esempio è solo a scopo illustrativo. Un approccio più comune a questa situazione consiste nell'analizzare il file di origine in una struttura ad albero di analisi in cui ogni nodo dell'albero contiene informazioni su un determinato token. Il nodo radice conterrà le proprietà del documento.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    // TokenType.Comment is the last item in that enumeration.
    public enum TestTokenTypes
    {
        DocPropertyLine = TokenType.Comment + 1,
        DocPropertyName,
        DocPropertyAssign,
        DocPropertyValue
    }

    class TestLanguageService : LanguageService
    {
        // Search this many lines from the beginning for properties.
        private static int maxLinesToSearch = 2;

        private TestDocumentProperties m_documentProperties;

        // Called whenever a full parsing operation has completed.
        public override void OnParseComplete(ParseRequest req)
        {
            if (m_documentProperties != null)
            {
                Source src = GetSource(req.View);
                if (src != null)
                {
                    string value = GetPropertyValue(src, "Filename");
                    m_documentProperties.SetFileName(value);

                    value = GetPropertyValue(src, "Description");
                    m_documentProperties.SetDescription(value);

                    // Update the Properties Window.
                    m_documentProperties.Refresh();
                }
            }
        }

        // Retrieves the specified property value from the given source.
        public string GetPropertyValue(Source src, string propertyName)
        {
            string propertyValue = "";

            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    string      line;
                    TokenInfo[] lineInfo = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line.
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                for ( ;
                                     tokenIndex < lineInfo.Length;
                                     tokenIndex++)
                                {
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)
                                    {
                                        break;
                                    }
                                }
                                if (tokenIndex < lineInfo.Length)
                                {
                                    propertyValue = src.GetText(i,
                                                          lineInfo[tokenIndex].StartIndex,
                                                          i,
                                                          lineInfo[tokenIndex].EndIndex + 1);
                                }
                                break;
                            }
                        }
                    }
                }
            }
            return propertyValue;
        }

        // Sets the specified property into the given source file.
        // Called from the TestDocumentProperties class.
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)
        {
            string newLine;

            if (propertyName == null || propertyName == "")
            {
                // No property name, so nothing to do
                return;
            }
            if (propertyValue == null)
            {
                propertyValue = "";
            }
            // This is the line to be inserted.
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);

            // First, find the line on which the property belongs.
            // If line is found, replace it.
            // Otherwise, insert the line at the beginning of the file.
            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    int         lineNumber = -1;
                    string      line;
                    TokenInfo[] lineInfo   = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                lineNumber = i;
                                break;
                            }
                        }
                    }

                    // Set up an undo context that also handles the insert/replace.
                    EditArray editArray = new EditArray(src,
                                                        true,
                                                        "Update Property");
                    if (editArray != null)
                    {
                        TextSpan span = new TextSpan();
                        if (lineNumber != -1)
                        {
                            // Replace line.
                            int lineLength = 0;
                            src.GetTextLines().GetLengthOfLine(lineNumber,
                                                               out lineLength);
                            span.iStartLine  = lineNumber;
                            span.iStartIndex = 0;
                            span.iEndLine    = lineNumber;
                            span.iEndIndex   = lineLength;
                        }
                        else
                        {
                            // Insert new line.
                            span.iStartLine  = 0;
                            span.iStartIndex = 0;
                            span.iEndLine    = 0;
                            span.iEndIndex   = 0;
                            newLine += "\n";
                        }
                        editArray.Add(new EditSpan(span, newLine));
                        editArray.ApplyEdits();
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vedi anche
- [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
