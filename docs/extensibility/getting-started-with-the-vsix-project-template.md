---
title: Introduzione al modello di progetto VSIX | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c96c0f66792f6a7a190fb5ea69ec5727ea4f2db1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-with-the-vsix-project-template"></a>Introduzione al modello di progetto VSIX
È possibile utilizzare il modello di progetto VSIX per creare un'estensione o per un'estensione esistente per la distribuzione del pacchetto. Il modello di progetto VSIX dispone di versioni di Visual Basic e Visual c# e viene installato come parte di Visual Studio SDK.  
  
 Il modello di progetto VSIX appena è costituito da un file vsixmanifest, che contiene informazioni sull'estensione e le risorse che è disponibile.  
  
 Per trovare il modello di progetto VSIX, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Distribuzione di un modello di progetto personalizzato utilizzando il modello di progetto VSIX  
 La procedura seguente viene illustrato come utilizzare il progetto VSIX per creare un modello di progetto che è possibile condividere con altri sviluppatori o caricare in Visual Studio Gallery il pacchetto.  
  
1.  Creare un modello di progetto.  
  
    1.  Aprire il progetto da cui creare un modello. Questo progetto può essere di qualsiasi tipo di progetto.  
  
    2.  Nel menu **Progetto** scegliere**Esporta modello**. Completare i passaggi della procedura guidata.  
  
         Viene creato un file con estensione zip in %USERPROFILE%\My Documents\Visual Studio  *\<versione >*\My Exported Templates\\.  
  
2.  Creare un progetto VSIX vuoto.  
  
     Scegliere **Nuovo** dal menu **File** , quindi fare clic su **Progetto**. Selezionare l'opzione **Visual Basic** o **Visual c#**. Selezionare il nodo selezionato, **estendibilità**, quindi selezionare **progetto VSIX**.  
  
3.  Aggiungere il file ZIP per il progetto. Impostare il relativo **copia nella Directory di Output di** proprietà `Copy Always`.  
  
4.  Nel **Esplora**, fare doppio clic su di `source.extension.vsixmanifest` file per aprirlo nel **progettazione del manifesto VSIX**e quindi apportare le modifiche seguenti:  
  
    -   Impostare il **Product Name** campo **risorse del modello di progetto**.  
  
    -   Impostare il **ID prodotto** campo **MyProjectTemplate - 1**.  
  
    -   Impostare il **autore** campo **Fabrikam**.  
  
    -   Impostare il **descrizione** campo **il modello di progetto**.  
  
    -   Nel **asset** sezione, aggiungere un **Microsoft.VisualStudio.ProjectTemplate** digitare e impostarne il percorso per il nome del file ZIP.  
  
5.  Salvare e chiudere il file vsixmanifest.  
  
6.  Compilare il progetto.  
  
7.  Nella directory di output, fare doppio clic sul file con estensione VSIX.  
  
8.  Oggetto **VSIX Installer** finestra di messaggio viene visualizzato. Seguire le istruzioni per installare l'estensione.  
  
9. Chiudere Visual Studio e quindi aprirlo nuovamente.  
  
10. Selezionare **estensioni e aggiornamenti** (sul **strumenti** menu) e selezionare il **modelli** categoria. Una delle estensioni disponibili deve essere **risorse del modello di progetto**.  
  
11. Il nuovo modello di progetto è presente il **nuovo progetto** finestra di dialogo nella stessa posizione come il modello di progetto originale. Ad esempio, se è stato creato un modello denominato **Console VB** da un'applicazione console Visual Basic, **Console VB** viene visualizzata nel riquadro stesso come Visual Basic **applicazione Console**modello.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Per specificare il percorso del modello nella finestra di dialogo Nuovo progetto  
  
1.  Le cartelle dei modelli si trovano nel *percorso di installazione di Visual Studio*\Common7\IDE\ProjectTemplates e *percorso di installazione di Visual Studio*\Common7\IDE\ItemTemplates directory. I nomi delle sezioni di primo livello nella finestra di dialogo Nuovo progetto corrisponde esattamente i nomi delle cartelle dei modelli. Dove sono diversi, utilizzare il nome della cartella del modello.  
  
     Modificare l'estensione di file VSIX in. zip e quindi aprire il file.  
  
2.  Creare una nuova cartella con lo stesso nome della sezione della finestra di dialogo Nuovo progetto che in cui deve essere visualizzato il modello.  
  
3.  Se il modello deve trovarsi in una sottosezione, creare una sottocartella con lo stesso nome.  
  
4.  Spostare il file zip del modello nella nuova cartella.  
  
5.  Modificare l'estensione. zip in VSIX.  
  
6.  Aprire il manifesto VSIX.  
  
7.  Nel manifesto VSIX, aggiornare il **Asset** percorso del modello in modo che punti alla radice della struttura di directory che contiene il file di modello. Ad esempio, se il modello è \CSharp\Windows, \CSharp deve puntare il riferimento.