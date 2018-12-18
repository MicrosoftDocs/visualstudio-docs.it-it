---
title: I comandi, menu e barre degli strumenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa1513bcd61ac63fb9d2a59f69a8b2ce22cf5114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="commands-menus-and-toolbars"></a>I comandi, menu e barre degli strumenti
Menu e barre degli strumenti sono che consente agli utenti di accedere ai comandi nel pacchetto VSPackage. I comandi sono funzioni che eseguono attività, ad esempio la stampa di un documento, l'aggiornamento di una visualizzazione o la creazione di un nuovo file. Menu e barre degli strumenti sono pratici metodi grafici per presentare i comandi agli utenti. In genere, i comandi correlati sono raggruppati nello stesso menu o sulla stessa barra degli strumenti.  
  
-   I menu vengono in genere visualizzati come stringhe di una sola parola raggruppate su una riga nella parte superiore dell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) o in una finestra degli strumenti. I menu possono essere visualizzati anche come risultato di un evento di clic con il pulsante destro del mouse e in tal caso vengono definiti menu di scelta rapida. Quando si fa clic su di essi, i menu si espandono per visualizzare uno o più comandi. Facendo clic sui comandi è possibile eseguire attività oppure aprire sottomenu che contengono altri comandi. Alcuni nomi di menu molto noti sono File, Modifica, Visualizza e Finestra. Per ulteriori informazioni, vedere [estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
-   Le barre degli strumenti sono in genere righe di pulsanti e altri controlli, ad esempio caselle combinate, caselle di riepilogo, caselle di testo e controller di menu. Tutti i controlli delle barre degli strumenti sono associati a comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene attivato il comando associato. I pulsanti della barra degli strumenti hanno in genere icone che suggeriscono i comandi sottostanti, ad esempio una stampante per un comando Stampa. In un controllo elenco a discesa, ogni elemento nell'elenco è associato a un comando diverso. Un controller di menu è un oggetto ibrido in cui un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia rivolta verso il basso che visualizza altri comandi quando si fa clic su di essa. Per ulteriori informazioni, vedere [aggiunta di un Controller di Menu per una barra degli strumenti](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Quando si crea un comando, è anche necessario creare un gestore eventi per esso. Il gestore eventi determina quando il comando è visibile o abilitato, consente di modificarne il testo e garantisce che il comando risponda in modo appropriato ("routing") quando attivato. Nella maggior parte dei casi, l'IDE gestisce i comandi usando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. I comandi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] route in modo gerarchico, a partire dal contesto del comando più interno, in base alla selezione locale e procedendo verso il contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo scripting. Per ulteriori informazioni, vedere [tra oggetti MenuCommand e. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) e [selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md).  
  
 Per definire nuovi menu e barre degli strumenti, è necessario descriverli in un file VSCT (Visual Studio Command Table). Il modello di pacchetto di Visual Studio crea automaticamente questo file, insieme agli elementi necessari per supportare qualsiasi comando, barra degli strumenti ed editor selezionato nel modello. In alternativa, è possibile scrivere il proprio file vsct, usando il linguaggio xml schema descritto qui: [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
 Per ulteriori informazioni sull'utilizzo dei file con estensione vsct, vedere [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Negli argomenti di questa sezione spiegano il funzionamento di comandi, menu e barre degli strumenti in VSPackage.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Una descrizione dettagliata della specifica di formato di tabella comandi.  
  
 [File Visual Studio Command Table (VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Viene descritto un basato su XML e alla sintassi per le tabelle di comando.  
  
 [Posizionamento predefinito di comandi, gruppi e barre degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Descrive barre degli strumenti, gruppi, i menu e comandi predefiniti.  
  
 [Comandi, menu e gruppi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Specifica il menu predefiniti, comandi e i gruppi di comandi disponibili per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Progettazione dei comandi](../../extensibility/internals/command-design.md)  
 Descrive come progettare i comandi.  
  
 [Ottimizzazione dei comandi di menu e barre degli strumenti](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Vengono fornite indicazioni per i comandi.  
  
 [Miglioramento della disponibilità dei comandi](../../extensibility/internals/making-commands-available.md)  
 Viene illustrato come rendere disponibili i comandi di Visual Studio.  
  
 [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Viene illustrato come implementare i comandi che usano gli assembly di interoperabilità.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Routing dei comandi nei pacchetti VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Viene illustrato il routing di comandi in VSPackage.