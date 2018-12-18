---
title: Algoritmo di Routing di comandi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aba7ddcdda4dd4eabbb9266e0fa89c916bb028f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="command-routing-algorithm"></a>Algoritmo di Routing di comandi
In Visual Studio, i comandi vengono gestiti da un numero dei diversi componenti. Indirizzare i comandi da un contesto più interno, che è basato sulla selezione corrente, per il contesto più esterno (noto anche come globale). Per ulteriori informazioni, vedere [disponibilità](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Ordine di risoluzione di comando  
 I comandi vengono passati attraverso i livelli di contesto del comando seguenti:  
  
1.  Componenti aggiuntivi: L'ambiente offre innanzitutto il comando per tutti i componenti aggiuntivi che sono presenti.  
  
2.  I comandi di priorità: questi comandi vengono registrati tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Essi vengono chiamati per tutti i comandi di Visual Studio e vengono chiamati nell'ordine in cui sono stati registrati.  
  
3.  Comandi del menu contestuale: un comando che si trova in un menu di scelta rapida prima viene offerto alla destinazione di comando che viene fornito per il menu di scelta rapida e dopo che per il routing tipico.  
  
4.  Barra degli strumenti imposta destinazioni comandi: destinazioni questi comandi vengono registrate quando si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. Il `pCmdTarget` parametro può essere `null`. Se non è `null`, questa destinazione del comando viene utilizzato per aggiornare tutti i comandi si trova sulla barra degli strumenti che si sta impostando. Se la shell sta configurando la barra degli strumenti, quindi passa la cornice della finestra come il `pCmdTarget` in modo che tutti gli aggiornamenti per i comandi del flusso della barra degli strumenti tramite la cornice della finestra, anche quando non è attivo.  
  
5.  Finestra degli strumenti: Strumento di windows, in genere implementato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> l'interfaccia, deve inoltre implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia in modo che Visual Studio è possibile ottenere la destinazione del comando quando la finestra degli strumenti è la finestra attiva. Tuttavia, se la finestra degli strumenti con stato attivo si trova il **progetto** finestra, quindi il comando viene indirizzato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia che rappresenta l'elemento padre comune degli elementi selezionati. Se questa selezione si estende su più progetti, il comando viene indirizzato al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> gerarchia. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia contiene i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metodi che sono analoghi ai comandi corrispondenti nel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.  
  
6.  Finestra del documento: Se il comando RouteToDocs flag è impostato nel file vsct, Visual Studio cerca una destinazione del comando sull'oggetto visualizzazione documento, vale a dire un'istanza di un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia o un'istanza di un oggetto documento (in genere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interfaccia o un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface). Se l'oggetto visualizzazione del documento non supporta il comando, Visual Studio indirizza il comando per il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia restituita. (Si tratta di un'interfaccia facoltativa per gli oggetti di dati di documento).  
  
7.  Gerarchia corrente: la gerarchia corrente può essere il progetto a cui appartiene la finestra del documento attivo o la gerarchia selezionata nel **Esplora**. Visual Studio cerca il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia implementata sulla gerarchia attiva o corrente. La gerarchia deve supportare comandi validi quando la gerarchia è attiva, anche se una finestra del documento di un elemento di progetto ha lo stato attivo. Tuttavia, i comandi che si applicano solo quando **Esplora** ha lo stato attivo deve essere supportato tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia e il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>metodi.  
  
     **Taglia**, **copia**, **Incolla**, **eliminare**, **rinominare**, **immettere**e **DoubleClick** comandi richiedono una gestione speciale. Per informazioni su come gestire **eliminare** e **rimuovere** comandi nelle gerarchie, vedere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfaccia.  
  
8.  Globale: Se un comando non è stato gestito nei contesti citati in precedenza, Visual Studio tenta di indirizzare il VSPackage che possiede un comando che implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Se il pacchetto VSPackage non è già stato caricato, non viene caricato quando Visual Studio chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo. Il pacchetto VSPackage viene caricato solo quando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione dei comandi](../../extensibility/internals/command-design.md)