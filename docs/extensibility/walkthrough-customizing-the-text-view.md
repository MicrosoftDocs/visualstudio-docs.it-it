---
title: 'Procedura dettagliata: personalizzazione della visualizzazione di testo | Microsoft Docs'
description: Per informazioni su come personalizzare una visualizzazione di testo, modificare una delle diverse proprietà nella relativa mappa in formato editor utilizzando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ef4d0b408afc00a806e73d1e2eae7a07dde7814
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216852"
---
# <a name="walkthrough-customize-the-text-view"></a>Procedura dettagliata: personalizzare la visualizzazione di testo
È possibile personalizzare una visualizzazione di testo modificando una delle proprietà seguenti nella mappa di formato dell'Editor:

- Margine indicatore

- Inserimento cursore

- Sovrascrivi punto di inserimento

- Testo selezionato

- Testo selezionato inattivo (ovvero, testo selezionato che perde lo stato attivo)

- Spazi vuoti visibili

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `ViewPropertyTest` .

2. Aggiungere un modello di elemento classificatore editor al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

## <a name="define-the-content-type"></a>Definire il tipo di contenuto

1. Aggiungere un file di classe e assegnargli il nome `ViewPropertyModifier`.

2. Aggiungere le direttive `using` seguenti:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet1":::

3. Dichiarare una classe denominata `TestViewCreationListener` che eredita da <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Esportare questa classe con gli attributi seguenti:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> per specificare il tipo di contenuto a cui si applica questo listener.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> per specificare il ruolo di questo listener.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet2":::

4. In questa classe importare il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet3":::

## <a name="change-the-view-properties"></a>Modificare le proprietà di visualizzazione

1. Configurare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che le proprietà di visualizzazione vengano modificate quando viene aperta la visualizzazione. Per apportare la modifica, trovare prima di tutto l'oggetto <xref:System.Windows.ResourceDictionary> che corrisponde all'aspetto della visualizzazione che si desidera trovare. Modificare quindi la proprietà appropriata nel dizionario risorse e impostare le proprietà. Eseguire il batch delle chiamate al <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metodo chiamando il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metodo prima di impostare le proprietà e quindi <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> dopo l'impostazione delle proprietà.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet4":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice

1. Compilare la soluzione.

     Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

2. Creare un file di testo e digitare alcune parole.

    - Il cursore di inserimento deve essere magenta e il punto di inserimento della sovrascrittura deve essere turchese.

    - Il margine dell'indicatore (a sinistra della visualizzazione di testo) dovrebbe essere verde chiaro.

3. Selezionare il testo digitato. Il colore del testo selezionato dovrebbe essere rosa chiaro.

4. Mentre il testo è selezionato, fare clic in un punto qualsiasi all'esterno della finestra di testo. Il colore del testo selezionato dovrebbe essere rosa scuro.

5. Attivare lo spazio vuoto visibile. Scegliere **Avanzate** dal menu **modifica** , quindi fare clic su **Visualizza spazi vuoti**. Digitare alcune schede nel testo. Verranno visualizzate le frecce rosse che rappresentano le schede.

## <a name="see-also"></a>Vedi anche
- [Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
