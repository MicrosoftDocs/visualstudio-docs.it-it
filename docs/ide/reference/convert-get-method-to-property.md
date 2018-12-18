---
title: "Convertire il metodo Get in proprietà e convertire una proprietà in un metodo Get in Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 3d0a532e2e3e5bb8afa4a3c3dc9720134a1b7e8b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Refactoring per convertire il metodo Get in proprietà o una proprietà in metodo Get

Questi refactoring si applicano a:

- C#

## <a name="convert-get-method-to-property"></a>Convertire il metodo Get in proprietà

**Cosa:** consente di convertire un metodo Get in una proprietà (e facoltativamente il metodo Set) e viceversa.

**Quando:** si ha un metodo Get che non contiene alcuna logica.

### <a name="how-to"></a>Procedura

1. Posizionare il cursore nel nome del metodo Get.

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Sostituisci metodo con la proprietà** dal popup della finestra di anteprima.
   - **Mouse**
     - fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Sostituisci metodo con la proprietà** dal popup della finestra di anteprima.

1. (Facoltativo) Se si dispone di un metodo Set, è anche possibile convertire il metodo Set in questo momento selezionando **Sostituisci metodo Get e metodo Set con la proprietà**.

1. Se si è soddisfatti delle modifiche nell'anteprima del codice, premere **INVIO** o fare clic sulla correzione nel menu. Verrà eseguito il commit delle modifiche.

Esempio:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Convertire una proprietà in un metodo Get

**Cosa:** consente di convertire una proprietà in un metodo Get

**Quando:** è presente una proprietà con maggiori requisiti rispetto all'impostazione e al recupero immediati di un valore 

### <a name="how-to"></a>Procedura

1. Posizionare il cursore nel nome del metodo Get.

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
     - Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Sostituisci proprietà con metodi** dal popup della finestra di anteprima.
   - **Mouse**
     - fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Sostituisci proprietà con metodi** dal popup della finestra di anteprima.

1. Se si è soddisfatti delle modifiche nell'anteprima del codice, premere **INVIO** o fare clic sulla correzione nel menu. Verrà eseguito il commit delle modifiche.

## <a name="see-also"></a>Vedere anche

[Refactoring](../refactoring-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)