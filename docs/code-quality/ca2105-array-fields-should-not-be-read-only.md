---
title: 'CA2105: I campi di matrici non devono essere di sola lettura'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b652247ea727c59a9e0d0d0c6850039be52634
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: I campi di matrici non devono essere di sola lettura
|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un campo pubblico o protetto che contiene una matrice è dichiarato di sola lettura.

## <a name="rule-description"></a>Descrizione della regola
 Quando si applica il `readonly` (`ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) modificatore a un campo che contiene una matrice, il campo non può essere modificato per fare riferimento a una matrice diversa. È tuttavia possibile modificare gli elementi della matrice archiviati in un campo in sola lettura. Codice che prende decisioni o esegua operazioni che si basano sugli elementi di una matrice di sola lettura che è possibile accedere pubblicamente potrebbe contenere una vulnerabilità della protezione.

 Si noti che anche la presenza di un campo pubblico viola la regola di progettazione [CA1051: non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per risolvere le vulnerabilità di sicurezza che è identificato da questa regola, non fare affidamento sul contenuto di una matrice di sola lettura accessibile pubblicamente. È consigliabile utilizzare una delle procedure seguenti:

-   Sostituire la matrice con una raccolta fortemente tipizzata che non può essere modificata. Per altre informazioni, vedere <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

-   Sostituire il campo pubblico con un metodo che restituisce un clone di una matrice privata. Poiché il codice non si basano sul duplicato, non vi è alcun rischio se gli elementi vengono modificati.

 Se si sceglie il secondo approccio, non sostituire il campo con una proprietà. proprietà che restituiscono matrici può influire negativamente sulle prestazioni. Per ulteriori informazioni, vedere [CA1819: le proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Esclusione di un avviso da questa regola è fortemente sconsigliato. Possono verificarsi quasi alcun scenari in cui il contenuto di un campo di sola lettura non è importante. Se questo è il caso, rimuovere il `readonly` modificatore anziché escludere il messaggio.

## <a name="example"></a>Esempio
 In questo esempio vengono illustrati i rischi di violazione di questa regola. La prima parte viene illustrata una libreria di esempio con un tipo, `MyClassWithReadOnlyArrayField`, che contiene due campi (`grades` e `privateGrades`) che non sono protette. Il campo `grades` sia pubblico e pertanto vulnerabile a qualsiasi chiamante. Il campo `privateGrades` è privato, ma è comunque vulnerabile poiché viene restituito per i chiamanti dal `GetPrivateGrades` metodo. Il `securePrivateGrades` esposto in modo sicuro dal campo di `GetSecurePrivateGrades` metodo. Dichiarata come privata seguire migliori pratiche di progettazione. La seconda parte viene illustrato il codice che modifica i valori archiviati nel `grades` e `privateGrades` membri.

 La libreria di classi di esempio viene visualizzato nell'esempio seguente.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example"></a>Esempio
 Il codice seguente usa la libreria di classi di esempio per illustrare i problemi di sicurezza di matrice di sola lettura.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

 L'output di questo esempio è:

 **Prima di eventuali manomissioni: voti: 90, 90, 90 gradi privato: 90, 90, 90 gradi Secure, 90, 90, 90**
**dopo eventuali manomissioni: voti: 90, 555, 90 gradi privato: 90, 555, 90 gradi Secure, 90, 90, 90**
## <a name="see-also"></a>Vedere anche
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>