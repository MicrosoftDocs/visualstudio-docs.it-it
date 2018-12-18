---
title: Proprietà di visualizzazione griglia | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 279450126cfcc7edba9398632e20bfb75e312b89
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="properties-display-grid"></a>Griglia di visualizzazione delle proprietà
Il **proprietà** finestra vengono visualizzati i campi all'interno di una griglia. La colonna a sinistra contiene i nomi delle proprietà; la colonna di destra contiene i valori delle proprietà.  
  
## <a name="working-with-the-grid"></a>Utilizzo della griglia  
 L'elenco di due colonne Mostra proprietà indipendenti dalla configurazione che può essere modificata in fase di progettazione e le relative impostazioni correnti. Si noti che tutte le proprietà potrebbero non essere visualizzate. Una proprietà può essere impostata come nascosto, ad esempio, implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metodo. In particolare, per nascondere proprietà con proprietà figlio:  
  
1.  Impostare il `pfDisplay` parametro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> a `FALSE`.  
  
2.  Impostare il `pfHide` parametro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> a `TRUE`.  
  
 Per informazioni di push per il **proprietà** finestra, l'IDE Usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene chiamato da pacchetti VSPackage per ogni finestra che contiene oggetti selezionabili con le proprietà correlate a essere visualizzati nel **proprietà** finestra. **Esplora soluzioni**dell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> chiamate `GetProperty` utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> della gerarchia di progetto per acquisire gli oggetti visualizzabili nella gerarchia.  
  
 Se il pacchetto VSPackage non supporta <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, l'IDE tenta di utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> utilizzando il valore per <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> che forniscono la gerarchia o più elementi.  
  
 Il progetto non è necessario creare VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> perché il pacchetto fornito IDE con una finestra che implementa (ad esempio, **Esplora**) costruisce <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per suo conto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> è costituita da tre metodi che vengono chiamati dall'IDE:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene il numero di oggetti selezionati da visualizzare nella **proprietà** finestra.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Restituisce il `IDispatch` gli oggetti selezionati da visualizzare nella **proprietà** finestra.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> rende possibile per gli oggetti restituiti da <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> per essere selezionate dall'utente. In questo modo il pacchetto VSPackage visivamente aggiornare la selezione visualizzata all'utente nell'interfaccia utente.  
  
 Il **proprietà** finestra estrae le informazioni dal `IDispatch` oggetti per recuperare le proprietà da esplorare. Utilizza il Visualizzatore di proprietà `IDispatch` per porre l'oggetto quali proprietà supporta eseguendo una query `ITypeInfo`, cui viene ottenuto da `IDispatch::GetTypeInfo`. Il browser Usa quindi questi valori per popolare il **proprietà** finestra e modificare i valori per le singole proprietà visualizzati nella griglia. Le informazioni di proprietà viene mantenute all'interno dell'oggetto stesso.  
  
 Poiché gli oggetti restituiti supportano `IDispatch`, il chiamante può ottenere informazioni quali il nome dell'oggetto con una chiamata a `IDispatch::Invoke` o `ITypeInfo::Invoke` con un ID di predefinito di invio (DISPID) che rappresenta le informazioni desiderate. I DISPID dichiarati sono negativi per verificare che non entrino in conflitto con gli identificatori definiti dall'utente.  
  
 Il **proprietà** finestra vengono visualizzati tipi diversi di campi in base gli attributi di proprietà specifiche di un oggetto selezionato. Questi campi includono caselle di modifica, elenchi a discesa e collegamenti a finestre di dialogo editor personalizzato.  
  
-   I valori contenuti in un elenco enumerato vengono recuperati da un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> eseguire una query da `IDispatch`. I valori ottenuti da un elenco enumerato possono essere modificati nella griglia delle proprietà facendo doppio clic sul nome del campo oppure selezionando il valore e selezionando il nuovo valore dall'elenco a discesa. Per le proprietà che dispongono di impostazioni da enumerato elenchi predefiniti, fare doppio clic sul nome della proprietà nell'elenco di proprietà consente di scorrere le scelte disponibili. Per le proprietà predefinite con solo due opzioni, ad esempio true/false, fare doppio clic sul nome della proprietà da passare tra le opzioni disponibili.  
  
-   Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> è `false`, che indica che il valore è stato modificato, il valore viene visualizzato in grassetto. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> Consente di determinare se il valore può essere reimpostato sul valore originale. Se in tal caso, è possibile modificare il valore predefinito il valore di facendo clic e scegliendo **reimpostare** dal menu visualizzato. In caso contrario, è necessario modificare manualmente il valore sul valore predefinito. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> consente inoltre di localizzare e nascondere i nomi delle proprietà visualizzate in fase di progettazione, ma non influisce sui nomi delle proprietà visualizzati in fase di esecuzione.  
  
-   Fare clic sul pulsante dei puntini di sospensione (…) consente di visualizzare un elenco di valori di proprietà da cui l'utente può selezionare (ad esempio, una selezione colori o un elenco di tipi di carattere). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> Questi valori vengono forniti.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)