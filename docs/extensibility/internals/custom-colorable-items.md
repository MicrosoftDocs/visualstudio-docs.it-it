---
title: Gli elementi di colori personalizzati | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 78c4823e3644dc755cef518dcbbba5f42c7aebc1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="custom-colorable-items"></a>Elementi di colori personalizzati
È possibile sostituire l'elenco dei tipi per colorare, ad esempio parole chiave e commenti, mediante l'implementazione di elementi di colori personalizzati come parte del servizio di linguaggio.  
  
## <a name="user-settings-of-colorable-items"></a>Impostazioni utente di colori  
 È possibile visualizzare il **tipi di carattere e colori** la finestra di dialogo selezionando **opzioni** sul **strumenti** menu e selezionando quindi **tipi di carattere e colori** in **ambiente**. Quando si seleziona una visualizzazione, ad esempio **Editor di testo** o **finestra di comando**, **visualizzare gli elementi** casella di riepilogo Mostra tutti gli elementi colorabile predefiniti per tale visualizzazione. È possibile visualizzare e modificare il tipo di carattere, dimensioni, colore di primo piano e il colore di sfondo per ogni elemento colorabile. Le scelte sono archiviate in una cache nel Registro di sistema e a cui accede il nome dell'elemento colorabile.  
  
## <a name="presentation-of-colorable-items"></a>Presentazione dei colori  
 Poiché l'IDE gestisce l'override dell'utente di elementi colorabili nel **tipi di carattere e colori** la finestra di dialogo, è necessario fornire solo con un nome di ogni elemento colorabile. Questo nome viene visualizzata nel **visualizzare gli elementi** elenco. Gli elementi di colori vengono visualizzati in ordine alfabetico. Per raggruppare gli elementi di colori personalizzati del servizio di linguaggio, è possibile iniziare ogni nome con il nome di lingua, ad esempio **NewLanguage - commento** e **NewLanguage - parola chiave**.  
  
> [!CAUTION]
>  È necessario includere il nome della lingua nel nome dell'elemento colorabile predefinito per evitare conflitti con i nomi di elemento colorabile esistenti. Se si modifica il nome di uno degli elementi colorabili durante lo sviluppo, è necessario reimpostare la cache è stata creata la prima volta che gli elementi colorabili erano accessibili. È possibile reimpostare la cache con lo strumento CreateExpInstance, che viene installato con Visual Studio SDK, in genere nella directory sperimentale  
>   
>  **C:\Programmi\Microsoft file (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Per reimpostare la cache, chiamare `CreateExpInstance /Reset`. Per ulteriori informazioni su CreateExpInstance, vedere [utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 Il primo elemento nell'elenco di colori non viene mai fatto riferimento. Il primo elemento corrisponde a un indice di elemento colorabile predefinito pari a 0, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sempre fornisce gli attributi per l'elemento e i colori predefiniti del testo. Il modo più semplice gestire con questo elemento privo di riferimento consiste nel fornire un elemento colorabile segnaposto nell'elenco come primo elemento.  
  
## <a name="implementing-custom-colorable-items"></a>Implementazione di elementi di colori personalizzati  
  
1.  Definire cosa deve essere colorata nella propria lingua, ad esempio (parola chiave), operatore e identificatore.  
  
2.  Creare un'enumerazione di questi elementi colorabile.  
  
3.  Associare i tipi di token restituiti da un parser o con i valori enumerati.  
  
     Ad esempio, i valori che rappresentano i tipi di token potrebbero essere gli stessi valori dell'enumerazione di elementi di colori personalizzati.  
  
4.  Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> di oggetto, riempire un elenco di attributi con i valori dell'enumerazione di elementi colorabile personalizzato corrispondente per i tipi di token restituiti dal parser o scanner.  
  
5.  Nella stessa classe che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia, implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaccia e i relativi due metodi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7.  Se si desidera supportare i valori di colore a 24 bit o ad alta, implementare anche il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia.  
  
8.  Nell'oggetto servizio di linguaggio, creare un elenco che contiene il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> oggetti, uno per ogni elemento colorabile possibile identificare il parser o scanner.  
  
     È possibile accedere a ogni elemento nell'elenco utilizzando il corrispondente valore dall'enumerazione elementi colori personalizzati. Utilizzare i valori di enumerazione come indice nell'elenco. Il primo elemento nell'elenco non viene mai eseguito l'accesso, poiché per il testo predefinito corrisponde allo stile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sempre gestisce se stesso. È possibile compensare per questo oggetto tramite l'inserimento di un elemento colorabile segnaposto all'inizio dell'elenco.  
  
9. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metodo, restituire il numero di elementi nell'elenco di elementi di colori personalizzati.  
  
10. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> (metodo), restituiscono l'elemento colorabile richiesto dall'elenco.  
  
 Per un esempio di come implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfacce, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Vedere anche  
 [Modello di un servizio di linguaggio Legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Sintassi colorazione nell'editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [In un servizio di linguaggio Legacy colorazione sintassi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementazione di colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Procedura: Usare gli elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)