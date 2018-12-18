---
title: Utilizzo di tipi di carattere e colori | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4415d00e5a1233bfdf14dbc86a3a7ed2f7b8e770
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-fonts-and-colors"></a>Utilizzo di tipi di carattere e colori
Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce il supporto per l'utilizzo di tipi di carattere e colori per visualizzare il testo.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Panoramica di colore e tipo di carattere](../extensibility/font-and-color-overview.md)  
 Vengono illustrate le impostazioni di carattere e colori testo nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Inoltre vengono presentati i concetti di categorie e di elementi visualizzati e viene descritto come i pacchetti VSPackage e l'editor di componenti di base utilizzare attributi di testo.  
  
 [Recupero di tipo di carattere e colore per testo colorazione](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Vengono fornite linee guida per l'implementazione di colorazione di testo in pacchetti VSPackage che gestiscono **categorie** diverso da **Editor di testo**.  
  
 [L'accesso a carattere archiviato e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md)  
 Viene illustrato come corrente carattere e colori impostazioni possono essere archiviate, recuperate e applicate.  
  
 [Implementazione di elementi visualizzati e categorie personalizzate](../extensibility/implementing-custom-categories-and-display-items.md)  
 Vengono descritti i passaggi di base da cui è possibile creare e utilizzare il proprio di una finestra **visualizzare elementi** e **categorie** per supportare la visualizzazione del testo.  
  
 Questo approccio richiede un pacchetto VSPackage implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaccia e interfacce correlate.  
  
 [Procedura: accedere ai tipi di carattere incorporati e una combinazione di colori](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Viene descritto come definire e registrare una categoria utilizzando colori e tipi di carattere incorporati e avviare l'utilizzo di fornita dal sistema di tipi di carattere e colori.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Fornisce un'istanza del `IVsFontAndColorDefaults` o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaccia che corrisponde a un particolare elemento nel **Mostra impostazioni per** nell'elenco di **tipi di carattere e colori** pagina della finestra di **Opzioni** la finestra di dialogo.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Consente a un pacchetto VSPackage supportare l'IDE **tipi di carattere e colori** pagina mediante la definizione di tipi di carattere predefiniti e i colori per una finestra o un componente dell'interfaccia utente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Fornisce un meccanismo mediante il quale un VSPackage che fornisce il supporto di carattere e colori è possibile specificare un gruppo di visualizzazione elemento - una categoria Super che rappresenta l'unione di due o più categorie.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Consente a un pacchetto VSPackage recuperare i dati di carattere e colori, o salvarlo nel Registro di sistema.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifica a VSPackage che utilizzano le informazioni di carattere e colori sulle modifiche nelle impostazioni di carattere e colori.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Fornisce strumenti per lavorare con i dati di input e outpui che viene utilizzati dai metodi del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **carattere e colori** meccanismo.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Controlla la memorizzazione nella cache delle impostazioni di carattere e colori.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)  
 Viene spiegato VSPackage possono utilizzare servizi di linguaggio per personalizzare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
 [Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries come [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor utilizza servizi di linguaggio per implementare la colorazione della sintassi.  
  
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Viene illustrato come utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] services per creare elementi dell'interfaccia utente che corrispondano al resto del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].