---
title: Guida introduttiva a servizio di linguaggio e le estensioni di Editor | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5f7b7440ff2f42eba1d138872071d4e51d2402c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Guida introduttiva a servizio di linguaggio e le estensioni di Editor
Per aggiungere funzionalità del linguaggio, ad esempio la struttura, corrispondenza parentesi graffe, IntelliSense e le lampadine proprio linguaggio di programmazione o a qualsiasi tipo di contenuto, è possibile utilizzare le estensioni di editor. È anche possibile personalizzare l'aspetto e il comportamento dell'editor di Visual Studio, ad esempio testo colorazione, margini, aree di controllo e altri elementi visivi. È inoltre possibile definire il tipo di contenuto e specificare l'aspetto e il comportamento delle visualizzazioni di testo in cui viene visualizzato il contenuto.  
  
 Per iniziare a scrivere le estensioni di editor, usare i modelli di progetto editor che vengono installati come parte di Visual Studio SDK. Visual Studio SDK è un set scaricabile di strumenti che semplificano lo sviluppo di estensioni di Visual Studio mediante pacchetti VSPackage o mediante Managed Extensibility Framework (MEF).  
  
> [!NOTE]
>  Per ulteriori informazioni su Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 È consigliabile conoscere i seguenti concetti e le tecnologie prima di scrivere estensioni di editor.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) e le estensioni di Editor  
 L'interfaccia utente dell'editor di Visual Studio (UI) viene implementato utilizzando Windows Presentation Foundation (WPF). WPF offre un'esperienza visiva dettagliata e un modello di programmazione coerente che separa gli aspetti visivi del codice dalla logica di business. È possibile utilizzare numerosi elementi WPF e sulle funzionalità quando si creano estensioni di editor. Per ulteriori informazioni, vedere [Windows Presentation Foundation](/dotnet/framework/wpf/index).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) e le estensioni di Editor  
 Editor di Visual Studio Usa Managed Extensibility Framework (MEF) per gestire i componenti e le estensioni. La MEF consente inoltre agli sviluppatori più facilmente creare estensioni per un'applicazione host come Visual Studio. In questo contesto, definire un'estensione in base a un contratto MEF ed esportarlo come componente MEF. L'applicazione host gestisce le parti componenti, ricerca, li registra e assicurarsi che vengano applicate nel contesto corretto.  
  
> [!NOTE]
>  Per ulteriori informazioni su MEF nell'editor, vedere [Managed Extensibility Framework nell'Editor](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Punti di estensione di Editor di Visual Studio e le estensioni  
 Punti di estensione di editor sono parti componente MEF che è possibile personalizzare ed estendere. In alcuni casi si estende il punto di estensione implementando un'interfaccia e l'esportazione con i metadati corretti. In altri casi sufficiente dichiarare un'estensione ed esportarlo come un tipo specifico.  
  
 Di seguito sono indicati alcuni dei tipi di base di estensioni di editor:  
  
-   Margini e le barre di scorrimento  
  
-   Tag  
  
-   Aree di controllo  
  
-   Opzioni  
  
-   IntelliSense  
  
 Per ulteriori informazioni sui punti di estensione di editor, vedere [servizio di linguaggio e i punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Distribuzione di estensioni di Editor  
 In Visual Studio, distribuire le estensioni di editor aggiungendo un file di metadati denominato vsixmanifest alla soluzione, compilare la soluzione, e quindi aggiunta una copia dei file binari e il manifesto in una cartella in cui è noto a Visual Studio. Il file manifesto definisce i fatti di base sull'estensione (ad esempio nome, autore, versione e tipo di contenuto). Per ulteriori informazioni sul file manifesto VSIX e come distribuire le estensioni, vedere [Shipping estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Quando si installa un'estensione in un computer, includere i file binari e il manifesto in una sottocartella della cartella in cui è noto a Visual Studio.  
  
> [!WARNING]
>  Non è necessario occuparsi di manifesti e percorsi di distribuzione se si utilizza uno dei modelli di editor di estendibilità che vengono inclusi in Visual Studio. I modelli contengono tutto il necessario per registrare e distribuire un'estensione.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Esecuzione delle estensioni nell'istanza sperimentale  
 È possibile isolare la versione di lavoro di Visual Studio mentre si sviluppa un'estensione distribuendola nella cartella seguente sperimentale (in Windows Vista e Windows 7):  
  
 *% LOCALAPPDATA %*\VisualStudio\10.0Exp\Extensions\\*aziendale*\\*ExtensionID*  
  
 dove *% LOCALAPPDATA %* è il nome dell'utente connesso, *aziendale* è il nome della società che possiede l'estensione, e *ExtensionID* è l'ID dell'estensione.  
  
 Quando si distribuisce un'estensione per il percorso sperimentale, viene eseguito in modalità di debug. Viene avviata una seconda istanza di Visual Studio ed è denominata **Microsoft Visual Studio - istanza sperimentale**.  
  
## <a name="managing-extensions"></a>Gestione delle estensioni  
 Estensioni di Visual Studio sono elencate nel **estensioni e aggiornamenti** (sul **strumenti** menu). Se si sta testando un'estensione nell'istanza sperimentale, è elencato nel **estensioni e aggiornamenti** nell'istanza sperimentale, ma non è elencato nell'istanza di sviluppo.  
  
 Per altre informazioni, vedere [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Utilizzo di modelli per creare estensioni dell'Editor  
 È possibile utilizzare modelli di editor per creare estensioni MEF che consentono di personalizzare i classificatori, aree di controllo e i margini. Sono disponibili modelli per progetti c# e Visual Basic. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 È inoltre possibile utilizzare il modello di progetto VSIX per creare estensioni. Questo modello offre solo gli elementi necessari per distribuire qualsiasi tipo di estensione e includere il file vsixmanifest, i riferimenti ad assembly richiesti e un file di progetto che include le attività di compilazione che consentono di distribuire la estensione. Per ulteriori informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
 È anche possibile creare editor di componenti MEF da un'estensione per il pacchetto di Visual Studio. Le procedure dettagliate seguenti per informazioni dettagliate, vedere:  
  
-   [Procedura dettagliata: Uso di un comando della shell con un'estensione dell'editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Procedura dettagliata: Uso di una combinazione di tasti con un'estensione dell'editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)