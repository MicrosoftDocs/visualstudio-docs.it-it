---
title: Creazione di un'estensione con un modello di elemento Editor | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 60f10479e0ce6fa08e888d92556ff47b5d82af66
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Creazione di un'estensione con un modello di elemento di Editor
È possibile utilizzare i modelli di elementi inclusi nel SDK di Visual Studio per creare estensioni dell'editor di base che aggiungono classificatori, aree di controllo e i margini nell'editor. I modelli di elemento editor sono disponibili per i progetti Visual c# o Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Creazione di un'estensione di classificazione  
 Il modello di elemento di classificatore Editor Crea un classificatore editor che colora il testo appropriato (in questo caso, tutti gli elementi) in qualsiasi file di testo.  
  
1.  Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** o **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** riquadro, selezionare **progetto VSIX**. Nella casella **Nome** digitare `TestClassifier`. Fare clic su **OK**.  
  
2.  Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Passare a Visual c# **estendibilità** nodo e selezionare **classificatore Editor**. Lasciare il nome di file predefinito (EditorClassifier1.cs).  
  
3.  Esistono tre file di codice, come indicato di seguito:  
  
    -   EditorClassifier1.cs contiene la `EditorClassifier1` classe.  
  
    -   EditorClassifier1ClassificationDefinition.cs contiene la `OEditorClassifier1ClassificationDefinition` classe.  
  
    -   EditorClassifier1Format.cs contiene la `EditorClassifier1Format` classe.  
  
    -   EditorClassifier1Provider.cs contiene la `EditorClassifier1Provider` classe.  
  
4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.  
  
     Se si apre un file di testo, tutto il testo è sottolineato su uno sfondo violetto.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Creazione di un'estensione di testo relativa dell'area di controllo  
 Il modello di area di controllo Text Editor crea un'area di controllo relativo al testo che decora tutte le istanze del carattere di testo 'a' utilizzando una casella con un contorno rosso e uno sfondo blu. È relativo al testo perché la casella sempre sovrapposizioni 'a' caratteri, anche quando vengono spostati o riformattati.  
  
1.  Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** o **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** riquadro, selezionare **progetto VSIX**. Nella casella **Nome** digitare `TestAdornment`. Fare clic su **OK**.  
  
2.  Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Passare a Visual c# **estendibilità** nodo e selezionare **dell'area di controllo di Editor di testo**. Lasciare il nome di file predefinito (TextAdornment1.cs/vb).  
  
3.  Esistono due file di codice, come indicato di seguito:  
  
    -   TextAdornment1.cs contiene la `TextAdornment1` classe.  
  
    -   extAdornment1TextViewCreationListener.cs contiene la `TextAdornment1TextViewCreationListener` classe.  
  
4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, tutti i 'a' caratteri nel testo vengono evidenziati in rosso su uno sfondo blu.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Creazione di un'estensione dell'area di controllo relativo al riquadro di visualizzazione  
 Il modello di area di controllo del riquadro di visualizzazione Editor Crea un area di controllo relativo al riquadro di visualizzazione che consente di aggiungere una casella viola con un contorno rosso nell'angolo superiore destro del riquadro di visualizzazione.  
  
> [!NOTE]
>  Il *viewport* è l'area di visualizzazione di testo che è attualmente visualizzata.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Per creare un'estensione dell'area di controllo del riquadro di visualizzazione utilizzando il modello di area di controllo del riquadro di visualizzazione dell'Editor  
  
1.  Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** o **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** riquadro, selezionare **progetto VSIX**. Nella casella **Nome** digitare `ViewportAdornment`. Fare clic su **OK**.  
  
2.  Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Passare a Visual c# **estendibilità** nodo e selezionare **dell'area di controllo del riquadro di visualizzazione Editor**. Lasciare il nome di file predefinito (ViewportAdornment1.cs/vb).  
  
3.  Esistono due file di codice, come indicato di seguito:  
  
    -   ViewportAdornment1.cs contiene la `ViewportAdornment1` classe.  
  
    -   ViewportAdornment1TextViewCreationListener.cs contiene la `ViewportAdornment1TextViewCreationListener` classe  
  
4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si crea un nuovo file di testo, una casella viola con un contorno rosso viene visualizzata nell'angolo superiore destro del riquadro di visualizzazione.  
  
## <a name="creating-a-margin-extension"></a>Creazione di un'estensione di margine  
 Il modello di margine Editor Crea un margine verde che viene visualizzato con le parole "Hello world!" sotto la barra di scorrimento orizzontale.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Per creare un'estensione di margine utilizzando il modello di margine di Editor  
  
1.  Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** o **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** riquadro, selezionare **progetto VSIX**. Nella casella **Nome** digitare `MarginExtension`. Fare clic su **OK**.  
  
2.  Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Passare a Visual c# **estendibilità** nodo e selezionare **dell'area di controllo del riquadro di visualizzazione Editor**. Lasciare il nome di file predefinito (EditorMargin1.cs/vb).  
  
3.  Esistono due file di codice, come indicato di seguito:  
  
    -   EditorMargin1.cs contiene la `EditorMargin1` classe.  
  
    -   EditorMargin1Factory.cs contiene la `EditorMargin1Factory` classe.  
  
4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, un margine verde con le parole "Hello EditorMargin1" viene visualizzato sotto la barra di scorrimento orizzontale.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)