---
title: 'CA1806: Non ignorare i risultati dei metodi'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 605222de258598e1022288b50f0a30ba87777fdc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Non ignorare i risultati dei metodi
|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Esistono diversi motivi possibili per questo avviso:

-   Viene creato un nuovo oggetto, ma mai utilizzato.

-   Viene chiamato un metodo che crea e restituisce una nuova stringa e la nuova stringa non viene mai utilizzata.

-   Un metodo COM o P/Invoke che restituisce un codice di errore o HRESULT che non viene mai utilizzato. Descrizione della regola

 Creazione di oggetti non necessari e la garbage collection associata dell'oggetto inutilizzato influire negativamente sulle prestazioni.

 Le stringhe sono immutabili e metodi, ad esempio String. ToUpper restituisce una nuova istanza di una stringa anziché modificare l'istanza di stringa nel metodo chiamante.

 Ignorando HRESULT o codice di errore può causare un comportamento imprevisto in condizioni di errore o di risorse insufficienti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se il metodo crea una nuova istanza dell'oggetto B che non viene mai usato, passare l'istanza come argomento a un altro metodo o assegnare l'istanza a una variabile. Se la creazione dell'oggetto non è necessaria, rimuoverla- o -

 Se il metodo chiama il metodo B, ma non utilizza la nuova istanza della stringa restituita dal metodo B. Passare l'istanza come argomento a un altro metodo, assegnare l'istanza a una variabile. Oppure rimuovere la chiamata se non è necessaria.

 oppure

 Se il metodo chiama il metodo B, ma non viene utilizzato il valore HRESULT o codice di errore che il metodo restituisce. Utilizzare il risultato in un'istruzione condizionale, assegnare il risultato a una variabile oppure passarlo come argomento a un altro metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola, a meno che l'operazione di creazione dell'oggetto scopo preciso.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe che ignora il risultato della chiamata String. Trim.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>Esempio
 Nell'esempio seguente consente di correggere la violazione precedente assegnando il risultato di String. Trim alla variabile che in cui è stata chiamata.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che non utilizza un oggetto che viene creato.

> [!NOTE]
>  Questa violazione non può essere riprodotti in Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>Esempio
 Nell'esempio seguente consente di correggere la violazione precedente rimuovendo la creazione di un oggetto non necessaria.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->