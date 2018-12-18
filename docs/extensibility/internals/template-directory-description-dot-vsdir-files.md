---
title: Descrizione del modello Directory (. File VSDIR) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 739dd0d41fb63c4993dad0d66737aaada1cf01c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="template-directory-description-vsdir-files"></a>Descrizione del modello Directory (. File VSDIR)
Un file di descrizione modello directory (VSDIR) è un file di testo che consente l'ambiente di sviluppo integrato (IDE) per visualizzare le cartelle, file VSZ della procedura guidata e i file modello associati al progetto nelle finestre di dialogo. Il contenuto include un record per ogni file o cartella. Tutti i file VSDir in una posizione a cui fa riferimento vengono uniti, anche se i file sola VSDIR generalmente è fornito per descrivere più cartelle, procedure guidate o file di modello.  
  
 Cartelle (le sottodirectory), i file a cui fa riferimento nel file VSDIR e il file VSDIR si trovano nella stessa directory. Quando l'IDE esegue una procedura guidata o Visualizza una cartella o un file di **nuovo progetto** o **Aggiungi nuovo elemento** finestre di dialogo, l'IDE esamina la directory che contiene i file per determinare se un file VSDir è eseguiti presente. Se viene trovato un file VSDIR, l'IDE legge per determinare se contiene una voce del file o cartella visualizzata o eseguita. Se viene individuata una voce, l'IDE Usa le informazioni nella visualizzazione del contenuto o dell'esecuzione della procedura guidata.  
  
 Esempio di codice seguente si trova il file SourceFiles.vsdir nel \<EnvSDK > chiave del Registro di sistema \BscPrj\BscPrj\BscPrjProjectItems\Source_Files:  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 In questo caso, due record sono in un file. Una nuova riga (ritorno a capo) separa ogni record. Ogni riga rappresenta un tipo di file diverso. Una barra verticale (&#124;) separa i campi in ogni record. Una singola directory può contenere più file VSDIR che dispongono di nomi di file diversi oppure è possibile avere un file VSDIR per ogni tipo di file.  
  
## <a name="fields"></a>Campi  
 Nella tabella seguente elenca i campi specificati per ogni record.  
  
|Campo|Descrizione|  
|-----------|-----------------|  
|Nome del percorso relativo (RelPathName)|Il nome del file VSZ, un modello o cartella, ad esempio HeaderFile.h o MyWizard. vsz. Questo campo può anche essere un nome utilizzato per rappresentare una cartella.|  
|{clsidPackage}|Il GUID del pacchetto VSPackage che consente l'accesso alle stringhe localizzate, ad esempio LocalizedName, descrizione, IconResourceId e SuggestedBaseName, in risorse di libreria (DLL) DLL satellite del VSPackage. IconResourceId si applica se DLLPath non viene specificato. **Nota:** questo campo è facoltativo, a meno che uno o più dei campi precedenti è un identificatore di risorsa. Questo campo è in genere vuoto per i file VSDIR corrispondenti alle procedure guidate di terze parti che non localizzare il testo.|  
|LocalizedName|Il nome localizzato del file di modello o della procedura guidata. Questo campo può essere una stringa o un identificatore di risorsa nel formato "#ResID". Questo nome viene visualizzato nel **Aggiungi nuovo elemento** la finestra di dialogo. **Nota:** se LocalizedName è un identificatore di risorsa, sarà necessario {clsidPackage}.|  
|SortPriority|Intero che rappresenta la priorità relativa di questo file modello o una procedura guidata. Ad esempio, se questo elemento ha un valore pari a 1, quindi questo elemento viene visualizzato accanto agli altri elementi con un valore pari a 1 e prima tutti gli elementi con un valore di ordinamento di 2 o superiore.<br /><br /> Priorità di ordinamento è relativo degli elementi nella stessa directory. Possono esistere più di un file VSDIR nella stessa directory. In questo caso, gli elementi da tutti *.* file VSDir in questa directory vengono uniti. Elementi con la stessa priorità vengono elencati in ordine lessicografico tra maiuscole e minuscole del nome visualizzato. Il `_wcsicmp` funzione viene utilizzata per ordinare gli elementi.<br /><br /> Gli elementi non descritti nel file VSDIR includono un numero di priorità maggiore del numero di priorità più alto elencato nel file VSDIR. Il risultato è che questi elementi si trova alla fine dell'elenco visualizzato indipendentemente dal relativo nome.|  
|Descrizione|La descrizione localizzata del file di modello o della procedura guidata. Questo campo può essere una stringa o un identificatore di risorsa nel formato "#ResID". Questa stringa è presente il **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo quando l'elemento è selezionato.|  
|DLLPath o {clsidPackage}|Utilizzato per caricare un'icona per il file di modello o la procedura guidata. L'icona viene caricato come risorsa da un file con estensione dll o .exe utilizzando il valore IconResourceId. Questo file con estensione dll o .exe può essere identificato tramite un percorso completo o mediante un GUID di un VSPackage. La DLL del pacchetto VSPackage di implementazione viene utilizzata per caricare l'icona (non la DLL satellite).|  
|IconResourceId|Identificatore della risorsa nell'implementazione di VSPackage o DLL DLL che determina l'icona da visualizzare.|  
|Flag (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)|Utilizzato per abilitare o disabilitare il **nome** e **percorso** campi di **Aggiungi nuovo elemento** la finestra di dialogo. Il valore di **flag** campo è l'equivalente decimale della combinazione di flag di bit richiesto.<br /><br /> Quando un utente seleziona un elemento nel **New** scheda, il progetto determina se il campo nome e il campo percorso vengono visualizzati quando il **Aggiungi nuovo elemento** finestra di dialogo viene visualizzata. Un elemento, tramite un file VSDIR, può controllare solo se i campi sono abilitati e disabilitati quando l'elemento è selezionato.|  
|SuggestedBaseName|Rappresenta il nome predefinito per il file, una procedura guidata o un modello. Questo campo è una stringa o un identificatore di risorsa nel formato "#ResID". L'IDE Usa questo valore per fornire un nome predefinito per l'elemento. Questo valore di base viene aggiunto con un valore integer per specificare un nome univoco, ad esempio MyFile21.asp.<br /><br /> Nell'elenco precedente, descrizione, DLLPath, IconResourceId, flag e SuggestedBaseNumber si applicano solo ai file di modello e procedura guidata. Questi campi non si applicano alle cartelle. Ciò è illustrato nel codice nel file BscPrjProjectItems il \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems chiave di registro di sistema. Questo file contiene tre record (uno per ogni cartella) con quattro campi per ogni record: RelPathName, {clsidPackage}, LocalizedName e SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 Quando si crea un file, è necessario anche considerare il seguente.  
  
-   Qualsiasi campo non obbligatori per il quale non sono presenti dati significativi deve contenere il valore 0 (zero) come segnaposto.  
  
-   Se non viene fornito alcun nome localizzato, viene utilizzato il nome di percorso relativo del file della procedura guidata.  
  
-   Esegue l'override DLLPath clsidPackage per le icone.  
  
-   Se è definita alcuna icona, l'IDE sostituisce l'icona predefinita per un file con estensione.  
  
-   Se non viene fornito alcun nome di base, verrà utilizzato 'Project'.  
  
-   Se si elimina il file VSZ, cartelle o file di modello, è necessario rimuovere anche i record associati nel file VSDIR.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)