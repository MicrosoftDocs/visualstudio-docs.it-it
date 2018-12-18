---
title: Iniziando a sviluppare estensioni di Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 09/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7bc03568465efa022981ade059b0de68019a5978
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Iniziando a sviluppare estensioni di Visual Studio
Se è mai stata scritta un'estensione di Visual Studio prima di, è probabile che alcune domande. È stata elencate alcune di quelle più comuni. Se le informazioni che si sta cercando non viene visualizzato, utilizzare i pulsanti di commenti e suggerimenti (**questa pagina è stata utile?** nella parte inferiore dello schermo) per chiedere a quello desiderato.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Il software necessario sviluppare estensioni di Visual Studio?  
 È necessario installare Visual Studio SDK, oltre a Visual Studio per sviluppare estensioni di Visual Studio. È possibile installare Visual Studio SDK come parte del programma di installazione normale, oppure è possibile installare in un secondo momento. Per ulteriori informazioni sull'installazione di Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Tipi di elementi può fare con estensioni di Visual Studio?  
 Il sky's il limite per quanto concerne possibile immaginare di diverse estensioni di Visual Studio. Naturalmente, la maggior parte delle estensioni dispongono di un elemento con la scrittura di codice, ma che non deve essere il caso. Di seguito sono riportati alcuni esempi dei tipi di estensioni che è possibile compilare:  
  
-   Supporto per lingue che non sono inclusi in Visual Studio, con la colorazione della sintassi, IntelliSense e il supporto del compilatore ed eseguire il debug  
  
-   Strumenti di produttività che estendono il nucleo IDE esperienza con altri modelli, finestre di dialogo codice refactoring, nuova o finestre degli strumenti  
  
-   Finestre di progettazione di specifico di dominio per scenari come il supporto di progettazione o il cloud di dati  
  
 Per esempi di estensioni, consultare il [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Molte estensioni sono open source e Marketplace include i collegamenti per i repository GitHub. 
  
## <a name="which-visual-studio-features-can-i-extend"></a>Le funzionalità di Visual Studio è possibile estendere?  
 In teoria, è possibile estendere qualsiasi parte di Visual Studio: menu, barre degli strumenti, comandi, windows, soluzioni, progetti, editor e così via.  
  
 In pratica, è stato rilevato che le funzionalità che maggior parte degli utenti desidera estendere sono comandi, menu e barre degli strumenti, windows, IntelliSense e progetti. Di seguito sono forniti collegamenti alle sezioni rilevanti:  
  
-   [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md): aggiungere i propri elementi di barre degli strumenti e menu di Visual Studio. È possibile utilizzare tali avviare nuove funzionalità di Visual Studio o alle applicazioni di supporto esterna. È anche possibile fornire collegamenti personalizzati per le voci di menu.  
  
-   [Estensione e le finestre degli strumenti personalizzazione](../extensibility/extending-and-customizing-tool-windows.md): estendere le finestre degli strumenti esistente o creare finestre degli strumenti. Ad esempio, è possibile aggiungere nuove proprietà per il **proprietà**, oppure è possibile creare una nuova finestra degli strumenti per aggiungere ulteriori funzionalità.  
  
-   [Editor e le estensioni del servizio di linguaggio](../extensibility/editor-and-language-service-extensions.md): aggiungere le proprie personalizzazioni IntelliSense fornita per i linguaggi di Visual Studio o creare il supporto per nuovi linguaggi di programmazione. È possibile creare nuovi completamento delle istruzioni, suggerimenti e le descrizioni comandi informazioni rapide di nuovo. Con le lampadine, è possibile aggiungere refactoring suggerimenti e correzioni di codice per supportare nuovi linguaggi di programmazione.  
  
-   [Estensione dei progetti](../extensibility/extending-projects.md)  
  
-   [Estensione di opzioni e impostazioni utente](../extensibility/extending-user-settings-and-options.md)  
  
-   [Estensione delle proprietà e della finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>I modelli di progetto forniti da Visual Studio SDK?  
 I due tipi principali di estensioni sono VSPackage ed estensioni MEF. In generale, le estensioni VSPackage vengono utilizzate per le estensioni che utilizzano o estendono i comandi, finestre degli strumenti e progetti. Le estensioni MEF vengono utilizzate per estendere o personalizzare l'editor di Visual Studio.  
  
 Per le estensioni di Visual c# e Visual Basic, Visual Studio SDK fornisce un modello di progetto vuoto di VSIX che è possibile utilizzare insieme i nuovi modelli di elemento che crea i comandi di menu, finestre degli strumenti e le estensioni di editor. È anche possibile utilizzare questo modello per modelli di progetto di pacchetto, frammenti di codice e altri elementi da distribuire ad altri utenti.  
  
 Per C++, la procedura guidata VSPackage fornisce il codice per aggiungere i comandi di menu e finestre degli strumenti editor personalizzati.  
  
 Il modello della Shell isolata viene utilizzato per creare il pacchetto in una versione di shell di Visual Studio che è possibile personalizzare e distribuire la propria estensione. Gli argomenti seguenti mostrano come iniziare a utilizzare ogni tipo di estensione:  
  
-   I comandi di menu: [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Finestre degli strumenti: [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Estensioni Editor: [creazione di un'estensione con un modello di elemento di Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Pacchetti VSPackage di base: [creazione di un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Modello di progetto VSIX: [Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Shell isolata di Visual Studio: [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Come ottenere l'estensione come Visual Studio?  
 Ottenere suggerimenti per la progettazione dell'interfaccia utente per l'estensione in [linee guida esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Dove trovare gli esempi di codice VSSDK  
 Ognuno dei collegamenti presenti nella sezione precedente sono incluse le procedure dettagliate che illustrano come implementare le funzionalità specifiche. È anche possibile trovare open source di esempi di VSSDK su GitHub in [esempi di Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Come è possibile distribuire l'estensione?  
 È possibile installare l'estensione in un altro computer o inviarlo ai tuoi amici come un file con estensione VSIX, che viene installato facendo doppio clic. È possibile trovare ulteriori informazioni sui pacchetti VSIX [Shipping estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 È anche possibile pubblicare l'estensione di Visual Studio Marketplace, che rende visibili a un numero elevato di clienti di Visual Studio. Per un esempio di creazione del pacchetto un'estensione per il Marketplace, vedere [procedura dettagliata: pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Per ulteriori informazioni sui requisiti necessari per pubblicare in Marketplace, vedere [prodotti e le estensioni per Visual Studio](/vsts/integrate/ide/extensions/overview).
