---
title: "Pulsanti della finestra proprietà | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 950b9f0a7b0f38689042877a42499e23253e6486
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-buttons"></a>Pulsanti della finestra proprietà
A seconda del linguaggio di sviluppo e il tipo di prodotto, alcuni pulsanti vengono visualizzati per impostazione predefinita sulla barra degli strumenti per la **proprietà** finestra. In tutti i casi, il **categoria**, **Alphabetized**, **proprietà**, e **pagine delle proprietà** pulsanti vengono visualizzati. In Visual c# e Visual Basic, il **eventi** pulsante viene visualizzato anche. In alcuni progetti Visual C++, il **VC + + messaggi** e **esegue l'override di VC** pulsanti vengono visualizzati. Pulsanti aggiuntivi potrebbero essere visualizzati per altri tipi di progetto. Per ulteriori informazioni sui pulsanti di **proprietà** finestra, vedere [finestra proprietà](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementazione di pulsanti della finestra proprietà  
 Quando si fa clic il **categoria** pulsante, le chiamate di Visual Studio il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interfaccia sull'oggetto che ha lo stato attivo per ordinare le proprietà per categoria. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>viene implementato il `IDispatch` oggetto che viene visualizzato il **proprietà** finestra.  
  
 Sono disponibili 11 categorie di proprietà predefiniti, che hanno valori negativi. È possibile definire categorie personalizzate, ma è consigliabile assegnare loro valori positivi per distinguerli dalle categorie predefinite.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> metodo restituisce il valore della categoria di proprietà appropriata per la proprietà specificata. Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> metodo restituisce una stringa che contiene il nome della categoria. È sufficiente fornire supporto per i valori di categoria personalizzate, poiché Visual Studio riconosce i valori di categoria di proprietà standard.  
  
 Quando si sceglie il **Alphabetized** pulsante, le proprietà vengono visualizzate in ordine alfabetico in base al nome. I nomi vengono recuperati da `IDispatch` in base a un algoritmo di ordinamento localizzato.  
  
 Quando il **proprietà** finestra è aperta, il **proprietà** pulsante viene automaticamente visualizzato come selezionato. In altre parti dell'ambiente, viene visualizzato lo stesso pulsante e sarà possibile selezionarla per mostrare il **proprietà** finestra.  
  
 Il **pagine delle proprietà** pulsante non è disponibile se `ISpecifyPropertyPages` non è implementata per l'oggetto selezionato. Le proprietà dipendenti dalla configurazione di visualizzazione che sono in genere associate a soluzioni, progetti e pagine delle proprietà, ma possono essere anche essere associate agli elementi di progetto (ad esempio, in Visual C++).  
  
> [!NOTE]
>  Non è possibile aggiungere i pulsanti della barra degli strumenti per la **proprietà** finestra usando il codice non gestito. Per aggiungere un pulsante della barra degli strumenti, è necessario creare un oggetto gestito che deriva da <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)