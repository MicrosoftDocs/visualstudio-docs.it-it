---
title: Modi per eseguire il debug del codice XSLT
description: Informazioni su come eseguire il debug di codice XSLT in Visual Studio usando il debugger XSLT per scorrere il codice, impostare i punti di interruzione e visualizzare gli Stati di esecuzione XSLT.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a7d0f5a683a627999076969dbc9077ba03d65208
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948557"
---
# <a name="debugging-xslt"></a>Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)

È possibile eseguire il debug del codice XSLT in Visual Studio. Il debugger XSLT supporta l'impostazione di punti di interruzione, la visualizzazione degli Stati di esecuzione di XSLT e così via. Il debugger XSLT può essere utilizzato per eseguire il debug di fogli di stile XSLT o di applicazioni XSLT.

È possibile eseguire il codice una riga alla volta eseguendo un'istruzione, eseguendo un'istruzione/routine o uscendo dal codice. I comandi per l'utilizzo della funzionalità di esecuzione del codice del debugger XSLT sono identici a quelli degli altri debugger di Visual Studio.

Una volta avviato il debug, nel debugger XSLT vengono aperte finestre di visualizzazione del documento di input e dell'output XSLT.

> [!NOTE]
> Il debugger XSLT è disponibile solo nelle edizioni Professional ed Enterprise di Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Eseguire il debug dall'editor XML

È possibile avviare il debugger quando si dispone di un foglio di stile o di un file XML di input aperto nell'editor. Questo consente di eseguire il debug durante la progettazione del foglio di stile.

1. Aprire il foglio di stile o il file XML in Visual Studio.

1. Selezionare **Avvia debug XSLT** dal menu **XML** oppure premere **ALT** + **F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Eseguire il debug da un'app che usa XSLT

È possibile eseguire l'istruzione XSLT durante il debug di un'applicazione. Quando si preme **F11** su una <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> chiamata, il debugger può eseguire un'istruzione nel codice XSLT.

> [!NOTE]
> Non è supportata l'esecuzione di istruzioni XSLT dalla classe <xref:System.Xml.Xsl.XslTransform>. La classe <xref:System.Xml.Xsl.XslCompiledTransform> è l'unico processore XSLT in grado di supportare l'esecuzione di istruzioni XSLT durante il debug.

### <a name="to-start-debugging-an-xslt-application"></a>Per avviare il debug di un'applicazione XSLT

1. Durante la creazione dell'istanza dell'oggetto <xref:System.Xml.Xsl.XslCompiledTransform>, impostare il parametro `enableDebug` su `true` nel codice. In questo modo viene indicato al processore XSLT di creare le informazioni di debug dopo la compilazione del codice.

1. Premere **F11** per eseguire l'istruzione nel codice XSLT.

   Il foglio di stile XSLT viene caricato in una nuova finestra del documento e viene avviato il debugger XSLT.

   In alternativa, è possibile aggiungere un punto di interruzione al foglio di stile ed eseguire l'applicazione.

### <a name="example"></a>Esempio

Di seguito è riportato un esempio di programma XSLT in C#. Viene illustrato come abilitare il debug di XSLT.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>Profiler XSLT

Il [Profiler XSLT](../xml-tools/xslt-profiler.md) è uno strumento che consente agli sviluppatori di misurare, valutare e risolvere i problemi correlati alle prestazioni nel codice XSLT creando rapporti di prestazioni XSLT dettagliati. Per altre informazioni, vedere [XSLT Profiler](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Esaminare prima di tutto il debugger di Visual Studio](../debugger/debugger-feature-tour.md)
- [Nozioni fondamentali sul debug: punti di interruzione](../debugger/using-breakpoints.md)
