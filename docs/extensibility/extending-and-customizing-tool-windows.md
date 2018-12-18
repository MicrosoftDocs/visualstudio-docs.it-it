---
title: Estendere e personalizzare le finestre degli strumenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 74616bf92b1424b4749354d1f0a7b3232e66a335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extending-and-customizing-tool-windows"></a>Estendere e personalizzare le finestre degli strumenti
Visual Studio fornisce diversi tipi di windows, ad esempio le finestre degli strumenti, finestre dei documenti e finestre di dialogo. Altre finestre, ad esempio la finestra Proprietà, la finestra di Output e la finestra Elenco attività, sono tipi di finestre degli strumenti.  
  
## <a name="tool-windows"></a>Finestre degli strumenti  
 Finestre di Visual Studio degli strumenti sono in genere di sola lettura di windows che non sono basati su file. In questo differiscono dalle finestre dei documenti, che visualizzano file in modalità di lettura/scrittura. La **casella degli strumenti**e le finestre **Esplora soluzioni**, **Proprietà** e **Web browser** sono tutte esempi di finestre degli strumenti.  
  
 Per scoprire come creare una semplice finestra degli strumenti, vedere [aggiunta di una finestra degli strumenti](../extensibility/adding-a-tool-window.md).  
  
 Per registrare una finestra degli strumenti di Visual Studio, vedere [la registrazione di una finestra degli strumenti](../extensibility/registering-a-tool-window.md).  
  
 Le finestre degli strumenti sono a istanza singola per impostazione predefinita, ovvero è possibile aprire una sola istanza di una finestra degli strumenti per volta. Una volta aperta, una finestra degli strumenti a istanza singola resta aperta fino a quando non viene chiuso l'IDE. Quando si chiude una finestra degli strumenti a istanza singola, cambia solo la sua visibilità. È anche possibile creare finestre degli strumenti a più istanze, in modo da permettere l'apertura di più istanze della finestra contemporaneamente. Vedere [la creazione di una finestra degli strumenti di multi-istanza](../extensibility/creating-a-multi-instance-tool-window.md) per ulteriori informazioni.  
  
 Le finestre degli strumenti possono essere *dinamica*, vale a dire che sono visibili ogni volta che si applica il contesto dell'interfaccia utente correlato. L'uso della visibilità automatica può ridurre il disordine delle finestre nell'IDE. Per ulteriori informazioni, vedere [aprendo una finestra degli strumenti dinamiche](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Le finestre degli strumenti possono essere ancorate, mobili o a schede nella cornice del documento. La cornice della finestra degli strumenti viene fornita dall'IDE ed è usata per controllare le dimensioni, la posizione, lo stato di ancoraggio e altre proprietà persistenti. Il riquadro della finestra degli strumenti visualizza il contenuto. Le dimensioni e la posizione predefinite vengono applicate solo alla prima apertura della finestra degli strumenti. Successivamente, lo stato della finestra viene salvato in modo permanente.  
  
 I riquadri della finestra degli strumenti possono ospitare controlli utente WPF e supportare le barre degli strumenti. È possibile eseguire l'override di <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> proprietà per restituire l'handle del controllo ospitato.  
  
 È possibile aggiungere più funzionalità diverse per le finestre degli strumenti. Ad esempio, è possibile aggiungere una barra degli strumenti: [aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) o un menu di scelta rapida: [aggiunta di un Menu di scelta rapida in una finestra degli strumenti](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). È possibile aggiungere un controllo di ricerca che consente di cercare gli elementi all'interno della finestra di strumento: [ricerca aggiunta a una finestra degli strumenti](../extensibility/adding-search-to-a-tool-window.md).  
  
 È possibile sottoscrivere eventi finestra dello strumento: [sottoscrizione a un evento](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Estensione delle finestre degli strumenti esistenti  
 È possibile aggiungere informazioni sulla finestra di strumento in un nuovo **opzioni** pagina e una nuova impostazione nel **proprietà** pagina, scrivere il **elenco attività** e **Output**  windows. Per ulteriori informazioni, vedere [estensione di proprietà, elenco attività, Output e le opzioni di Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) e [estensione di proprietà, elenco attività, Output e le opzioni di Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Finestre di dialogo modale  
 In un'estensione di Visual Studio è necessario creare finestre di dialogo modale tramite la derivazione da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, che consente di controllare queste e il resto dell'interfaccia utente. Per altre informazioni, vedere . [Creazione e la gestione delle finestre di dialogo modale](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)