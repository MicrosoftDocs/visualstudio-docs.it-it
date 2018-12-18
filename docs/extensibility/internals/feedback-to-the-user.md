---
title: Commenti e suggerimenti all'utente | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 629d12974a52bca30c0db96e838c5c731ae1abf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="feedback-to-the-user"></a>Commenti e suggerimenti per l'utente
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE), la risposta visiva relative alle funzionalità disponibili si basa sulla selezione corrente dell'utente e il contesto di selezione globale. Nella tabella seguente sono elencate le funzionalità che sono disponibile in contesti diversi di selezione.  
  
|Contesto della selezione|Funzionalità disponibili|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Set di prodotto corrente|Prodotto specifico|  
|Gerarchia attivo|Specifica tipo di gerarchia|  
|Elemento della gerarchia Active|Specifiche del tipo di elemento gerarchia|  
|Documento attivo|Specifica tipo di documento|  
|Finestra in primo piano interfaccia a documenti multipli (MDI)|Specifica tipo di finestra|  
|Contesto della selezione corrente|Contesto della selezione specifico|  
  
 Se si mostrano solo le funzionalità necessarie agli utenti e forniscono continuamente selezione coerente e commenti e suggerimenti contesto di ambiente, si riduce la complessità nell'IDE. Le regole seguenti si applicano ogni volta che viene aperta una finestra nell'IDE:  
  
-   Se la finestra viene modificata relativo contesto di selezione, commenti e suggerimenti di selezione sono chiaramente indicato nella finestra e finestra Guida dinamica, se visualizzata, viene aggiornata per riflettere il contesto corrente.  
  
-   Se la finestra viene modificata contesto globale della selezione, tutti i menu specifici del contesto, la finestra gerarchia attivo e barra del titolo dell'applicazione vengono aggiornati per riflettere il contesto corrente.  
  
-   La finestra dovrebbe area le proprietà per la selezione corrente nella **proprietà** finestra e, facoltativamente, se visualizzata, la **pagine delle proprietà** la finestra di dialogo.  
  
-   Se la finestra non esporre una proprietà o modificare il contesto di selezione globale, commenti e suggerimenti di selezione non devono rimanere nella finestra quando non è più la finestra attiva nell'IDE.  
  
-   Tutte le finestre di documento specifico strumento continuamente devono riflettere il documento attivo.  
  
-   Menu, barre degli strumenti e barra del titolo dell'applicazione deve riflettere finestra del client di livello più alto interfaccia a documenti multipli (MDI).  
  
 Ad esempio, quando viene aperta la visualizzazione HTML di un Web Form all'interno di un progetto di applicazione Web di Visual Basic e l'utente seleziona un `<td>` tag, viene fornito un feedback nel modo seguente:  
  
-   La selezione è indicata nella finestra attiva e applicata le **proprietà** finestra.  
  
-   Specifica del documento **della casella degli strumenti** viene aggiornata per riflettere il documento attivo.  
  
-   Il **Editor** barra degli strumenti e **tabella** vengono visualizzati i menu e barra del titolo aggiorna in modo da riflettere la finestra del Web Form.  
  
-   Finestra gerarchia attivo in cui è in genere **Esplora**e l'aggiornamento della barra del titolo in modo da riflettere il contesto corrente e il sensibile al contesto **progetto** applicano i comandi di menu per il Web attivo Progetto di applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Selezione e la valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md)   
 [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)