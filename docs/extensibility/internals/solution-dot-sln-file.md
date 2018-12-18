---
title: Soluzione (. File sln) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ad918b72d38e61fb1670adda8ff1f730987c2aa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="solution-sln-file"></a>Soluzione (. File sln)
Una soluzione è una struttura per organizzare i progetti in Visual Studio. La soluzione gestisce le informazioni sullo stato per i progetti in file con estensione sln (basata su testo, condivisa) e i file con estensione suo (opzioni di soluzione binario e specifiche dell'utente). Per ulteriori informazioni sui file con estensione suo, vedere [opzioni utente della soluzione (. File suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Se il pacchetto VSPackage viene caricato in seguito a cui viene fatto riferimento nel file sln, l'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> per leggere il file con estensione sln.  
  
 Il file con estensione sln contiene informazioni basate su testo che nell'ambiente viene utilizzato per individuare e caricare i parametri nome-valore per i dati persistenti e il progetto VSPackage fa riferimento. Quando un utente apre una soluzione, l'ambiente consente di scorrere il `preSolution`, `Project`, e `postSolution` informazioni nel file con estensione sln per caricare la soluzione, progetti all'interno della soluzione e tutte le informazioni persistenti associato alla soluzione.  
  
 Ogni file di progetto contiene informazioni aggiuntive di lettura da parte dell'ambiente per popolare la gerarchia con gli elementi del progetto. La persistenza dei dati di gerarchia è controllata dal progetto. i dati non è in genere archiviati nel file con estensione sln, sebbene sia possibile scrivere informazioni sul progetto nel file con estensione sln intenzionalmente se si sceglie di eseguire questa operazione. Per ulteriori informazioni relative alla persistenza, vedere [persistenza del progetto](../../extensibility/internals/project-persistence.md) e [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Contenuto del File di soluzione  
 Il file con estensione sln è costituito da diverse sezioni come illustrato nel codice seguente.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Per caricare una soluzione, l'ambiente esegue la seguente sequenza di attività.  
  
1.  L'ambiente legge la sezione del file con estensione sln globale ed elabora tutte le sezioni contrassegnate `preSolution`. In questo caso, è un'istruzione di questo tipo:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     Quando l'ambiente legge il `GlobalSection('name')` tag, viene eseguito il mapping il nome di un pacchetto VSPackage usando il Registro di sistema. Il nome della chiave devono essere presenti nel Registro di sistema [HKLM\\< radice del Registro di sistema dell'ID applicazione\>\SolutionPersistence\AggregateGUIDs]. Valore predefinito delle chiavi è il GUID del pacchetto (REG_SZ) del pacchetto VSPackage che ha scritto le voci.  
  
2.  L'ambiente carica il pacchetto VSPackage, chiamate `QueryInterface` nel pacchetto VSPackage per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaccia e chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> (metodo) con i dati nella sezione in modo il pacchetto VSPackage può archiviare i dati. L'ambiente, questo processo viene ripetuto per ogni `preSolution` sezione.  
  
3.  L'ambiente scorre tutti i blocchi di persistenza del progetto. In questo caso, è un progetto.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     L'istruzione contiene il GUID di progetto univoco e il GUID del tipo di progetto. Queste informazioni vengono utilizzate per l'ambiente per trovare i file di progetto o file appartenenti alla soluzione e il pacchetto VSPackage necessari per ogni progetto. Il progetto con GUID viene passato a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> per caricare il pacchetto VSPackage specifico correlato al progetto, quindi il progetto viene caricato dal pacchetto VSPackage. In questo caso, il pacchetto VSPackage che viene caricato per questo progetto è Visual Basic.  
  
     Ogni progetto può rendere persistente un ID istanza univoco del progetto, in modo che siano accessibili in base alle esigenze altri progetti nella soluzione. In teoria, se la soluzione e i progetti sono al controllo del codice sorgente, il percorso del progetto deve essere relativo al percorso per la soluzione. Quando viene caricata inizialmente la soluzione, i file di progetto non possono essere sul computer dell'utente. Se il file di progetto archiviato nel server rispetto al file della soluzione, è relativamente semplice per il file di progetto per trovare e copiato nel computer dell'utente. Viene quindi copiata e carica il resto dei file necessari per il progetto.  
  
4.  In base alle informazioni contenute nella sezione del file con estensione sln di progetto, l'ambiente carica ogni file di progetto. Il progetto è quindi responsabile per la compilazione della gerarchia del progetto e il caricamento di tutti i progetti annidati.  
  
5.  Dopo l'elaborazione di tutte le sezioni del file con estensione sln, la soluzione viene visualizzata in Esplora soluzioni ed è pronta per la modifica dall'utente.  
  
 Se qualsiasi VSPackage che implementa un progetto nella soluzione non viene caricato, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> metodo viene chiamato e ogni altro progetto nella soluzione abbia la possibilità di ignorare le modifiche eventualmente apportate durante il caricamento. Se si verificano errori di analisi, viene mantenuti il maggior numero possibile di informazioni con i file della soluzione e l'ambiente Visualizza una finestra di dialogo che avvisa l'utente che la soluzione è danneggiata.  
  
 Quando la soluzione viene salvata o chiuso, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> metodo viene chiamato e passato alla gerarchia per vedere se sono state apportate modifiche alla soluzione che devono essere immesse nel file con estensione sln. Un valore null, passato per `QuerySaveSolutionProps` in <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, indica che sono permanente le informazioni per la soluzione. Se il valore non è null, le informazioni persistenti sono per un progetto specifico, determinato dal puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia.  
  
 Se sono presenti informazioni da salvare, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaccia viene chiamata con un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> metodo. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> viene quindi chiamato il metodo da parte dell'ambiente per recuperare le coppie nome-valore da `IPropertyBag` l'interfaccia e scrivere le informazioni nel file con estensione sln.  
  
 `SaveSolutionProps`e `WriteSolutionProps` gli oggetti vengono denominati in modo ricorsivo dall'ambiente di recuperare le informazioni viene salvata la `IPropertyBag` interfaccia fino a quando tutte le modifiche sono stati immessi nel file con estensione sln. In questo modo, è possibile garantire che le informazioni vengono rese persistenti con la soluzione e disponibile successiva apertura della soluzione.  
  
 Ogni VSPackage caricato viene enumerata per verificare se dispone di alcuna azione per salvare il file con estensione sln. È solo in fase di caricamento che le chiavi del Registro di sistema sono sottoposti a query. L'ambiente conosce tutti i pacchetti caricati perché sono al momento che la soluzione viene salvata in memoria.  
  
 Solo il file con estensione sln contiene voci di `preSolution` e `postSolution` sezioni. Non simile le sezioni sono nel file con estensione suo poiché la soluzione necessita di queste informazioni per caricare correttamente. Il file con estensione suo contiene opzioni specifiche dell'utente, ad esempio le note private, che non è studiate per essere condivisi o sottoposti a controllo del codice sorgente.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opzioni utente della soluzione (. File suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluzioni](../../extensibility/internals/solutions.md)