---
title: Frammenti di codice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 514408ff2dbbde12d243a1458c380a2e17b516cc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="code-snippets"></a>Frammenti di codice

I frammenti di codice sono piccoli blocchi di codice riutilizzabili che possono essere inseriti in un file di codice usando un comando di menu di scelta rapida o una combinazione di tasti di scelta rapida. In genere contengono blocchi di codice di uso comune, ad esempio blocchi `try-finally` o `if-else`, ma possono essere usati per inserire intere classi o metodi.

Sono disponibili frammenti di codice per una vasta gamma di linguaggi, tra cui C#, C++, Visual Basic, XML e T-SQL, per citarne alcuni. Per visualizzare tutti i frammenti installati disponibili per un linguaggio, aprire **Gestione frammenti di codice** dal menu **Strumenti** in Visual Studio e scegliere il linguaggio nel menu a discesa in alto.

![Finestra di dialogo Gestione frammenti di codice](media/code-snippets-manager.png)

I frammenti di codice sono accessibili nei modi generali seguenti:

- Nella barra dei menu scegliere **Modifica** > **IntelliSense** > **Inserisci frammento di codice**

- Dal menu di scelta rapida nell'editor del codice scegliere **Frammento** > **Inserisci frammento di codice**

- Dalla tastiera premere **CTRL**+**K**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Frammenti di espansione e frammenti Racchiudi tra

In Visual Studio sono disponibili due tipi di frammento di codice: frammenti di espansione, che vengono aggiunti in un punto di inserimento specificato e possono sostituire un collegamento al frammento, e frammenti Racchiudi tra (solo C# e C++), che vengono aggiunti a un blocco di codice selezionato.

Un esempio di un frammento di espansione: in C# viene usato il collegamento tryf per inserire un blocco try-finally:

```csharp
try
{

}
finally
{

}
```

Per inserire questo frammento di codice, scegliere **Inserisci frammento di codice** dal menu di scelta rapida della finestra del codice, quindi scegliere **Visual C#** e digitare `tryf` e infine premere **TAB**. In alternativa, è possibile digitare `tryf` e premere **TAB** due volte.

Un esempio di un frammento Racchiudi tra: in C++ il collegamento `if` può essere usato come frammento di inserimento o come frammento Racchiudi tra. Se si seleziona una riga di codice (ad esempio `return FALSE;`) e quindi si sceglie **Racchiudi tra** > **if**, il frammento viene espanso intorno alla riga:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametri di sostituzione del frammento

I frammenti di codice possono contenere parametri di sostituzione, cioè segnaposto che è necessario sostituire per adattare il codice preciso che si scrive. Nell'esempio precedente `true` è un parametro di sostituzione, che è possibile sostituire con la condizione appropriata. La sostituzione effettuata viene ripetuta per ogni istanza dello stesso parametro di sostituzione nel frammento.

Ad esempio, in Visual Basic è presente un frammento di codice che inserisce una proprietà. Per inserire il frammento di codice, scegliere **Frammento** > **Inserisci frammento di codice** dal menu di scelta rapida in un file di codice di Visual Basic. Scegliere quindi **Modelli di codice** > **Proprietà, procedure, eventi** > **Definisci una proprietà**.

![Menu del frammento di codice per Definisci una proprietà](media/code-snippets-vb-property.png)

Viene inserito il codice seguente:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Se si modifica `newPropertyValue` in `m_property`, tutte le istanze di `newPropertyValue` vengono modificate. Se si modifica `String` in `Int` nella dichiarazione di proprietà, anche il valore nel metodo set viene modificato in `Int`.

## <a name="see-also"></a>Vedere anche

[Procedura dettagliata: creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md)  
[Procedura: Distribuire frammenti di codice](../ide/how-to-distribute-code-snippets.md)  
[Procedure consigliate per l'uso dei frammenti di codice](../ide/best-practices-for-using-code-snippets.md)  
[Risoluzione dei problemi relativi ai frammenti di codice](../ide/troubleshooting-snippets.md)  
[Frammenti di codice C#](../ide/visual-csharp-code-snippets.md)  
[Frammenti di codice Visual C++](../ide/visual-cpp-code-snippets.md)  
[Informazioni di riferimento sullo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)