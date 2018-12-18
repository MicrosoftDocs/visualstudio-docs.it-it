---
title: IDiaSymbol | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a456abd2d3d80a122d4182ae882ca28b07788596
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbol"></a>IDiaSymbol
Vengono descritte le proprietà di un'istanza del simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaSymbol : IUnknown  
```  
  
## <a name="methods-in-alphabetical-order"></a>Metodi nell'ordine alfabetico  
 Nella tabella seguente sono illustrati i metodi di `IDiaSymbol`.  
  
> [!NOTE]
>  Simboli restituirà dati significativi solo per alcuni di questi metodi, a seconda del tipo di simbolo. Se restituisce un metodo `S_OK`, quindi tale metodo ha restituito dati significativi.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Recupera tutti gli elementi figlio del simbolo.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Recupera gli elementi figlio del simbolo. Questo metodo è la versione estesa del [idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Recupera gli elementi figlio del simbolo sono validi su un indirizzo specificato.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Recupera gli elementi figlio del simbolo sono validi in un indirizzo virtuale relativo specificato (RVA).|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Recupera gli elementi figlio del simbolo valide in un indirizzo virtuale specificato.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un determinato indirizzo.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un indirizzo virtuale relativo specificato (RVA).|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un indirizzo virtuale specificato (VA).|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni di numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, in questo simbolo.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni sul numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, in questo simbolo all'interno dell'intervallo di indirizzi specificato.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni sul numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, in questo simbolo all'interno dell'indirizzo virtuale relativo specificato (RVA).|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Recupera un'enumerazione che consente a un client scorrere le informazioni sul numeri di riga di tutte le funzioni che vengono impostati come inline, direttamente o indirettamente, in questo simbolo all'interno dell'indirizzo virtuale specificato (VA).|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Dato un valore di tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in questa funzione stub in un indirizzo virtuale relativo specificato.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Restituisce il numero di tag puntatore tasti di scelta rapida in una funzione di C++ AMP stub.|  
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Restituisce tutti i valori tag puntatore tasti di scelta rapida che corrispondono a una funzione di stub di C++ AMP tasti di scelta rapida.|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Recupera il modificatore di accesso di un membro di classe.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Recupera la parte offset di un percorso di indirizzo.|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Recupera la parte della sezione di un percorso di indirizzo.|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Recupera un flag che indica se un altro simbolo fa riferimento a questo indirizzo.|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Recupera il valore di durata di un database di programma.|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Recupera l'identificatore di simbolo del tipo di indice di matrice.|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Recupera l'identificatore di tipo di indice di matrice del simbolo.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Recupera il numero di versione principale di back-end.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Recupera il numero di versione secondaria di back-end.|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Recupera il numero di build di back-end.|  
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Recupera l'offset di dati di base.|  
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Recupera lo slot di dati di base.|  
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Recupera il simbolo da cui è basato il puntatore del mouse.|  
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Recupera l'ID di simbolo da cui è basato il puntatore del mouse.|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Recupera il tag del tipo di un tipo semplice.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Recupera la posizione del bit di un percorso.|  
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Recupera un tipo incorporato del tipo HLSL.|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Restituisce un indicatore di convenzione di chiamata del metodo.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Recupera un riferimento all'elemento padre di classe del simbolo.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Recupera l'identificatore di classe padre del simbolo.|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Recupera un flag che indica se il simbolo fa riferimento a un indirizzo di codice.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Recupera un flag che indica se il simbolo è stato generato dal compilatore.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Recupera il nome del compilatore usato per creare il [compilando](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Recupera un flag che indica se il tipo di dati definito dall'utente ha un costruttore.|  
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Recupera il contenente il simbolo di questo simbolo.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è costante.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Recupera il numero di elementi di una matrice o elenco.|  
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Recupera il numero di intervalli di indirizzi valido associato al simbolo locale.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Recupera un flag che indica se la funzione utilizza una convenzione di chiamata personalizzata.|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Recupera i byte di dati di un simbolo OEM.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Recupera la classificazione di variabili di un simbolo di dati.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Recupera il flag che descrivono le funzionalità di modifica e continuazione del programma compilato o unità.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Recupera un flag che indica se la funzione utilizza una misura restituito.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Recupera il numero di versione principale front-end.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Recupera il numero di versione secondaria front-end.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Recupera il numero di build front-end.|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Recupera un flag che indica se il simbolo pubblico fa riferimento a una funzione.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Recupera il GUID del simbolo.|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Recupera un flag che indica se la funzione contiene una chiamata a `alloca`.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Recupera un flag che indica se il tipo di dati definito dall'utente ha tutti gli operatori di assegnazione definiti.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è definiti tutti gli operatori di cast.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Recupera un flag che indica se il modulo contiene le informazioni di debug.|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Recupera un flag che indica se la funzione dispone di un gestore di eccezioni di tipo C++.|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Recupera un flag che indica se la funzione dispone di un gestore di eccezioni asincrone.|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Recupera un flag che indica se la funzione dispone di assembly inline.|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Recupera un flag che indica se la funzione contiene un comando longjmp (parte di gestione delle eccezioni di tipo C).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Recupera un flag che indica se il modulo contiene il codice gestito.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Recupera un flag che indica se il tipo di dati definito dall'utente include nidificati, definizioni dei tipi.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Recupera un flag che indica se la funzione o un modulo è compilati in controlli di sicurezza (tramite il [/GS (controllo sicurezza Buffer)](/cpp/build/reference/gs-buffer-security-check) opzione del compilatore).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Recupera un flag che indica se la funzione è di tipo Win32 Structured Exception Handling.|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Recupera un flag che indica se la funzione contiene un comando setjmp.|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è una classe base virtuale indiretta.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Recupera un flag che indica se la funzione è stata contrassegnata con l'attributo inline.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Recupera un flag che indica se la funzione dispone di un restituito dall'istruzione di interrupt.|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Recupera un flag che indica se la funzione è la classe base virtuale.|  
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Recupera un flag che indica se il simbolo corrisponde a una variabile locale condivisa gruppo nel codice compilato per un tasto di scelta rapida di C++ AMP.|  
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Recupera un flag che indica se il simbolo corrisponde alla *simbolo intervallo definizione* per il componente di tag di una variabile puntatore nel codice compilato per un tasto di scelta rapida di C++ AMP. Il simbolo di intervallo di definizione è il percorso di una variabile per un intervallo di indirizzi.|  
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Indica se il simbolo corrisponde a un simbolo di funzione di primo livello per uno shader compilato per una scelta rapida che corrisponde a un `parallel_for_each` chiamare.|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Recupera un flag che indica se i dati fanno parte di un'aggregazione di più simboli.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Recupera un flag che indica se il file di simboli contiene tipi C.|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Recupera un flag che indica se il modulo è stato convertito da Common Intermediate Language (CIL) al codice nativo.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Recupera un flag che indica se gli elementi di un tipo di dati definito dall'utente sono allineati a un limite specifico.|  
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Specifica se questo simbolo rappresenta dati di alto livello dello Shader Language (HLSL).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Recupera un flag che indica se il modulo è stato compilato con la [/hotpatch (Crea immagine di patch a caldo)](/cpp/build/reference/hotpatch-create-hotpatchable-image) opzione del compilatore.|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Recupera un flag che indica se il modulo gestito è stato collegato con /LTCG l'opzione del linker.|  
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Specifica se la matrice è riga principale.|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Recupera un flag che indica se il modulo gestito è un file netmodule (contenente solo i metadati).|  
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Specifica se il `this` puntatore punta a un membro dati con ereditarietà multipla.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Recupera un flag che indica se la funzione ha il [naked](/cpp/cpp/naked-cpp) attributo.|  
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Specifica se la variabile è ottimizzata.|  
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Specifica se il `this` puntatore si basa su un valore di simbolo.|  
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Specifica se questo simbolo è un puntatore a un membro dati.|  
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Specifica se questo simbolo è un puntatore a una funzione membro.|  
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Specifica se la variabile contiene un valore restituito.|  
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Specifica se il modulo compilato con l'opzione /SDL.|  
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Specifica se il `this` puntatore punta a un membro dati con ereditarietà singola.|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Recupera un flag che indica se i dati sono stata suddivisa in un'aggregazione di separare i simboli.|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Recupera un flag che indica se un livello di funzione o thunk è statico.|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Recupera un flag che indica se i simboli privati sono state rimosse dal file di simboli.|  
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Specifica se il `this` puntatore punta a un membro dati con ereditarietà virtuale.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Recupera la lingua dell'origine.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Recupera il numero di byte di memoria utilizzata dall'oggetto rappresentato da questo simbolo.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Recupera un riferimento all'elemento padre lessicale del simbolo.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Recupera l'identificatore padre lessicale del simbolo.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Recupera il nome del file del file di libreria o oggetto da cui è stato caricato l'oggetto.|  
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Restituisce la lunghezza dell'intervallo di indirizzi in cui il simbolo locale è valido.|  
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Restituisce la parte della sezione dell'intervallo di indirizzi iniziale in cui il simbolo locale è valido.|  
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Restituisce la parte offset dell'intervallo di indirizzi iniziale in cui il simbolo locale è valido.|  
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Restituisce l'inizio dell'intervallo di indirizzi in cui il simbolo locale è valido.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Recupera il tipo di posizione di un simbolo di dati.|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Recupera il limite inferiore di una dimensione di matrice FORTRAN.|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Recupera l'identificatore di simbolo del limite inferiore della finestra di una dimensione di matrice FORTRAN.|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Recupera il tipo di CPU di destinazione.|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Recupera un flag che che indica se il simbolo fa riferimento a codice gestito.|  
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Recupera il tipo di spazio di memoria.|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Recupera un flag che indica se il simbolo fa riferimento al codice Microsoft Intermediate Language (MSIL).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Recupera il nome del simbolo.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è nidificato.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Recupera un flag che indica se la funzione è contrassegnata con il [noinline](/cpp/cpp/noinline) attributo.|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Recupera un flag che indica se la funzione è stata dichiarata con la [noreturn](/cpp/cpp/noreturn) attributo.|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Recupera un flag che indica se nessun ordinamento stack poteva essere eseguito come parte del controllo del buffer dello stack.|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Recupera un flag che indica se la funzione o l'etichetta non viene mai raggiunto.|  
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Restituisce il numero di tag puntatore tasti di scelta rapida in una funzione di C++ AMP stub.|  
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Recupera il numero di modificatori che vengono applicati al tipo originale.|  
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Recupera il numero di indici di registro.|  
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Recupera il numero di righe nella matrice.|  
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Recupera il numero di colonne nella matrice.|  
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Recupera il nome del file oggetto.|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Recupera il tipo del puntatore a oggetto per un metodo della classe.|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Recupera il simbolo `oemId` valore.|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Recupera il simbolo `oemSymbolId` valore.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Recupera l'offset della posizione simbolo.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Recupera un flag che indica se la funzione o l'etichetta contiene codice ottimizzato anche come informazioni di debug.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Recupera un flag che indica se il tipo di dati definito dall'utente con gli operatori di overload.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Recupera un flag che indica se il tipo di dati definito dall'utente verrà compressi.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Recupera il tipo di piattaforma per cui è stato compilato il programma o modulo.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Recupera un flag che indica se la funzione è pura virtuale.|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Recupera il numero di dimensioni di una matrice multidimensionale di FORTRAN.|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Recupera un flag che indica se un tipo di puntatore è un riferimento.|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Recupera l'identificatore di registro del percorso.|  
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Recupera il tipo di registro.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Recupera l'indirizzo virtuale relativo (RVA) della posizione.|  
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Specifica se il `this` puntatore risulta limitato.|  
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Recupera lo slot campionatore.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Recupera un flag che indica se il tipo di dati definito dall'utente viene visualizzato in un ambito lessicale non globali.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Recupera il valore di firma del simbolo.|  
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Recupera le dimensioni di un membro di un tipo definito dall'utente.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Recupera il numero di slot della posizione.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Recupera il nome del file del file di origine.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Recupera il numero della riga e file di origine che indicano in cui è definito un tipo definito dall'utente specificato.|  
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Recupera lo stride di matrice o matrice non sequenziale.|  
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Recupera il tipo sub.|  
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Recupera l'ID di tipo sub.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Recupera il nome del file da cui sono stati caricati i simboli.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Recupera l'identificatore univoco di simbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Recupera il classificatore di tipo di simbolo.|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Recupera la sezione di offset di una destinazione thunk.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Recupera l'indirizzo virtuale relativo (RVA) di una destinazione thunk.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Recupera una sezione dell'indirizzo di una destinazione thunk.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Recupera l'indirizzo virtuale (VA) di una destinazione thunk.|  
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Recupera lo slot della trama.|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Recupera l'operatore logico `this` DS per il metodo.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Recupera il tipo di thunk di una funzione.|  
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Recupera il timestamp del file eseguibile sottostante.|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Recupera il token di metadati di una funzione gestita o una variabile.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Recupera un riferimento alla firma della funzione.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Recupera l'identificatore del tipo del simbolo.|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Recupera una matrice di valori di tipo specifici del compilatore per questo simbolo.|  
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Recupera una matrice di valori di identificatore di tipo specifici del compilatore per questo simbolo.|  
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Recupera lo slot uav.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Recupera la varietà di un tipo definito dall'utente (UDT).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Recupera un flag che indica se il tipo di dati definito dall'utente non è allineato.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Recupera il nome non decorato di C++ decorato, o un collegamento, un nome.|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|Estensione di `get_undecoratedName` metodo che recupera il nome non decorato in base al valore di un campo di estensione.|  
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Recupera l'ID del tipo originale (non modificato).|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Recupera il limite superiore di una dimensione di matrice FORTRAN.|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Recupera l'identificatore di simbolo il limite superiore di una dimensione di matrice FORTRAN.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Recupera il valore di una costante.|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Recupera un flag che indica se la funzione è virtuale.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Recupera l'indirizzo virtuale (VA) della posizione.|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è una classe base virtuale.|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Recupera l'indice per la tabella di spostamento di base virtuale.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Recupera l'offset della tabella di funzione virtuale di una funzione virtuale.|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Recupera l'offset del puntatore di base virtuale.|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Recupera il tipo di puntatore una tabella di base virtuale.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Recupera l'interfaccia di simbolo del tipo di tabella virtuale per un tipo definito dall'utente.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Recupera l'identificatore di tabella virtuale forma del simbolo.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è volatile.|  
  
## <a name="remarks"></a>Note  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Per ottenere questa interfaccia, una chiamata a uno dei metodi seguenti:  
  
-   [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
-   [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
-   [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
-   [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come visualizzare le variabili locali per una funzione in un determinato indirizzo virtuale relativo. Viene inoltre illustrato come i simboli di tipi diversi sono correlati tra loro.  
  
> [!NOTE]
>  `CDiaBSTR` è una classe che esegue il wrapping di un `BSTR` e gestisce automaticamente liberando la stringa quando la creazione dell'istanza diventa esterno all'ambito.  
  
```C++  
void DumpLocalVars( DWORD rva, IDiaSession *pSession )  
{  
    CComPtr< IDiaSymbol > pBlock;  
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )  
    {  
        Fatal( "Failed to find symbols by RVA" );  
    }  
    CComPtr< IDiaSymbol > pscope;  
    for ( ; pBlock != NULL; )  
    {  
        CComPtr< IDiaEnumSymbols > pEnum;  
        // local data search  
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )  
        {  
            Fatal( "Local scope findChildren failed" );  
        }  
        CComPtr< IDiaSymbol > pSymbol;  
        DWORD tag;  
        DWORD celt;  
        while ( pEnum != NULL &&  
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1)  
        {  
            pSymbol->get_symTag( &tag );  
            if ( tag == SymTagData )  
            {  
                CDiaBSTR name;  
                DWORD    kind;  
                pSymbol->get_name( &name );  
                pSymbol->get_dataKind( &kind );  
                if ( name != NULL )  
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );  
            }  
            else if ( tag == SymTagAnnotation )  
            {  
                CComPtr< IDiaEnumSymbols > pValues;  
                // local data search  
                wprintf_s( L"\tAnnotation:\n" );  
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )  
                    Fatal( "Annotation findChildren failed" );  
                pSymbol = NULL;  
                while ( pValues != NULL &&  
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&  
                        celt == 1 )  
                {  
                    CComVariant value;  
                    if ( pSymbol->get_value( &value ) != S_OK )  
                        Fatal( "No value for annotation data." );  
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );  
                    pSymbol = NULL;  
                }  
            }  
            pSymbol = NULL;  
        }  
        pBlock->get_symTag( &tag );   
        if ( tag == SymTagFunction )    // stop when at function scope  
            break;  
        // move to lexical parent  
        CComPtr< IDiaSymbol > pParent;  
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )  
            && pParent != NULL ) {  
            pBlock = pParent;  
        }  
        else  
        {  
            Fatal( "Finding lexical parent failed." );  
        }  
    };  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 `Header:` DIA2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Compilando](../../debugger/debug-interface-access/compiland.md)