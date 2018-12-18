---
title: I flag della riga di comando del compilatore VSCT | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d33c0e1bc54ee0c1abab736ba24ce76fbf710fdc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vsct-compiler-command-line-flags"></a>Flag della riga di comando del compilatore VSCT
Il compilatore di Visual Studio comando tabella (VSCT) fornisce le opzioni della riga di comando per assicurarsi la compilazione corretta del file con estensione vsct.  
  
## <a name="command-line-parameters"></a>Parametri della riga di comando  
 Per visualizzare informazioni di base VSCT da un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **comando** finestra, passare il *il percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ cartella e il tipo:  
  
```  
vsct /?  
```  
  
 Restituisce:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  I caratteri - (trattino) e / (barra) sono entrambi notazione accettati per indicare i parametri della riga di comando.  
  
 Di seguito sono riportati i flag accettabile e il relativo significato.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|-D|Specificare eventuali ulteriori simboli definiti.|  
|-I|Indicare che percorsi che devono essere utilizzati per la risoluzione dei riferimenti a file di inclusione aggiuntiva.|  
|-L|Specificare il <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura, ad esempio "en-US".|  
|-E|Creare oggetti c# nello spazio dei nomi specificato per gli elementi di comando, seguito da [C &#124; E &#124; N]:*filename*dove C = c#, H = intestazione di C++, N = dello spazio dei nomi. Lo spazio dei nomi è obbligatorio per c#.|  
|-v|Output dettagliato.|  
  
 L'opzione -L indica al compilatore di selezionare un gruppo di stringhe per generare il file CTO binario corrispondente per il determinato <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura. Il nome di impostazioni cultura specificate debba corrispondere all'attributo di linguaggio di uno o più [elemento stringhe](../../extensibility/strings-element.md) nel file vsct. Se un elemento stringhe non dispone di alcun attributo di linguaggio, è ereditato dal contenitore [CommandTable elemento](../../extensibility/commandtable-element.md).  
  
 Un file con estensione vsct può disporre di più elementi di stringhe e può disporre di un altro attributo di linguaggio. Globalizzazione si ottiene eseguendo il compilatore VSCT più volte e modificando l'opzione -L per ogni nome di impostazioni cultura.  
  
 Se il nome delle impostazioni cultura specificato dall'opzione -L non corrisponde all'attributo di linguaggio di qualsiasi elemento di stringhe, il compilatore tenterà in modo che corrisponda alla lingua e non l'area. Ad esempio, se non viene trovato "en-US", il compilatore tenterà "en" invece. In caso contrario, verrà effettuato un tentativo di impostazioni cultura correnti del sistema operativo. In caso contrario, esegue la compilazione trova il primo elemento di stringhe.  
  
 L'opzione -E consente di generare un file di intestazione di tipo C che contiene i simboli utilizzati per la tabella di comando o per generare un file c# che contiene gli oggetti per i simboli di comando.  
  
 -D e - I commutatori di avere la sintassi dei flag per il preprocessore C Cl.exe che hanno lo stesso nome. -D definizioni che hanno il formato X = Y sono utilizzate per l'espansione di basato su XML \<definiti > test in `Condition` attributi. -I percorsi di inclusione vengono utilizzati per risolvere \<inclusione >, \<Extern > e \<Bitmap > i riferimenti di file. Per ulteriori informazioni, vedere il [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
 Il compilatore VSCT possibile decompilare anche un file binario compilato in precedenza. A tale scopo, specificare un file binario per il \<infile >.   Se il file binario è stato generato dal compilatore VSCT, avranno i simboli già incorporati e viene prodotto un output con i nomi simbolici in una \<simboli > della sezione dell'output. Se il file binario è stato generato dal compilatore CTC, l'output conterrà i GUID e ID effettivo. Se il file *.ctsym derivante da versioni correnti di Ctc.exe è nella stessa cartella del file di input binario, i simboli verranno caricati da tale file e usati per l'output.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)