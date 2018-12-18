---
title: Suggerimenti ed esempi (SAL)
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: d26f5329f530af2d6547f44b73ded82c5db53f4f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="best-practices-and-examples-sal"></a>Suggerimenti ed esempi (SAL)
Ecco alcuni modi per ottenere il massimo fuori origine codice annotazione Language (SAL) ed evitare alcuni problemi comuni.

## <a name="in"></a>\_In\_

Se la funzione deve per scrivere l'elemento, utilizzare `_Inout_` anziché `_In_`. Ciò è particolarmente importante in caso di conversione automatica da precedenti macro di SAL. Prima di SAL, molti programmatori le macro utilizzate come commenti, le macro che erano denominate `IN`, `OUT`, `IN_OUT`, o varianti di questi nomi. Sebbene sia consigliabile convertire queste macro SAL, è inoltre consiglia di prestare attenzione quando si decide di convertire in quanto il codice potrebbe essere stato modificato dopo il prototipo originale è stato scritto e la macro precedente potrebbe non riflettere più operazioni eseguite dal codice. Prestare particolare attenzione il `OPTIONAL` commento (macro), in quanto spesso viene posizionato in modo non corretto, ad esempio, sul lato di una virgola errato.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="opt"></a>\_opt\_

Se il chiamante non è possibile passare un puntatore null, utilizzare `_In_` o `_Out_` anziché `_In_opt_` o `_Out_opt_`. Questo vale anche per una funzione che controlla i relativi parametri e restituisce un errore se è NULL quando non deve essere. Anche se con una funzione di controllare il relativo parametro valore null imprevisto e restituire normalmente è una buona norma difensivo, questo non significa che l'annotazione del parametro può essere di tipo facoltativo (`_*Xxx*_opt_`).

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}

```

## <a name="predefensive-and-postdefensive"></a>\_Pre\_difensivo\_ e \_Post\_difensivo\_

Se in una funzione è presente un limite di attendibilità, si consiglia di utilizzare l'annotazione `_Pre_defensive_`.  Il modificatore di "difesa" modifica alcune annotazioni per indicare che, al momento della chiamata, controllare rigorosamente l'interfaccia, ma il corpo di implementazione deve presupporre che possono essere passati parametri non corretti. In tal caso, `_In_ _Pre_defensive_` viene preferito ad un limite di attendibilità per indicare che sebbene un chiamante otterrà un errore se tenta di passare NULL, il corpo della funzione verrà analizzato come se il parametro fosse NULL e verranno contrassegnati tutti i tentativi di de referenziare il puntatore senza prima controllare che non sia NULL.  Un'annotazione `_Post_defensive_` può inoltre essere utilizzata nei callback, dove si assume che la parte attendibile sia il chiamante e il codice non attendibile sia il codice chiamato.

## <a name="outwrites"></a>\_Out\_scrive\_

Nell'esempio seguente viene solitamente `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);

```

L'annotazione `_Out_writes_` indica che si dispone di un buffer. Ha `cb` byte allocati, con il primo byte inizializzato all'uscita. Questa annotazione non è rigorosamente corretto ed è utile esprimere le dimensioni allocate. Tuttavia, non indica quanti elementi vengono inizializzati dalla funzione.

L'esempio successivo mostra tre modi di specificare la dimensione esatta della parte del buffer inizializzata correttamente.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);

```

## <a name="out-pstr"></a>\_Out\_ PSTR

L'utilizzo di `_Out_ PSTR` è quasi sempre errato. Ciò viene interpretato come definire un parametro di output che punta a un buffer di caratteri ed è con terminazione NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);

```

Ad esempio un'annotazione `_In_ PCSTR` è comune e utile. Punta a una stringa di input con terminazione NULL, perché la condizione preliminare di `_In_` consente il riconoscimento di una stringa con terminazione NULL.

## <a name="in-wchar-p"></a>\_In\_ WCHAR * p

`_In_ WCHAR* p` indica che è un puntatore di input `p` che punta a un carattere. Tuttavia, nella maggior parte dei casi, ciò è probabilmente non la specifica che deve essere. Che cos'è probabilmente è invece la specifica di una matrice con terminazione NULL; a tale scopo, utilizzare `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);

```

Manca la specifica di terminazione NULL appropriata è comune. Utilizzare l'oggetto appropriato `STR` versione per sostituire il tipo, come illustrato nell'esempio seguente.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}

```

## <a name="outrange"></a>\_Out_range\_

Se il parametro è un puntatore e si desidera esprimere l'intervallo del valore dell'elemento a cui punta il puntatore, utilizzare `_Deref_out_range_` anziché `_Out_range_`. Nell'esempio seguente, l'intervallo di * viene espresso pcbFilled, non pcbFilled.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);

```

 `_Deref_out_range_(0, cbSize)` non è strettamente necessaria per alcuni strumenti perché può essere dedotto da `_Out_writes_to_(cbSize,*pcbFilled)`, ma viene comunque indicato di seguito per motivi di completezza.

## <a name="wrong-context-in-when"></a>Contesto errato in \_quando\_

Un altro errore comune consiste nell'utilizzare post-stato di valutazione per le precondizioni. Nell'esempio seguente, `_Requires_lock_held_` è una precondizione.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);

```

 L'espressione `result` fa riferimento a un valore di post-stato che non è disponibile in pre stato di.

## <a name="true-in-success"></a>TRUE in \_esito positivo\_

Se la funzione ha esito positivo quando il valore restituito è diverso da zero, utilizzare `return != 0` come condizione di esito positivo anziché `return == TRUE`. NonZero non implica necessariamente l'equivalenza con il valore effettivo che il compilatore fornisce per `TRUE`. Il parametro `_Success_` è un'espressione e le seguenti espressioni vengono valutate come equivalenti: `return != 0`, `return != false`, `return != FALSE` e `return` senza parametri o confronti.

```cpp

// Incorrect
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

```

## <a name="reference-variable"></a>Variabile di riferimento

Per una variabile di riferimento, la versione precedente di SAL utilizzato l'indicatore di misura implicita come destinazione annotazione e necessari l'aggiunta di un `__deref` alle annotazioni che è collegato a una variabile di riferimento. Questa versione viene utilizzato l'oggetto stesso e non richiedono altro `_Deref_`.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);

```

## <a name="annotations-on-return-values"></a>Annotazioni sui valori restituiti

Nell'esempio seguente viene illustrato un problema comune nelle annotazioni di valore restituito.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();

```

In questo esempio, `_Out_opt_` è indicato che il puntatore potrebbe essere NULL durante la precondizione. Impossibile applicare le precondizioni, tuttavia, il valore restituito. In questo caso, l'annotazione corretto è `_Ret_maybenull_`.

## <a name="see-also"></a>Vedere anche

[Utilizzo delle annotazioni SAL per ridurre gli errori del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[comprensione SAL](../code-quality/understanding-sal.md)
[annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md) 
 [Annotazione del comportamento della funzione](../code-quality/annotating-function-behavior.md)
[annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)
[annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md) 
 [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[funzioni intrinseche](../code-quality/intrinsic-functions.md)