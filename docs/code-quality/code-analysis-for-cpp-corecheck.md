---
title: Linee guida di Visual Studio C++ Core controllo riferimento | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d5db13aa350e33a297981066f36c3d1dfd1ecb67
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="c-core-guidelines-checker-reference"></a>Linee guida di base C++ controllo di riferimento
In questa sezione sono elencati gli avvisi del correttore linee guida di base di C++. Per informazioni sull'analisi del codice, vedere [/analyze (analisi di codice)](/cpp/build/reference/analyze-code-analysis) e [avvio rapido: analisi del codice per C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).  
  
**Nota**: alcuni avvisi appartengono a più di un gruppo e non tutti gli avvisi da un argomento di riferimento.

## <a name="ownerpointer-group"></a>Gruppo OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  
  Se dispone di un costruttore di spostamento, restituire un oggetto con ambito invece di allocazione heap. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
     
[C26403 RESET_OR_DELETE_OWNER](C26403.md)  
  Ripristinare o eliminare in modo esplicito un proprietario\<T > '% variabile %' puntatore. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
     
[C26404 DONT_DELETE_INVALID](C26404.md)  
  Non eliminare un proprietario\<T > che potrebbe essere in stato non valido. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)  
  Non assegnare a un proprietario\<T > che potrebbe essere in stato valido. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)  
  Non si assegna un puntatore non elaborato a un proprietario\<T >. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
  
[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)  
  Gli oggetti con ambiti di preferito, non heap-allocare inutilmente. Vedere [linee guida di base C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  

[C26429 USE_NOTNULL](C26429.md)  
  Simbolo '% % di simboli' non si verifica mai dell'invalidità, possono essere contrassegnato come not_null. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  Simbolo '% simbolo %' non è stato testato dell'invalidità su tutti i percorsi. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  Il tipo dell'espressione '% % expr' è già gsl::not_null. Eseguire test e dell'invalidità. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

## <a name="rawpointer-group"></a>RAW_POINTER Group
 
[C26400  NO_RAW_POINTER_ASSIGNMENT](c26400.md)  
Non assegnare il risultato di un'allocazione o una chiamata di funzione con un proprietario\<T > di un valore restituito a un puntatore non elaborato, utilizzare proprietario\<T > in alternativa. Vedere [linee guida di base C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26401 DONT_DELETE_NON_OWNER](c26401.md)  
Non eliminare un puntatore non elaborato non è un proprietario\<T >. Vedere [linee guida di base C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   restituiscono un oggetto con ambito invece di allocazione heap se dispone di un costruttore di spostamento. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
 
[C26408 NO_MALLOC_FREE](C26408.md)  
  Evitare malloc () e Free (), preferire la versione nothrow di nuovo con l'istruzione delete. Vedere [linee guida di base C++ R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).  
  
[C26409 NO_NEW_DELETE](C26409.md)  
  Evitare di chiamare di nuovo ed eliminare in modo esplicito, utilizzare std::make_unique\<T > in alternativa. Vedere [linee guida di base C++ R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).  

[C26429 USE_NOTNULL](C26429.md)  
  Simbolo '% % di simboli' non si verifica mai dell'invalidità, possono essere contrassegnato come not_null. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  Simbolo '% simbolo %' non è stato testato dell'invalidità su tutti i percorsi. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  Il tipo dell'espressione '% % expr' è già gsl::not_null. Eseguire test e dell'invalidità. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26481 NO_POINTER_ARITHMETIC](C26481.md)  
  Non utilizzare l'aritmetica dei puntatori. In alternativa, usare l'intervallo. Vedere [Bounds.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  L'espressione '% % expr': non matrice da decadimento puntatore. Vedere [Bounds.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

## <a name="uniquepointer-group"></a>Gruppo UNIQUE_POINTER
  
[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)  
  Il parametro '% % di parametro' è un riferimento a `const` puntatore univoco, utilizzare const T * o const T & invece. Vedere [linee guida di base C++ R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).  
     
[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)  
  Il parametro '% % di parametro' è un riferimento al puntatore univoco e viene riassegnato o reimpostato mai, utilizzare T * o T & invece. Vedere [linee guida di base C++ R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).  
     
[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Spostare, copiare, riassegnare o reimpostare un puntatore intelligente locale '% simbolo %'. Vedere [linee guida di base C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Puntatore intelligente parametro '% simbolo %' viene utilizzato solo per il puntatore di accesso ai contenuti. Utilizzare T * o T & invece. Vedere [linee guida di base C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  

## <a name="sharedpointer-group"></a>Gruppo SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Spostare, copiare, riassegnare o reimpostare un puntatore intelligente locale '% simbolo %'. Vedere [linee guida di base C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Puntatore intelligente parametro '% simbolo %' viene utilizzato solo per il puntatore di accesso ai contenuti. Utilizzare T * o T & invece. Vedere [linee guida di base C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  
    
[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)  
  Puntatore condiviso '% % di simboli' viene passato per riferimento rvalue. Passare invece per valore. Vedere [linee guida di base C++ R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).  
  
[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)  
  Puntatore condiviso parametro '% simbolo %' è passato per riferimento e non è stato reimpostato o riassegnato. Utilizzare T * o T & invece. Vedere [linee guida di base C++ R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).  
  
[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)  
  Parametro del puntatore condiviso '% simbolo %' non viene copiato o spostato. Utilizzare T * o T & invece. Vedere [linee guida di base C++ R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).  

## <a name="declaration-group"></a>Gruppo di dichiarazione
    
[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)  
  Inizializzatore globale chiama una funzione constexpr non '% simbolo %'. Vedere [linee guida di base C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)  
  Inizializzatore globale accede oggetto extern '% simbolo %'. Vedere [linee guida di base C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) evitare senza nome oggetti con personalizzata costruzione e distruzione. [ES.84: Non (provare a) dichiarare una variabile locale senza nome](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Gruppo di classi
    
[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)  
  Se si definiscono o elimina qualsiasi operazione predefinita nel tipo '% simbolo %', definire o eliminarli tutti. Vedere [linee guida di base C++ C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).  


[C26433 OVERRIDE_EXPLICITLY](c26433.md) funzione '% % di simboli' deve essere contrassegnata con 'override'. Vedere [ C.128: funzioni virtuali devono specificare esattamente un override virtuali, o l'ultimo](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final). 

  
[C26434 DONT_HIDE_METHODS](C26434.md)  
  Funzione '% % symbol_1' nasconde una funzione non virtuale '% symbol_2% '. Vedere [linee guida di base C++ C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).  
  

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) funzione '% % di simboli' deve specificare esattamente uno di 'virtual', 'override' o 'final'. Vedere [ C.128: funzioni virtuali devono specificare esattamente un override virtuali, o l'ultimo](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md). 


[C26436 NEED_VIRTUAL_DTOR](C26436.md)  
  Il tipo '% simbolo % con una funzione virtuale deve entrambi distruttore non virtuale pubblico virtuale o protetto. Vedere [linee guida di base C++ C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).  


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) distruttore di sostituzione non è consigliabile utilizzare esplicita 'override' o 'virtuali' identificatori. Vedere [C.128: funzioni virtuali devono specificare esattamente un override virtuali, o l'ultimo](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>TIPO di gruppo
    
[C26437 DONT_SLICE](C26437.md)  
  Non sezionare. Vedere [linee guida di base C++ ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).  

## <a name="style-group"></a>Gruppo di stili  
[C26438 NO_GOTO](C26438.md)  
  Evitare `goto`. Vedere [linee guida di base C++ ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).  
  
## <a name="function-group"></a>Gruppo di funzioni
    
[C26439 SPECIAL_NOEXCEPT](C26439.md)  
  Questo tipo di funzione non può generare. Dichiara la classe `noexcept`. Vedere [linee guida di base C++ f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  
  
[C26440 DECLARE_NOEXCEPT](C26440.md)  
  Funzione '% simbolo %' può essere dichiarata `noexcept`. Vedere [linee guida di base C++ f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  

## <a name="concurrency-group"></a>Gruppo di concorrenza
    
[C26441 NO_UNNAMED_GUARDS](C26441.md)  
 Gli oggetti di protezione devono essere denominati. Vedere [cp.44 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).  

## <a name="const-group"></a>Gruppo CONST
    
C26460 USE_CONST_REFERENCE_ARGUMENTS  
  L'argomento di riferimento '% % di argomento' per la funzione '% % di funzione' può essere contrassegnato come `const`. Vedere [con.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26461 USE_CONST_POINTER_ARGUMENTS: l'argomento del puntatore 'argomento di % %' per la funzione '% % di funzione' può essere contrassegnato come un puntatore a `const`. Vedere [con.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26462 USE_CONST_POINTER_FOR_VARIABLE  
  Il valore a cui fa riferimento '% variabile %' è assegnato una sola volta, contrassegnarlo come un puntatore a `const`. Vedere [con.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26463 USE_CONST_FOR_ELEMENTS  
  Gli elementi della matrice '% % di matrice' una sola volta, vengono assegnati gli elementi di contrassegno `const`. Vedere [con.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26464 USE_CONST_POINTER_FOR_ELEMENTS  
  I valori a cui fa riferimento a elementi di matrice '% % di matrice' una sola volta, vengono assegnati elementi contrassegna come puntatore a `const`. Vedere [con.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  

C26496 USE_CONST_FOR_VARIABLE  
  La variabile '% variabile %' è assegnata una sola volta, contrassegnarlo come `const`. Vedere [con.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26497 USE_CONSTEXPR_FOR_FUNCTION  
  Questa funzione % % funzione potrebbe essere contrassegnato come `constexpr` se si desidera la valutazione in fase di compilazione. Vedere [linee guida di base C++ f. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).  
  
C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL  
  Utilizzare questa funzione chiamata % funzione % `constexpr` se si desidera la valutazione in fase di compilazione. Vedere [con.5 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).  

## <a name="type-group"></a>TIPO di gruppo
C26465 NO_CONST_CAST_UNNECESSARY  
  Non utilizzare `const_cast` per eseguire il cast `const`. `const_cast`non è obbligatorio. non si desidera rimuovere da questa conversione constness o volatilità. Vedere [Type.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).  
  
C26466 NO_STATIC_DOWNCAST_POLYMORPHIC  
  Non utilizzare `static_cast` downcast. Un cast da un tipo polimorfico deve utilizzare dynamic_cast. Vedere [Type.2 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).  
  
C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR  
  Non utilizzare `reinterpret_cast`. Può usare un cast da void * `static_cast`. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)  
  Non utilizzare un `static_cast` per le conversioni aritmetiche. Utilizzare l'inizializzazione con parentesi graffe, gsl::narrow_cast o gsl::narow. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26473 NO_IDENTITY_CAST](C26473.md)  
  Non eseguire il cast tra tipi di puntatore in cui il tipo di origine e il tipo di destinazione sono uguali. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26474 NO_IMPLICIT_CAST](C26474.md)  
  Non eseguire il cast tra tipi puntatore quando la conversione potrebbe essere implicita. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)  
  Non utilizzare stile della funzione cast di C. Vedere [linee guida di base C++ ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).  
     
C26490 NO_REINTERPRET_CAST  
  Non utilizzare `reinterpret_cast`. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26491 NO_STATIC_DOWNCAST  
  Non utilizzare `static_cast` downcast. Vedere [Type.2 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26492 NO_CONST_CAST  
  Non utilizzare `const_cast` per eseguire il cast `const`. Vedere [Type.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
    
C26493 NO_CSTYLE_CAST  
  Non utilizzare cast di tipo C. Vedere [Type.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type). 
     
C26494 VAR_USE_BEFORE_INIT  
  Variabile '% variabile %' non è inizializzata. Inizializzare sempre un oggetto. Vedere [Type.5 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26495 MEMBER_UNINIT  
  Variabile '% variabile %' non è inizializzata. Sempre inizializzare una variabile membro. Vedere [Type.6 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
## <a name="bounds-group"></a>Gruppo di limiti

[C26481 NO_POINTER_ARITHMETIC](C26481.md)   
  Non utilizzare l'aritmetica dei puntatori. In alternativa, usare l'intervallo. Vedere [Bounds.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26482 NO_DYNAMIC_ARRAY_INDEXING  
  Solo l'indice di matrici utilizzando espressioni costanti. Vedere [Bounds.2 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26483 STATIC_INDEX_OUT_OF_RANGE  
  Valore % % di valore è esterno ai limiti (0, associato %) della variabile '% variabile %'. Solo l'indice di matrici utilizzando espressioni costanti che sono all'interno dei limiti della matrice. Vedere [Bounds.2 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  L'espressione '% % expr': non matrice da decadimento puntatore. Vedere [Bounds.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
## <a name="see-also"></a>Vedere anche  
[Utilizzando i controlli della linee guida C++ Core](using-the-cpp-core-guidelines-checkers.md)
