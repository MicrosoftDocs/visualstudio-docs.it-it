---
title: 'Procedura: Creare un tipo nullable (Progettazione classi) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fcef9fc80bbc55b07cd9dad68e217c9982a3b1f7
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Procedura: creare un tipo nullable (Progettazione classi)
Alcuni tipi di valore non sempre hanno (o hanno bisogno di) un valore definito. Questa è una pratica comune nei database, in cui ad alcuni campi potrebbero non essere assegnati valori. Ad esempio, è possibile assegnare un valore null a un campo di database per indicare che non gli è stato ancora assegnato un valore.  
  
Un *tipo nullable* è un tipo di valore che si estende in modo che prenda l'intervallo tipico di valori per il tipo e anche un valore null. Ad esempio, a un valore nullable di `Int32`, detto anche Nullable\<Int32 >, può essere assegnato qualsiasi valore compreso tra -2147483648 e 2147483647 oppure può essere assegnato un valore null. A un oggetto nullable\<bool > possono essere assegnati i valori `True`, `False`, o null (nessun valore).  
  
I tipi nullable sono istanze della struttura <xref:System.Nullable%601>. Ogni istanza di un tipo nullable ha due proprietà pubbliche di sola lettura `HasValue` e `Value`:  
  
-   `HasValue` è di tipo `bool` e indica se la variabile contiene un valore definito. `True` indica che la variabile contiene un valore diverso da null. È possibile testare un valore definito tramite un'istruzione, ad esempio `if (x.HasValue)` o `if (y != null)`.  
  
-   `Value` è dello stesso tipo del tipo sottostante. Se `HasValue` è `True`, `Value` contiene un valore significativo. Se `HasValue` è `False`, l'accesso a `Value` genera un'eccezione di operazione non valida.  
  
Per impostazione predefinita, una variabile dichiarata come tipo nullable non ha alcun valore definito (`HasValue` è `False`), a parte il valore predefinito del tipo di valore sottostante.  
  
Progettazione classi visualizza un tipo nullable, esattamente come visualizza il tipo sottostante.  
  
Per altre informazioni sui tipi nullable in C#, vedere [Tipi nullable](/dotnet/csharp/programming-guide/nullable-types/index). Per altre informazioni sui tipi nullable in Visual Basic, vedere [Tipi di valori Nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).  
  
[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Per aggiungere un tipo nullable tramite Progettazione classi  
  
1.  Nel diagramma classi espandere una classe esistente o creare una nuova classe.  
  
2.  Per aggiungere una classe al progetto, nel menu **Diagramma classi** fare clic su **Aggiungi** e scegliere **Aggiungi classe**.  
  
3.  Per espandere la forma della classe, nel menu **Diagramma classi** fare clic su **Espandi**.  
  
4.  Selezionare la forma della classe. Nel menu **Diagramma classi** fare clic su **Aggiungi** e scegliere **Campo**. Un nuovo campo con il nome predefinito **campo** verrà visualizzato nella forma della classe e anche nella finestra **Dettagli classe**.  
  
5.  Nella colonna **Nome** della finestra **Dettagli classe** (o nella forma della classe stessa) modificare il nome del nuovo campo in un nome valido e significativo.  
  
6.  Nella colonna **Tipo** della finestra **Dettagli classe** dichiarare il tipo come tipo nullable, come illustrato nel codice seguente:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Per aggiungere un tipo nullable tramite Editor del codice  
  
1.  Aggiungere una classe al progetto. Selezionare il nodo del progetto in **Esplora soluzioni** e nel menu **Progetto** fare clic su **Aggiungi classe**.  
  
2.  Nel file con estensione CS o VB della nuova classe, aggiungere uno o più tipi nullable nella nuova classe per la dichiarazione di classe.  
  
3.  Dalla visualizzazione classi, trascinare la nuova icona di classe all'area di progettazione delle classi. Viene visualizzata un forma della classe nel diagramma classi.  
  
4.  Espandere i dettagli della forma della classe e spostare il puntatore del mouse sui membri della classe. La descrizione comando visualizza la dichiarazione di ogni membro.  
  
5.  Fare clic sulla forma della classe e fare clic su **Dettagli classe**. È possibile visualizzare o modificare le proprietà del nuovo tipo nella finestra **Dettagli classe**.  
  
## <a name="see-alose"></a>Vedere anche
<xref:System.Nullable%601>   
[Tipi nullable](/dotnet/csharp/programming-guide/nullable-types/index)   
[Uso dei tipi nullable](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)   
[Procedura: Identificare un tipo nullable](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)   
[Tipi di valori nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)