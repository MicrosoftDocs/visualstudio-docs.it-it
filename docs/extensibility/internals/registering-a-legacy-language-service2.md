---
title: Registrazione di un Service2 Language Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 364b17e6759d0ca337b69c89c51dfba8d26f3e32
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-legacy-language-service"></a>Registrazione di un servizio di linguaggio Legacy
Le sezioni seguenti forniscono elenchi di voci del Registro di sistema per la lingua di varie opzioni di servizio disponibile in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Nel seguente elenco di voci del Registro di sistema, *VS Reg radice* è uguale a HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, dove *x. y* è la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numero di versione.  
  
## <a name="registry-entries-for-language-service-options"></a>Voci del Registro di sistema per le opzioni di servizio di linguaggio  
 Il *VS Reg radice*\Languages\Language servizi\\*nome di lingua* chiave può contenere i valori seguenti.  
  
|nome|Tipo|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|*\<GUID >*|GUID del servizio di linguaggio.|  
|LangResID|REG_DWORD|0x0-0xffff|Identificatore di risorsa (ResID) per il nome di testo localizzato del linguaggio della stringa.|  
|Pacchetto|REG_SZ|*\<GUID >*|GUID del pacchetto VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Specifica se il **il completamento delle istruzioni** opzioni il **opzioni** la finestra di dialogo sono abilitati.|  
|ShowSmartIndent|REG_DWORD|0-1|Specifica se l'opzione per selezionare **Smart** rientri nel **opzioni** è attivata la finestra di dialogo.|  
|RequestStockColors|REG_DWORD|0-1|Specifica se personalizzato o vengono utilizzati i colori predefiniti per le parole chiave di colore.|  
|ShowHotURLs|REG_DWORD|0-1|Specifica se l'utente può fare clic su URL.|  
|Per impostazione predefinita gli URL Non attivi|REG_DWORD|0-1|Specifica l'impostazione iniziale per il **Consenti navigazione URL con clic singolo** opzione il **opzioni** la finestra di dialogo.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Specifica se il servizio di linguaggio ha "Inserisci spazi" come l'opzione di scheda predefinita.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Abilita o disabilita il **barra di spostamento** opzione il **opzioni** la finestra di dialogo che mostra o nasconde il **barra di spostamento**.|  
|Solo finestra codice singolo|REG_DWORD|0-1|Abilita o disabilita il **nuova finestra** scelte nel **finestra** menu per un servizio di linguaggio.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Abilita o disabilita un **opzioni** impostazione della finestra di dialogo per **Nascondi membri avanzati**.|  
|Supporto CF_HTML|REG_DWORD|0-1|Specifica se l'editor consente la copia e Incolla di dati HTML.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Specifica se il **i numeri di riga** opzioni il **opzioni** la finestra di dialogo è abilitata per un servizio di linguaggio.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Specifica se i membri avanzati, ad esempio campi privati sono nascosti negli elenchi di completamento.|  
|ShowBraceCompletion|REG_DWORD|0-1|Specifica se il **tra parentesi graffe completamento** opzione il **opzioni** è attivata la finestra di dialogo.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## <a name="registry-entries-for-debugger-languages-options"></a>Voci del Registro di sistema per le opzioni di lingue del Debugger  
 Il *VS Reg radice*\Languages\Language servizi\\*nome di lingua*\Debugger lingue\\*GUID*\ chiave può includere le operazioni seguenti valori.  
  
|nome|Tipo|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|ASCII|Il valore predefinito può essere utilizzato per documentare il nome della lingua. Il nome di questa chiave è un GUID di un analizzatore di espressioni che ha una voce corrispondente in  *\<VS Reg radice >*\AD7Metrics\Expression dell'analizzatore di espressioni.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>Voci del Registro di sistema per le opzioni di strumenti dell'Editor  
 È possibile aggiungere le chiavi del Registro di sistema nella chiave EditorToolsOptions per le pagine delle proprietà e i nodi di proprietà. Queste chiavi e i relativi valori identificano pagine delle proprietà nel **opzioni** la finestra di dialogo (nel **strumenti** menu) che consentono di configurare il servizio di linguaggio. Nell'esempio seguente, *nome pagina* è il nome di una pagina delle proprietà, e *nome del nodo* è il nome di un nodo nell'albero di **opzioni** la finestra di dialogo. La voce di pagina e la voce del nodo devono essere specificati separatamente.  
  
|nome|Tipo|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|resID|Il nome visualizzato localizzato di questa pagina di opzioni. Il nome può essere testo letterale o #`nnn`, dove `nnn` è un ID di risorsa stringa nella DLL del pacchetto VSPackage specificato satellite.|  
|Pacchetto|REG_SZ|*GUID*|Il GUID del pacchetto VSPackage che implementa questa pagina di opzioni.|  
|Pagina|REG_SZ|*GUID*|Il GUID della pagina delle proprietà per richiedere il pacchetto VSPackage chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo. Se questa voce del Registro di sistema non è presente, la chiave del Registro di sistema viene descritto un nodo, non è una pagina.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## <a name="registry-entries-for-file-name-extension-options"></a>Voci del Registro di sistema per le opzioni di estensione nome File  
 La voce per l'estensione del file deve includere il punto iniziale, ad esempio ".myext".  
  
|nome|Tipo|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|*GUID*|GUID del servizio per il servizio di linguaggio predefinito per questo tipo di estensione del nome file.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Voci del Registro di sistema per le opzioni Editor  
 Il *VS Reg radice*chiave \Editors può contenere i seguenti valori:  
  
|nome|Tipo|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|""|Inutilizzato; è possibile inserire il nome per la documentazione.|  
|DefaultToolboxTab|REG_SZ|""|Nome della scheda della casella degli strumenti per impostare come predefinito quando l'editor è attivo.|  
|DisplayName|REG_SZ|resID|Nome da visualizzare nel **Apri con** la finestra di dialogo. Il nome è un nome o l'ID della risorsa stringa in formato standard.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Utilizzato per il **Apri con** comando di menu. Se si desidera elencare l'editor di testo predefinito nell'elenco degli editor disponibili per un tipo di file specifico, impostare questo valore su 1.|  
|LinkedEditorGUID|REG_SZ|*\<GUID >*|Utilizzato per qualsiasi servizio di linguaggio che è possibile aprire un file con il supporto di tabella codici. Ad esempio, quando si apre un file con estensione txt utilizzando il **Apri con** comando, sono disponibili le opzioni per l'utilizzo di editor del codice sorgente con e senza codifica.<br /><br /> Il GUID specificato nel nome della sottochiave è per factory editor tabella codici. il GUID collegato specificato in questa voce del Registro di sistema è per la factory editor regolari. Lo scopo di questa voce è che se l'IDE non si apre un file utilizzando l'editor predefinito, l'IDE tenterà di utilizzare l'editor successiva nell'elenco. Questo editor successivo non deve essere la factory editor tabella codici perché questa factory editor è fondamentalmente lo stesso come il factory editor che non è riuscita.|  
|Pacchetto|REG_SZ|*\<GUID >*|GUID VSPackage ResID del nome visualizzato.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## <a name="registry-entries-for-logical-view-options"></a>Voci del Registro di sistema per le opzioni di visualizzazione logica  
 Il *VS Reg radice*\Editors\\*GUI Editor >*chiave \LogicalViews può contenere i valori seguenti.  
  
|nome|Tipo|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ||Non usato.|  
|*\<GUID >*|REG_SZ|""|Chiave per la logiche visualizzazioni supportate. Può avere come molti di questi, in base alle esigenze. Il nome della voce del Registro di sistema è importante, non il valore, è sempre una stringa vuota.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## <a name="registry-entries-for-editor-extension-options"></a>Voci del Registro di sistema per le opzioni di estensione dell'Editor  
 Il *VS Reg radice*\Editors\\*Editor GUID*chiave \Extensions può contenere i valori seguenti. L'estensione del nome file non include il punto iniziale.  
  
|nome|Tipo|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ||Non usato.|  
|*\<ext >*|REG_DWORD|0-0xffffffff.|Priorità relativa delle estensioni. Se due o più lingue condividono la stessa estensione, viene scelto il linguaggio di priorità più alta.|  
  
 Inoltre, selezione predefinita dell'utente corrente per un editor viene archiviata in HKEY_Current_User\Software\Microsoft\VisualStudio\\*x. y*\Default editor\\*ext*. Il GUID del servizio di linguaggio selezionato è nella voce personalizzata. Questo ha la precedenza per l'utente corrente.  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Voci del Registro di sistema per le opzioni del servizio di lingue Framework di pacchetto gestito  
 Le voci del Registro di sistema seguenti sono specifiche per le classi del servizio pacchetto gestito (MPF) framework language. Queste voci del Registro di sistema indicano il supporto del servizio di linguaggio per diverse funzionalità di IntelliSense e per altri avanzate funzionalità di modifica.  
  
 Queste voci del Registro di sistema sono accessibili attraverso la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
|nome|Tipo|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Supporto per le operazioni di IntelliSense.|  
|MatchBraces|REG_DWORD|0-1|Supporto per la corrispondenza di coppie di linguaggio, ad esempio parentesi, parentesi e parentesi quadre.|  
|Informazioni rapide|REG_DWORD|0-1|Supporto per l'operazione di informazioni rapide di IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0-1|Supporto per la visualizzazione la coppia di lingue corrispondenti nella barra di stato.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Supporto per la visualizzazione delle coppie corrispondenti di lingua, in genere tramite evidenziando i due elementi.|  
|MaxErrorMessages|REG_DWORD|0-n|Il numero massimo di errori che possono essere visualizzati nel **elenco errori** finestra.|  
|CodeSenseDelay|REG_DWORD|0-n|Il numero di millisecondi di ritardo prima dell'avvio in background durante l'analisi per un'operazione di IntelliSense.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Supporto per l'analisi in background.|  
|EnableCommenting|REG_DWORD|0-1|Il supporto per i blocchi di testo selezionati come commento e implica inoltre supporto per la rimozione dei commenti sul testo selezionato.|  
|EnableFormatSelection|REG_DWORD|0-1|Supporto per la formattazione del testo, ad esempio il rientro di auto o regolare la posizione delle parentesi graffe.|  
|AutoOutlining|REG_DWORD|0-1|Supporto per la struttura (aree che possono essere compressi).|  
|MaxRegions|REG_DWORD|0-n|Il numero massimo di aree nascoste per ogni file.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)