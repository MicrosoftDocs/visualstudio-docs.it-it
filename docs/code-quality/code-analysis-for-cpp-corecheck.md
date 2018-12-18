---
title: Controllo riferimenti di Visual Studio C++ Core linee guida
ms.date: 03/22/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6d68ed1d7002ac0e92d3a8c3e32226cb3a38c3f0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="c-core-guidelines-checker-reference"></a>Linee guida di base C++ controllo di riferimento

In questa sezione sono elencati gli avvisi del correttore linee guida di base di C++. Per informazioni sull'analisi del codice, vedere [/analyze (analisi di codice)](/cpp/build/reference/analyze-code-analysis) e [avvio rapido: analisi del codice per C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Alcuni avvisi appartengano a più di un gruppo e non tutti gli avvisi sono un argomento di riferimento complete.

## <a name="ownerpointer-group"></a>Gruppo OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) restituiscono un oggetto con ambito invece di allocazione heap se dispone di un costruttore di spostamento. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) reimpostare o eliminare in modo esplicito un proprietario\<T > indicatore di misura '% variabile %'. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) non si elimina un proprietario\<T > che potrebbe essere in stato non valido. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) non vengono assegnati a un proprietario\<T > che potrebbe essere in stato valido. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) non si assegna un puntatore non elaborato a un proprietario\<T >. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) preferiscono gli oggetti con ambiti, non heap-allocare inutilmente. Vedere [linee guida di base C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) simbolo '% simbolo %' non si verifica mai dell'invalidità, può essere contrassegnato come not_null. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) simbolo '% simbolo %' non è stato testato dell'invalidità per tutti i percorsi. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) il tipo dell'espressione 'expr % %' è già gsl::not_null. Eseguire test e dell'invalidità. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>Gruppo RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) non assegnare il risultato di un'allocazione o una chiamata di funzione con un proprietario\<T > di un valore restituito per un puntatore non elaborato, utilizzare proprietario\<T > in alternativa. Vedere [linee guida di base C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) non si elimina un puntatore non elaborato che non è un proprietario\<T >. Vedere [linee guida di base C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   restituiscono un oggetto con ambito invece di allocazione heap se dispone di un costruttore di spostamento. Vedere [linee guida di base C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) evitare malloc () e Free (), preferire la versione nothrow di nuovo con l'istruzione delete. Vedere [linee guida di base C++ R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) evitare la chiamata a new e delete in modo esplicito, utilizzare std::make_unique\<T > in alternativa. Vedere [linee guida di base C++ R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) simbolo '% simbolo %' non si verifica mai dell'invalidità, può essere contrassegnato come not_null. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) simbolo '% simbolo %' non è stato testato dell'invalidità per tutti i percorsi. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) il tipo dell'espressione 'expr % %' è già gsl::not_null. Eseguire test e dell'invalidità. Vedere [linee guida di base C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) non usano l'aritmetica dei puntatori. In alternativa, usare l'intervallo. Vedere [Bounds.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
L'espressione '% % expr': non matrice da decadimento puntatore. Vedere [Bounds.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>Gruppo UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) il parametro '% % di parametro' è un riferimento a `const` puntatore univoco, utilizzare const T * o const T & invece. Vedere [linee guida di base C++ R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) il parametro '% % di parametro' è un riferimento al puntatore univoco e viene riassegnato o reimpostato mai, utilizzare T * o T & invece. Vedere [linee guida di base C++ R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) spostare, copiare, riassegnare o reimpostare un puntatore intelligente locale '% simbolo %'. Vedere [linee guida di base C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) puntatore intelligente parametro '% simbolo %' viene utilizzato solo per accedere a puntatore indipendente. Utilizzare T * o T & invece. Vedere [linee guida di base C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>Gruppo SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) spostare, copiare, riassegnare o reimpostare un puntatore intelligente locale '% simbolo %'. Vedere [linee guida di base C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) puntatore intelligente parametro '% simbolo %' viene utilizzato solo per accedere a puntatore indipendente. Utilizzare T * o T & invece. Vedere [linee guida di base C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) parametro del puntatore condiviso '% simbolo %' è passato per riferimento rvalue. Passare invece per valore. Vedere [linee guida di base C++ R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) parametro del puntatore condiviso '% simbolo %' è passato per riferimento e non la reimpostazione o riassegnato. Utilizzare T * o T & invece. Vedere [linee guida di base C++ R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) parametro del puntatore condiviso '% simbolo %' non viene copiato o spostato. Utilizzare T * o T & invece. Vedere [linee guida di base C++ R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Gruppo di dichiarazione

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) inizializzatore globale chiama una funzione constexpr non '% simbolo %'. Vedere [linee guida di base C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) inizializzatore globale accede all'oggetto extern '% simbolo %'. Vedere [linee guida di base C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) evitare senza nome oggetti con personalizzata costruzione e distruzione. Vedere [ES.84: non (provare a) dichiarare una variabile locale senza nome](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Gruppo di classi

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) se si definiscono o elimina qualsiasi operazione predefinita nel tipo '% simbolo %', definire o eliminarli tutti. Vedere [linee guida di base C++ C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) funzione '% % di simboli' deve essere contrassegnata con 'override'. Vedere [C.128: funzioni virtuali devono specificare esattamente un override virtuali, o l'ultimo](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) funzione '% symbol_1% ' nasconde una funzione non virtuale '% symbol_2% '. Vedere [linee guida di base C++ C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) funzione '% % di simboli' deve specificare esattamente uno di 'virtual', 'override' o 'final'. Vedere [C.128: funzioni virtuali devono specificare esattamente un override virtuali, o l'ultimo](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


[C26436 NEED_VIRTUAL_DTOR](C26436.md) entrambi pubblico virtuale o protetto il distruttore per il tipo '% simbolo % con una funzione virtuale necessarie. Vedere [linee guida di base C++ C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) distruttore di sostituzione non è consigliabile utilizzare esplicita 'override' o 'virtuali' identificatori. Vedere [C.128: funzioni virtuali devono specificare esattamente un override virtuali, o l'ultimo](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>TIPO di gruppo

[C26437 DONT_SLICE](C26437.md) non sezionare. Vedere [linee guida di base C++ ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Gruppo di stili

[C26438 NO_GOTO](C26438.md) evitare `goto`. Vedere [linee guida di base C++ ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Gruppo di funzioni

[C26439 SPECIAL_NOEXCEPT](C26439.md) questo tipo di funzione non può generare. Dichiara la classe `noexcept`. Vedere [linee guida di base C++ f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) funzione '% simbolo %' può essere dichiarata `noexcept`. Vedere [linee guida di base C++ f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) la funzione viene dichiarata **noexcept** ma chiama una funzione che può generare eccezioni.
Vedere [linee guida dei componenti di base di C++: f. 6: se la funzione non può generare, dichiararla come noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Gruppo di concorrenza

[C26441 NO_UNNAMED_GUARDS](C26441.md) oggetti Guard devono essere denominati. Vedere [cp.44 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Gruppo CONST

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) l'argomento di riferimento '% argomento %' per la funzione '% % di funzione' può essere contrassegnato come `const`. Vedere [con.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): l'argomento del puntatore 'argomento % %' per la funzione '% % di funzione' può essere contrassegnato come un puntatore a `const`. Vedere [con.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) il valore a cui fa riferimento '% variabile %' è assegnato una sola volta, contrassegnarlo come un puntatore a `const`. Vedere [con.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) gli elementi della matrice '% % di matrice' una sola volta, vengono assegnati gli elementi di contrassegno `const`. Vedere [con.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) i valori puntati da elementi di matrice '% % di matrice' una sola volta, vengono assegnati gli elementi di contrassegno come puntatore a `const`. Vedere [con.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) la variabile '% variabile %' è assegnata una sola volta, contrassegnarlo come `const`. Vedere [con.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) potrebbe essere contrassegnato come funzione di % questa funzione `constexpr` se si desidera la valutazione in fase di compilazione. Vedere [linee guida di base C++ f. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) possibile utilizzare questa funzione chiamata % funzione % `constexpr` se si desidera la valutazione in fase di compilazione. Vedere [con.5 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>TIPO di gruppo

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) non usano `const_cast` eseguire il cast `const`. `const_cast` non è obbligatorio. non si desidera rimuovere da questa conversione constness o volatilità. Vedere [Type.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) non usare `static_cast` il downcast. Un cast da un tipo polimorfico deve utilizzare dynamic_cast. Vedere [Type.2 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) non usare `reinterpret_cast`. Può usare un cast da void * `static_cast`. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) non usare un `static_cast` per le conversioni aritmetiche. Utilizzare l'inizializzazione con parentesi graffe, gsl::narrow_cast o gsl::narow. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) non eseguire il cast tra tipi di puntatore in cui il tipo di origine e il tipo di destinazione sono uguali. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) non eseguire il cast tra tipi puntatore quando la conversione potrebbe essere implicita. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) non utilizzano il tipo di funzione C-cast. Vedere [linee guida di base C++ ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) non usare `reinterpret_cast`. Vedere [Type.1 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) non usare `static_cast` il downcast. Vedere [Type.2 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) non usano `const_cast` eseguire il cast `const`. Vedere [Type.3 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) non utilizzare i cast di tipo C. Vedere [Type.4 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) variabile '% variabile %' non è inizializzata. Inizializzare sempre un oggetto. Vedere [Type.5 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) variabile '% variabile %' non è inizializzata. Sempre inizializzare una variabile membro. Vedere [Type.6 linee guida di base C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Gruppo di limiti

[C26446 USE_GSL_AT](c26446.md) preferiscono utilizzare `gsl::at()` anziché l'operatore di indice non è selezionata. Vedere [linee guida dei componenti di base di C++: Bounds.4: non utilizzare le funzioni della libreria standard e tipi che non sono al controllo dei limiti](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Non utilizzare l'aritmetica dei puntatori. In alternativa, usare l'intervallo. Vedere [Bounds.1 linee guida dei componenti di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) solo indicizzazione di matrici utilizzando le espressioni costanti. Vedere [Bounds.2 linee guida dei componenti di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) valore % valore è esterno ai limiti (0, associato %) della variabile '% variabile %'. Solo l'indice di matrici utilizzando espressioni costanti che sono all'interno dei limiti della matrice. Vedere [Bounds.2 linee guida dei componenti di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) espressione 'expr % %': non matrice da decadimento puntatore. Vedere [Bounds.3 linee guida dei componenti di base di C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Gruppo GSL

[C26445 NO_SPAN_REF](c26445.md) un riferimento a `gsl::span` o `std::string_view` potrebbe essere un'indicazione di un problema di durata.
Vedere [GSL.view linee guida dei componenti di base di C++: viste](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) preferiscono utilizzare `gsl::at()` anziché l'operatore di indice non è selezionata. Vedere [linee guida dei componenti di base di C++: Bounds.4: non utilizzare le funzioni della libreria standard e tipi che non sono al controllo dei limiti](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY ](c26448.md) si consiglia di utilizzare `gsl::finally` se azione finale è destinato. Vedere [linee guida dei componenti di base di C++: GSL.util: utilità](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` o `std::string_view` creato da una password temporanea non sarà possibile quando il file temporaneo viene invalidato. Vedere [linee guida dei componenti di base di C++: GSL.view: viste](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).


## <a name="deprecated-warnings"></a>Avvisi deprecati

Gli avvisi seguenti sono presenti in un set di regole sperimentale anticipata di controllo linee guida dei componenti di base, ma ora sono deprecati e possono essere tranquillamente ignorati. Gli avvisi vengono sostituiti da avvisi nell'elenco precedente.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- VALID_OWNER_LEAVING_SCOPE 26422
- ALLOCATION_NOT_ASSIGNED_TO_OWNER 26423
- VALID_ALLOCATION_LEAVING_SCOPE 26424
- 26425 ASSIGNING_TO_STATIC
- NO_LIFETIME_TRACKING 26499

## <a name="see-also"></a>Vedere anche
[Utilizzando i controlli della linee guida C++ Core](using-the-cpp-core-guidelines-checkers.md)
