---
title: Finestra Proprietà | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: accebfc02e5bba6be361cb3ab2d252f20f59314f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="properties-window"></a>Finestra Proprietà
Usare questa finestra per visualizzare e modificare in fase di progettazione le proprietà e gli eventi degli oggetti selezionati presenti in editor e finestre di progettazione. È anche possibile usare la finestra **Proprietà** per modificare e visualizzare le proprietà di file, progetto e soluzione. La finestra **Proprietà** può essere selezionata dal menu **Visualizza**. È anche possibile aprirla premendo F4 o digitando **Proprietà** nella finestra **Avvio veloce**.  
  
 Nella finestra **Proprietà** vengono visualizzati diversi tipi di campi di modifica, a seconda delle esigenze di una determinata proprietà. I campi di modifica comprendono caselle di modifica, elenchi a discesa e collegamenti a finestre di dialogo dell'editor personalizzato. Le proprietà visualizzate in grigio sono di sola lettura.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 Nome oggetto  
 Indica l'oggetto o gli oggetti attualmente selezionati. Sono visibili solo gli oggetti dell'editor o della finestra di progettazione attivi. Quando si selezionano più oggetti vengono visualizzate solo le proprietà comuni a tutti gli oggetti selezionati.  
  
 Per categoria  
 Elenca tutte le proprietà e i valori delle proprietà per l'oggetto selezionato, in base alla categoria. È possibile comprimere una categoria per ridurre il numero di proprietà visualizzate. Quando si espande o si comprime una categoria, viene visualizzato un segno più (+) o meno (-) a sinistra del nome della categoria. Le categorie sono elencate in ordine alfabetico.  
  
 Alfabetico  
 Ordina alfabeticamente tutti gli eventi e le proprietà della fase di progettazione per gli oggetti selezionati. Per modificare una proprietà attiva, fare clic nella cella a destra della proprietà e immettere le modifiche.  
  
 Pagine delle proprietà  
 Visualizza la finestra di dialogo **Pagine delle proprietà** o **Creazione progetti** per l'elemento selezionato. In Pagine delle proprietà viene visualizzato un subset, lo stesso o un superset delle proprietà disponibili nella finestra **Proprietà**. Usare questo pulsante per visualizzare e modificare le proprietà correlate alla configurazione attiva del progetto.  
  
 Proprietà  
 Visualizza le proprietà di un oggetto. Molti oggetti contengono anche eventi che possono essere visualizzati usando la finestra **Proprietà**.  
  
 Ordina per origine proprietà  
 Raggruppa le proprietà per origine, ad esempio ereditarietà, stili applicati e binding. È disponibile solo quando si modificano i file XAML nella finestra di progettazione.  
  
 Eventi  
 Visualizza gli eventi per un oggetto.  
  
> [!NOTE]
>  Questo controllo della barra degli strumenti della finestra **Proprietà** è disponibile solo quando si attiva un modulo o una finestra di progettazione controlli nel contesto di un progetto [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Quando si modificano i file XAML, gli eventi vengono visualizzati in una scheda separata della finestra Proprietà.  
  
 Messages  
 Elenca tutti i messaggi di Windows. Consente di aggiungere o eliminare funzioni specifiche del gestore per i messaggi visualizzati per la classe selezionata.  
  
> [!NOTE]
>  Questo controllo della barra degli strumenti della finestra **Proprietà** è disponibile solo quando **Visualizzazione classi** è la finestra attiva nel contesto di un progetto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Overrides  
 Indica tutte le funzioni virtuali per la classe selezionata e consente di aggiungere o eliminare funzioni per l'override.  
  
> [!NOTE]
>  Questo controllo della barra degli strumenti della finestra **Proprietà** è disponibile solo quando **Visualizzazione classi** è la finestra attiva nel contesto di un progetto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Riquadro descrizione  
 Visualizza il tipo di proprietà e una breve descrizione della proprietà. È possibile attivare e disattivare la descrizione della proprietà usando il comando Descrizione del menu di scelta rapida.  
  
> [!NOTE]
>  Questo controllo della barra degli strumenti della finestra **Proprietà** non è disponibile se si modificano i file XAML nella finestra di progettazione.  
  
 Visualizzazione anteprima  
 Visualizza una rappresentazione visiva dell'elemento attualmente selezionato quando si modificano i file XAML nella finestra di progettazione.  
  
 Cerca  
 Specifica una funzione di ricerca per le proprietà e gli eventi quando si modificano i file XAML nella finestra di progettazione. La casella di ricerca risponde alle ricerche di parole parziali e aggiorna i risultati della ricerca durante la digitazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle proprietà di progetto](../../ide/reference/project-properties-reference.md)   
 [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)