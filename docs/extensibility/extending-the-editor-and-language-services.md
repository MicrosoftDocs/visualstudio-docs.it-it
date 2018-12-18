---
title: Estensione dell'Editor e i servizi di linguaggio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4e81409f8ac93c80bf16b5040c6f388b64ffabbe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-editor-and-language-services"></a>Estensione dell'Editor e i servizi di linguaggio
È possibile estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio e aggiungere funzionalità del linguaggio (ad esempio IntelliSense) per il proprio editor.  Per un elenco completo di ciò che è possibile estendere, vedere [servizio di linguaggio e i punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Estendere la maggior parte delle funzionalità dell'editor mediante Managed Extensibility Framework (MEF). Ad esempio, se si desidera estendere la funzionalità di editor la colorazione della sintassi, è possibile scrivere un MEF *componente* che definisce le classificazioni per cui si desidera diversi colori e la modalità desiderata come gestiti. L'editor supporta anche più estensioni della stessa funzionalità.  
  
 Il livello di presentazione dell'editor è basato su Windows Presentation Framework (WPF). WPF fornisce una libreria grafica per la formattazione del testo flessibile e fornisce inoltre visualizzazioni quali grafici e le animazioni.  
  
 Visual Studio SDK fornisce adapter noto come *shim* per supportare i pacchetti VSPackage che sono state scritte per le versioni precedenti. Tuttavia, se si dispone di un VSPackage esistente, è consigliabile aggiornarlo alla nuova tecnologia per ottenere l'affidabilità e prestazioni migliori.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Introduzione alle estensioni dell'editor e dei servizi di linguaggio](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Viene illustrato come creare un'estensione per l'editor.|  
|[Componenti e funzionalità dell'editor](../extensibility/inside-the-editor.md)|Descrive la struttura generale dell'editor e vengono elencate alcune delle funzionalità.|  
|[Managed Extensibility Framework nell'editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Viene illustrato come utilizzare Managed Extensibility Framework (MEF) con l'editor.|  
|[Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)|Elenca i punti di estensione dell'editor. Punti di estensione rappresentano le funzionalità dell'editor che possono essere estesa.|  
|[Procedura dettagliata: Creazione di un'area di controllo di visualizzazione, di comandi e impostazioni (guide di colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Descrive e illustra la creazione di un'area di controllo di visualizzazione che consente di disegnare linee gudie colonna che consentono di mantenere il codice per una determinata larghezza di visualizzazione.  Mostra anche durante la lettura e scrittura delle impostazioni, nonché la dichiarazione e l'implementazione di comandi che è possibile richiamare la finestra di comando.|  
|[Importazioni dell'editor](../extensibility/editor-imports.md)|Elenca i servizi che è possibile importare un'estensione.|  
|[Adattamento del codice Legacy nell'editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Vengono illustrati diversi modi per adattare il codice legacy (pre-Visual Studio 2010) per estendere l'editor.|  
|[Migrazione di un servizio di linguaggio Legacy](../extensibility/internals/migrating-a-legacy-language-service.md)|Viene illustrato come eseguire la migrazione di un servizio di linguaggio basato su VSPackage.|  
|[Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Viene illustrato come collegare un tipo di contenuto per un'estensione di file.|  
|[Procedura dettagliata: Creazione di un glifo di margine](../extensibility/walkthrough-creating-a-margin-glyph.md)|Viene illustrato come aggiungere un'icona di un margine.|  
|[Procedura dettagliata: Evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md)|Viene illustrato come utilizzare *tag* per evidenziare il testo.|  
|[Procedura dettagliata: Definizione della struttura](../extensibility/walkthrough-outlining.md)|Viene illustrato come aggiungere la struttura per tipi specifici di parentesi graffe.|  
|[Procedura dettagliata: Visualizzazione della corrispondenza parentesi graffe](../extensibility/walkthrough-displaying-matching-braces.md)|Viene illustrato come evidenziare parentesi graffe corrispondenti.|  
|[Procedura dettagliata: Visualizzazione delle informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Viene illustrato come visualizzare i popup informazioni rapide che descrivono gli elementi di codice, ad esempio proprietà, metodi ed eventi.|  
|[Procedura dettagliata: Visualizzazione della funzionalità di supporto alla firma](../extensibility/walkthrough-displaying-signature-help.md)|Viene illustrato come visualizzare i popup che offrono informazioni relative a numero e tipi di parametri in una firma.|  
|[Procedura dettagliata: Visualizzazione del completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)|Viene illustrato come implementare il completamento delle istruzioni.|  
|[Procedura dettagliata: Implementazione di frammenti di codice](../extensibility/walkthrough-implementing-code-snippets.md)|Viene illustrato come implementare l'espansione del frammento di codice.|  
|[Procedura dettagliata: Visualizzazione dei suggerimenti delle icone lampadina](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Viene illustrato come visualizzare le lampadine per i suggerimenti di codice.|  
|[Procedura dettagliata: Uso di un comando della shell con un'estensione dell'editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Viene illustrato come associare un comando di menu in un pacchetto VSPackage a un componente MEF.|  
|[Procedura dettagliata: Uso di una combinazione di tasti con un'estensione dell'editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Viene illustrato come associare un collegamento di menu in un pacchetto VSPackage a un componente MEF.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Vengono fornite informazioni su Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Vengono fornite informazioni su Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Riferimenti  
 L'editor di Visual Studio include i seguenti spazi dei nomi.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>