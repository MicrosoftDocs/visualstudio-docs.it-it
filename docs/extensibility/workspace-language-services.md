---
title: Aree di lavoro e servizi di linguaggio in Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 551a621ab97c232970d6ef67da14379c5cdfbd46
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="workspaces-and-language-services"></a>Aree di lavoro e servizi di linguaggio

Possono fornire servizi di linguaggio [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) agli utenti la stessa funzionalità del linguaggio avanzata sono utilizzati per quando si lavora con soluzioni e progetti. Un servizio di linguaggio potrebbe attivarsi in base all'estensione di file o il contenuto di un documento aperto anche se questo servizio di linguaggio "file separato" è limitato a evidenziazione della sintassi. Sono necessarie informazioni aggiuntive per garantire un'esperienza più completa per la modifica/revisione del codice sorgente. Ogni servizio di linguaggio ha una proprio API per l'inizializzazione con i dati extra contestuali per un documento. È in genere gestita da un sistema di progetto, è strettamente collegato al servizio di linguaggio e al sistema di compilazione.

## <a name="initialization"></a>Inizializzazione

In un [dell'area di lavoro](workspaces.md), servizi di linguaggio vengono inizializzati da un <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> punto dell'estensione che progettato solo per tale servizio di linguaggio e non la creazione di compilazione è a conoscenza. In questo modo, un proprietario del servizio di linguaggio può mantenere un'unica cartella aperta estensione indipendentemente dal modo in cui numerosi modelli esiste all'interno di cartelle e file per l'esecuzione delle loro del compilatore durante la compilazione (ad esempio MSBuild, makefile e così via). Quando i file da cui è stato creato un contesto di file vengono modificati sul disco e il contesto di file viene aggiornato, il provider del servizio di linguaggio viene notificato l'insieme aggiornato di contesti di file. Il provider del servizio di linguaggio possibile aggiornare il modello.

Quando un documento viene aperto nell'editor, Visual Studio prende in considerazione esclusivamente language i provider di servizi che richiedono i tipi di contesto di file per cui è possibile trovare un provider di contesto di file corrispondente. Passa quindi i contesti dei file dal provider corrispondente al provider di servizi lingua selezionata tramite `ILangaugeServiceProvider.InitializeAsync`. Il provider del servizio di linguaggio scopo con che i dati di contesto di file sono un dettaglio di implementazione del provider del servizio di linguaggio, ma l'esperienza utente previsto è un servizio di linguaggio più completo per tale documento aperto.

## <a name="using-ilanguageserviceprovider"></a>Utilizzo ILanguageServiceProvider

Il servizio di linguaggio verrà visualizzato un messaggio viene creato un contesto di file con un `ContextType` che corrisponde a uno del `SupportedContextTypes` i valori del server language export (attributo).

Per supportare un servizio di linguaggio, sarà necessario un'estensione:

- Univoco `Guid`. Verrà utilizzato per `SupportedContextTypes` gli argomenti di attributo e in un `FileContext` oggetto.
- Contesto di file di lingua
  - Factory del provider
    - `ExportFileContextProviderAttribute` generato in modo univoco l'attributo con il precedente `Guid` in `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementazione del provider di `IFileContextProvider.GetContextsForFileAsync`
    - Costruire un nuovo `FileContext` con il `contextType` argomento del costruttore come generato in modo univoco `Guid`
    - Utilizzare il `Context` proprietà del `FileContext` per fornire dati aggiuntivi per il `ILanguageServiceProvider`
- Servizio di linguaggio
  - Factory del provider
    - `ExportLanguageServiceProvider` generato in modo univoco l'attributo con il precedente `Guid` in `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Provider
    - Implementa `ILanguageServiceProvider`
    - Utilizzare `ILanguageServiceProvider.InitializeAsync` per abilitare i servizi di linguaggio per gli argomenti forniti quando viene aperto un file
    - Utilizzare `ILanguageServiceProvider.UninitializeAsync` per disabilitare i servizi di linguaggio per gli argomenti forniti quando viene chiuso un file

>[!WARNING]
>Il `ILanguageServiceProvider` metodi potrebbero essere richiamati nell'area di lavoro nel thread principale. È consigliabile pianificare lavoro su un thread diverso per evitare di introdurre ritardi dell'interfaccia utente.

## <a name="language-server-protocol"></a>Protocollo di lingua del Server

Il `Microsoft.VisualStudio.Workspace.*` API non sono l'unico modo per abilitare il servizio di linguaggio nella cartella aperta. Un'altra opzione consiste nell'utilizzare un server di linguaggio. Per altre informazioni, a conoscenza di [protocollo Server Language](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfacce correlate

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> viene richiamato quando un file di corrispondenti tipi di file è aperto o chiuso per la modifica.

## <a name="next-steps"></a>Passaggi successivi

* [Compilazione dell'area di lavoro](workspace-build.md) -Apri cartella supporta sistemi, ad esempio makefile e MSBuild di compilazione. 