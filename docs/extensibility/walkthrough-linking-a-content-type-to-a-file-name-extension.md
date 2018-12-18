---
title: "Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di File | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cca12f7c04b51bcf2b695e00d9305a7feb72ebc4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di File
È possibile definire il tipo di contenuto e collegare un'estensione di file utilizzando le estensioni di editor Managed Extensibility Framework (MEF). In alcuni casi, l'estensione del nome file è già stato definito da un servizio di linguaggio. Tuttavia, per utilizzarlo con MEF è ancora necessario collegarlo a un tipo di contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo Seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `ContentTypeTest`.  
  
2.  Nel **vsixmanifest** file, passare al **asset** scheda e impostare il **tipo** campo **MEFComponent**, **origine** campo **un progetto nella soluzione corrente**e **progetto** campo il nome del progetto.  
  
## <a name="defining-the-content-type"></a>Definizione del tipo di contenuto  
  
1.  Aggiungere un file di classe e assegnargli il nome `FileAndContentTypes`.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Aggiungere il seguente `using` direttive.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Dichiarare una classe statica che contiene le definizioni.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  Questa classe, è possibile esportare un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> denominato "nascosta" e si dichiara la definizione di base per essere "text".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Collegamento di un'estensione di File a un tipo di contenuto  
  
-   Per eseguire il mapping di questo tipo di contenuto per un'estensione di file, è possibile esportare un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> che ha l'estensione "HID" e il tipo di contenuto "nascosta".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Aggiungere il tipo di contenuto per un'esportazione di Editor  
  
1.  Creare un'estensione di editor. Ad esempio, è possibile utilizzare l'estensione del glifo margine descritto in [procedura dettagliata: creazione di un'icona di margine](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Aggiungere la classe definita in questa procedura.  
  
3.  Quando si esporta la classe di estensione, aggiungere un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di tipo "nascosta" a esso.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)