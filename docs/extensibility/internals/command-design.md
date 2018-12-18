---
title: Comando progettazione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 43b83e5a02fb84ad09531f87b3120168bad0b2e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="command-design"></a>Progettazione di comando
Quando si aggiunge un comando a un VSPackage, è necessario specificare dove verrà visualizzato quando è disponibile e come è possibile gestire.  
  
## <a name="defining-commands"></a>Definizione di comandi  
 Per definire nuovi comandi, includere un file di Visual Studio Command Table (vsct) nel progetto VSPackage. Se è stato creato un pacchetto VSPackage usando il modello di pacchetto di Visual Studio, il progetto include uno di questi file. Per ulteriori informazioni, vedere [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio unisce tutti i file con estensione vsct che rileva in modo da poter visualizzare i comandi. Poiché questi file sono distinti dal VSPackage binario, Visual Studio non è necessario caricare il pacchetto per trovare i comandi. Per ulteriori informazioni, vedere [come VSPackage aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio Usa il <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> attributo di registrazione per definire le risorse di menu e comandi. Per ulteriori informazioni, vedere [implementazione](../../extensibility/internals/command-implementation.md).  
  
 I comandi possono essere modificati in fase di esecuzione in un numero di modi diversi. Si può essere visualizzati o nascosti, abilitati o disabilitati. Possono visualizzare un testo diverso o icone, o contenere valori diversi. Sono disponibili numerose personalizzazione può essere eseguita prima di Visual Studio carica il pacchetto VSPackage. Per ulteriori informazioni, vedere [come VSPackage aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Gestori di comandi  
 Quando si crea un comando, è necessario fornire un gestore eventi per eseguire il comando. Se l'utente seleziona il comando, devono essere indirizzato in modo appropriato. Routing di un comando significa inviarlo al pacchetto VSPackage corretto per abilitare o disabilitare la funzionalità, nascondere o visualizzarli ed eseguirlo se l'utente sceglie di eseguire questa operazione. Per ulteriori informazioni, vedere [algoritmo di Routing](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Ambiente di comando di Visual Studio  
 Visual Studio può ospitare un numero qualsiasi di VSPackage e ogni può comportare un proprio set di comandi. L'ambiente consente di visualizzare solo i comandi appropriati per l'attività corrente. Per ulteriori informazioni, vedere [disponibilità](../../extensibility/internals/command-availability.md) e [selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md).  
  
 Un VSPackage che definisce i nuovi comandi, menu, barre degli strumenti o menu di scelta rapida fornisce le informazioni di comando di Visual Studio al momento dell'installazione tramite le voci del Registro di sistema che fanno riferimento a risorse in assembly nativo o gestito. Ogni risorsa fa quindi riferimento a un file di risorse (CTO) di dati binari, viene generato quando si compila un file di Visual Studio Command Table (vsct). Ciò consente a Visual Studio per set di comandi unito, menu e barre degli strumenti senza dover caricare ogni VSPackage installato.  
  
### <a name="command-organization"></a>Organizzazione di comando  
 L'ambiente posiziona i comandi di menu, gruppo e priorità.  
  
-   I gruppi sono raccolte logiche di comandi correlati, ad esempio, il **Taglia**, **copia**, e **Incolla** del gruppo di comandi. I gruppi sono i comandi che vengono visualizzati nei menu.  
  
-   La priorità determina l'ordine in cui singoli comandi in un gruppo visualizzato nel menu.  
  
-   Menu fungono da contenitori per i gruppi.  
  
 L'ambiente sono disponibili alcuni comandi, gruppi e i menu. Per ulteriori informazioni, vedere [comando predefinito, gruppo e il posizionamento della barra degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Un comando può essere assegnato a un gruppo primario. Il gruppo primario controlla la posizione del comando nella struttura di menu principale e nel **Personalizza** la finestra di dialogo. Un comando può essere visualizzati in più gruppi; ad esempio, un comando può essere nel menu principale, in un menu di scelta rapida e su una barra degli strumenti. Per ulteriori informazioni, vedere [come VSPackage aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>comandi (routing)  
 Il processo di chiamata e routing di comandi per pacchetti VSPackage è diverso dal processo di chiamata ai metodi nelle istanze di un oggetto.  
  
 L'ambiente indirizza i comandi in sequenza dal contesto del comando (local) più interno, che prevede la selezione corrente, per il contesto più esterno (globale). Il primo contesto che è in grado di eseguire il comando è quello che la gestisce. Per ulteriori informazioni, vedere [algoritmo di Routing](../../extensibility/internals/command-routing-algorithm.md).  
  
 Nella maggior parte dei casi, l'ambiente gestisce i comandi utilizzando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Poiché molti oggetti diversi gestire i comandi, viene abilitata la combinazione di routing di comandi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> può essere implementata da qualsiasi numero di oggetti; questi includono controlli Microsoft ActiveX, le implementazioni di visualizzazione di finestra, oggetti documento, le gerarchie di progetto, e oggetti VSPackage stessi (per i comandi globali). In alcuni casi speciali, ad esempio, routing dei comandi in una gerarchia, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia deve essere implementata.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Implementazione](../../extensibility/internals/command-implementation.md)|Viene descritto come implementare i comandi in un pacchetto VSPackage.|  
|[Disponibilità](../../extensibility/internals/command-availability.md)|Descrive come contesto di Visual Studio determina quali comandi sono disponibili.|  
|[Algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md)|Viene descritto come architettura del routing dei comandi di Visual Studio consenta i comandi devono essere gestiti da diversi pacchetti VSPackage.|  
|[Linee guida per la selezione host](../../extensibility/internals/command-placement-guidelines.md)|Viene spiegato come posizionare i comandi nell'ambiente di Visual Studio.|  
|[Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Viene descritto come i VSPackage possono utilizzare al meglio l'architettura di comandi di Visual Studio.|  
|[Posizionamento predefinito di comandi, gruppi e barre degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Viene descritto il VSPackage possono meglio utilizzare i comandi inclusi in Visual Studio.|  
|[Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)|Descrive la modalità di caricamento VSPackage in Visual Studio.|  
|[File Visual Studio Command Table (VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Vengono fornite informazioni sui file vsct basato su XML, che vengono utilizzati per descrivere il layout e l'aspetto dei comandi in VSPackage.|