---
title: Configurazione per l'Output del progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f3927ac9aa9e85be026d2b9a2af1c0c4d956c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-output"></a>Configurazione per l'Output del progetto
Ogni configurazione è in grado di supportare un set di processi di compilazione che generano elementi di output, ad esempio il file eseguibile o una risorsa. Questi elementi di output sono privati per l'utente e possono essere inseriti in gruppi che si collegano i tipi correlati di output, ad esempio i file eseguibili (.exe, DLL,. lib) e file di origine (con estensione idl, file con estensione h).  
  
 Gli elementi di output possono essere resi disponibili tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metodi ed enumerato con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metodi. Quando si desidera raggruppare gli elementi di output, il progetto deve inoltre implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfaccia.  
  
 Il costrutto sviluppato implementando `IVsOutputGroup` consente ai progetti di gruppo di output in base all'utilizzo. Ad esempio, una DLL potrebbe essere raggruppata con il database di programma (PDB).  
  
> [!NOTE]
>  Un file PDB contiene informazioni di debug e viene creato quando l'opzione 'Genera informazioni di Debug' è specificato quando si compila il file DLL o .exe. Il file con estensione PDB viene in genere generato Debug progetto solo per la configurazione.  
  
 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione supportata, anche se il numero di output contenuti all'interno di un gruppo può variare da una configurazione alla configurazione. Ad esempio, Matt del progetto DLL potrebbe includere mattd.dll e mattd.pdb nella configurazione Debug, ma solo matt.dll nella configurazione delle vendite al dettaglio.  
  
 I gruppi dispongono anche le informazioni sull'identificatore stesso, ad esempio il nome canonico, nome visualizzato e informazioni di gruppo, dalla configurazione alla configurazione all'interno di un progetto. La coerenza consente e distribuzione dei pacchetti per continuare a funzionare anche se modificare le configurazioni.  
  
 I gruppi possono anche presentare un output chiave che consente di scelta rapida creazione di pacchetti in modo che punti a un nome significativo. Qualsiasi gruppo potrebbe essere vuoto in una determinata configurazione, pertanto non devono essere rese presupposti sulle dimensioni di un gruppo. Le dimensioni (numero di output) di ogni gruppo in una configurazione possono essere diversa dalla dimensione di un altro gruppo nella stessa configurazione. Può anche essere diversa dalla dimensione dello stesso gruppo in un'altra configurazione.  
  
 ![Rappresentazione grafica dei gruppi di output](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Gruppi di output  
  
 L'utilizzo principale del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfaccia è quello di fornire l'accesso per la compilazione, distribuzione e il debug di oggetti di gestione e consentire la libertà di output gruppo di progetti. Per ulteriori informazioni sull'utilizzo di questa interfaccia, vedere [oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md).  
  
 Nel diagramma precedente, gruppo incorporato dispone di una chiave di output in configurazioni (bD.exe o b.exe), pertanto l'utente può creare un collegamento a predefiniti e sapere che il collegamento funzionerà indipendentemente dalla configurazione distribuita. Origine del gruppo non dispone di una chiave di output, pertanto l'utente non è possibile creare un collegamento ad esso. Se il gruppo di eseguire il Debug compilata include un output chiave, ma il gruppo delle vendite al dettaglio compilato non, sarebbe un'implementazione non corretta. Di conseguenza, quindi, se qualsiasi configurazione dispone di un gruppo che non contiene nessun output, e, di conseguenza, nessun file di chiave, altre configurazioni che contengono l'output con tale gruppo non possono avere file di chiave. Gli editor di programma di installazione si presuppongono che nomi canonici e nomi visualizzati dei gruppi, nonché l'esistenza di un file di chiave, non verrà modificato in configurazioni di base.  
  
 Si noti che se un progetto ha un `IVsOutputGroup` che non desidera pacchetti o la distribuzione, è sufficiente per non inserire l'output in un gruppo. L'output può comunque essere enumerato in genere mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metodo che restituisce tutti gli output di una configurazione indipendentemente dal raggruppamento.  
  
 Per ulteriori informazioni, vedere l'implementazione di `IVsOutputGroup` nell'esempio di progetto personalizzato in [MPF per i progetti](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md)   
 [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)