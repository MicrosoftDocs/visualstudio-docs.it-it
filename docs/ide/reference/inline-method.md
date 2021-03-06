---
title: Metodo inline
description: Informazioni su come usare il menu azioni rapide e refactoring in Visual Studio per effettuare il refactoring delle dichiarazioni di metodi inline e fornire una sintassi più chiara.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 80313cf0dd9b828c9602fdf8ebff022342faa0fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852362"
---
# <a name="inline-method"></a>Metodo inline

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Refactoring del metodo inline. 

**Quando:** Si desidera sostituire gli utilizzi di un metodo statico, di istanza e di estensione all'interno di un singolo corpo dell'istruzione con un'opzione per rimuovere la dichiarazione del metodo originale.

**Motivo:**  Questo refactoring fornirà una sintassi più chiara.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sull'utilizzo del metodo.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare una delle opzioni seguenti: 
    
   Selezionare **Inline `<QualifiedMethodName>`** (NomeMetodo inline) per rimuovere la dichiarazione del metodo inline: 

    ![LinkedDataFormUpdated del menu azioni rapide e refactoring in Visual Studio con le modifiche apportate al codice in linea ' CreateWidget ()' selezionate e in C# visualizzate.](media/inline-method-remove-declaration.png)

   Selezionare **Inline and keep `<QualifiedMethodName>`** (NomeMetodo inline e mantieni) per mantenere la dichiarazione del metodo originale: 

    ![LinkedDataFormUpdated del menu azioni rapide e refactoring in Visual Studio con convert ' inline and Keep ' CreateWidget ()' selected and C# Code changes mostrate.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
