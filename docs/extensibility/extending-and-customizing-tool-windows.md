---
title: Estensione e personalizzazione delle finestre degli strumenti | Microsoft Docs
description: Informazioni sull'estensione e la personalizzazione delle finestre degli strumenti fornite da Visual Studio, tra cui il Finestra Proprietà, la finestra di output e la finestra di Elenco attività.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e5b5615b8b004dcbdfe860ba4d775a3ace177ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075224"
---
# <a name="extend-and-customize-tool-windows"></a>Estendi e Personalizza le finestre degli strumenti
Visual Studio offre diversi tipi di finestre, ad esempio finestre degli strumenti, finestre dei documenti e finestre di dialogo. Altre finestre, ad esempio la finestra **Proprietà** , la finestra di **output** e la finestra di **elenco attività** , sono tipi di finestre degli strumenti.

## <a name="tool-windows"></a>Finestre degli strumenti
 Le finestre degli strumenti di Visual Studio sono in genere finestre di sola lettura che non sono basate su file. In questo differiscono dalle finestre dei documenti, che visualizzano file in modalità di lettura/scrittura. La **casella degli strumenti** e le finestre **Esplora soluzioni**, **Proprietà** e **Web browser** sono tutte esempi di finestre degli strumenti.

 Per informazioni su come creare una semplice finestra degli strumenti, vedere [aggiungere una finestra degli strumenti](../extensibility/adding-a-tool-window.md).

 Per registrare una finestra degli strumenti con Visual Studio, vedere [registrare una finestra degli strumenti](../extensibility/registering-a-tool-window.md).

 Le finestre degli strumenti sono a istanza singola per impostazione predefinita, ovvero è possibile aprire una sola istanza di una finestra degli strumenti per volta. Una volta aperta, una finestra degli strumenti a istanza singola resta aperta fino a quando non viene chiuso l'IDE. Quando si chiude una finestra degli strumenti a istanza singola, viene modificata solo la relativa visibilità. È anche possibile creare finestre degli strumenti a più istanze, in modo da permettere l'apertura di più istanze della finestra contemporaneamente. Per altre informazioni, vedere [creare una finestra degli strumenti a più istanze](../extensibility/creating-a-multi-instance-tool-window.md) .

 Le finestre degli strumenti possono essere *dinamiche*, vale a dire che sono visibili ogni volta che viene applicato il contesto dell'interfaccia utente correlato. L'uso della visibilità automatica può ridurre il disordine delle finestre nell'IDE. Per altre informazioni, vedere [aprire una finestra degli strumenti dinamica](../extensibility/opening-a-dynamic-tool-window.md).

 Le finestre degli strumenti possono essere ancorate, mobili o a schede nella cornice del documento. La cornice della finestra degli strumenti viene fornita dall'IDE ed è usata per controllare le dimensioni, la posizione, lo stato di ancoraggio e altre proprietà persistenti. Il riquadro della finestra degli strumenti visualizza il contenuto. Le dimensioni e la posizione predefinite vengono applicate solo alla prima apertura della finestra degli strumenti. Successivamente, lo stato della finestra viene salvato in modo permanente.

 I riquadri della finestra degli strumenti possono ospitare controlli utente WPF e supportare le barre degli strumenti. È possibile eseguire l'override della proprietà <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> per restituire l'handle del controllo ospitato.

 È possibile aggiungere molte funzionalità diverse alle finestre degli strumenti. Ad esempio, è possibile aggiungere una barra degli strumenti: [aggiungere una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) o a un menu di scelta rapida: [aggiungere un menu di scelta rapida in una finestra degli strumenti](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). È possibile aggiungere un controllo di ricerca che consente di cercare gli elementi all'interno della finestra degli strumenti: [aggiungere la ricerca a una finestra degli strumenti](../extensibility/adding-search-to-a-tool-window.md).

 È possibile sottoscrivere gli eventi della finestra degli strumenti: [sottoscrivere un evento](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Estendi le finestre degli strumenti esistenti
 È possibile aggiungere informazioni sulla finestra degli strumenti a una nuova pagina di **Opzioni** e una nuova impostazione nella pagina **Proprietà** , scrivere nelle finestre **elenco attività** e **output** . Per altre informazioni, vedere [estendere le finestre Proprietà, elenco attività, output e opzioni](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Finestre di dialogo modali
 In un'estensione di Visual Studio è necessario creare finestre di dialogo modali mediante la derivazione da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , che consente di controllarle e il resto dell'interfaccia utente. Per altre informazioni, vedere [creare e gestire finestre di dialogo modali](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Vedi anche
- [Creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Estendi progetti](../extensibility/extending-projects.md)
- [Estendi soluzioni](../extensibility/extending-solutions.md)
