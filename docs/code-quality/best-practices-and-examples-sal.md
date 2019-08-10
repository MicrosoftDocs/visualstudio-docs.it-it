---
title: Suggerimenti ed esempi (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 478efc77bd1fb14f6241e026cfe280355a90746a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919451"
---
# <a name="best-practices-and-examples-sal"></a>Suggerimenti ed esempi (SAL)
Ecco alcuni modi per sfruttare al meglio il linguaggio di annotazione del codice sorgente (SAL) ed evitare alcuni problemi comuni.

## <a name="_in_"></a>\_In\_

Se si suppone che la funzione scriva nell'elemento, usare `_Inout_` `_In_`anziché. Questa operazione è particolarmente importante in caso di conversione automatica da macro precedenti a SAL. Prima di Sal, molti programmatori usavano le macro come commenti, ovvero le macro `IN`denominate `IN_OUT`, `OUT`, o varianti di questi nomi. Anche se si consiglia di convertire queste macro in SAL, è necessario prestare attenzione quando si esegue la conversione perché il codice potrebbe essere stato modificato dopo che il prototipo originale è stato scritto e la macro precedente potrebbe non riflettere più le operazioni del codice. Prestare particolare attenzione alla `OPTIONAL` macro di commento perché spesso viene posizionata in modo non corretto, ad esempio sul lato errato di una virgola.

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

## <a name="_opt_"></a>\_opt\_

Se al chiamante non è consentito passare un puntatore null, `_In_` utilizzare o `_Out_` anziché `_In_opt_` o `_Out_opt_`. Si applica anche a una funzione che controlla i relativi parametri e restituisce un errore se è NULL se non deve essere. Sebbene la presenza di una funzione per il controllo del parametro per un valore NULL imprevisto e la restituzione di una normale procedura di codifica, non significa che l'annotazione del`_*Xxx*_opt_`parametro può essere di tipo facoltativo ().

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

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Pre\_-\_ difensivo e \_Post\_-difesa\_

Se in una funzione è presente un limite di attendibilità, si consiglia di utilizzare l'annotazione `_Pre_defensive_`.  Il modificatore "difensivo" modifica alcune annotazioni per indicare che, al momento della chiamata, l'interfaccia deve essere controllata rigorosamente, ma nel corpo di implementazione deve presumere che potrebbero essere passati parametri non corretti. In tal caso, `_In_ _Pre_defensive_` viene preferito ad un limite di attendibilità per indicare che sebbene un chiamante otterrà un errore se tenta di passare NULL, il corpo della funzione verrà analizzato come se il parametro fosse NULL e verranno contrassegnati tutti i tentativi di de referenziare il puntatore senza prima controllare che non sia NULL.  Un'annotazione `_Post_defensive_` può inoltre essere utilizzata nei callback, dove si assume che la parte attendibile sia il chiamante e il codice non attendibile sia il codice chiamato.

## <a name="_out_writes_"></a>\_Scritture in uscita\_\_

Nell'esempio seguente viene illustrato un utilizzo comune `_Out_writes_`di.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

L'annotazione `_Out_writes_` indica che è presente un buffer. Dispone `cb` di byte allocati, con il primo byte inizializzato all'uscita. Questa annotazione non è strettamente sbagliata ed è utile per esprimere le dimensioni allocate. Tuttavia, non indica il numero di elementi inizializzati dalla funzione.

Nell'esempio riportato di seguito vengono illustrati tre modi corretti per specificare completamente le dimensioni esatte della parte inizializzata del buffer.

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

## <a name="_out_-pstr"></a>\_PSTR\_ out

L'uso di `_Out_ PSTR` è quasi sempre errato. Viene interpretato come avente un parametro di output che punta a un buffer di caratteri e con terminazione NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Un'annotazione come `_In_ PCSTR` è comune e utile. Punta a una stringa di input con terminazione null perché la precondizione di `_In_` consente il riconoscimento di una stringa con terminazione null.

## <a name="_in_-wchar-p"></a>\_In\_ WCHAR * p

`_In_ WCHAR* p`indica che è presente un puntatore `p` di input che punta a un carattere. Nella maggior parte dei casi, tuttavia, probabilmente non è la specifica desiderata. È invece probabile che sia la specifica di una matrice con terminazione NULL. a tale scopo, usare `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Manca la specifica corretta della terminazione NULL è comune. Usare la versione `STR` appropriata per sostituire il tipo, come illustrato nell'esempio seguente.

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

## <a name="_out_range_"></a>\_\_Intervallo\_

Se il parametro è un puntatore e si desidera esprimere l'intervallo del valore dell'elemento a cui punta il puntatore, utilizzare `_Deref_out_range_` `_Out_range_`anziché. Nell'esempio seguente viene espresso l'intervallo di * pcbFilled, non pcbFilled.

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

`_Deref_out_range_(0, cbSize)`non è strettamente necessario per alcuni strumenti perché può essere dedotto da `_Out_writes_to_(cbSize,*pcbFilled)`, ma viene visualizzato qui per motivi di completezza.

## <a name="wrong-context-in-_when_"></a>Contesto errato in \_quando\_

Un altro errore comune è quello di usare la valutazione post-stato per le precondizioni. Nell'esempio `_Requires_lock_held_` seguente è una condizione preliminare.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

L'espressione `result` fa riferimento a un valore di post-stato non disponibile in pre-stato.

## <a name="true-in-_success_"></a>TRUE in \_Success\_

Se la funzione ha esito positivo quando il valore restituito è diverso da `return != 0` `return == TRUE`zero, utilizzare come condizione Success anziché. Il valore diverso da zero non significa necessariamente l'equivalenza al valore effettivo fornito dal compilatore per `TRUE`. Il parametro `_Success_` è un'espressione e le seguenti espressioni vengono valutate come equivalenti: `return != 0`, `return != false`, `return != FALSE` e `return` senza parametri o confronti.

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

Per una variabile di riferimento, la versione precedente di Sal usava il puntatore implicito come destinazione dell'annotazione e richiedeva l'aggiunta di un `__deref` a annotazioni associate a una variabile di riferimento. Questa versione USA l'oggetto stesso e non richiede l'operazione aggiuntiva `_Deref_`.

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

## <a name="annotations-on-return-values"></a>Annotazioni nei valori restituiti

Nell'esempio seguente viene illustrato un problema comune nelle annotazioni del valore restituito.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

In questo esempio, `_Out_opt_` indica che il puntatore potrebbe essere null come parte della precondizione. Tuttavia, non è possibile applicare le precondizioni al valore restituito. In questo caso, l'annotazione `_Ret_maybenull_`corretta è.

## <a name="see-also"></a>Vedere anche

[Uso delle annotazioni SAL per ridurreC++ i difetti](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
di C/codice comprensione dell'annotazione[Sal](../code-quality/understanding-sal.md)
[parametri della funzione e valori](../code-quality/annotating-function-parameters-and-return-values.md)
restituiti annotazione del[comportamento](../code-quality/annotating-function-behavior.md) 
dellafunzione [Annotazione di struct e classi](../code-quality/annotating-structs-and-classes.md)
annotazione del[comportamento](../code-quality/annotating-locking-behavior.md)
di blocco[specificando quando e dove un'annotazione applica](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[funzioni intrinseche](../code-quality/intrinsic-functions.md)