---
title: Nessuna origine disponibile | Microsoft Docs
description: Informazioni sulle operazioni che è possibile eseguire quando il progetto non dispone di codice sorgente per il codice che si desidera visualizzare.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9993c4482d20393a3ca46d9afcd0a8ec1b13f65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942035"
---
# <a name="no-source-available"></a>Nessuna origine disponibile
Il progetto non contiene codice sorgente per il codice che si tenta di visualizzare. Questa condizione si verifica, di solito, quando si fa doppio clic su un modulo per il quale non è disponibile codice sorgente nella finestra **Stack di chiamate** o **Thread**. È possibile continuare il debug, ma non è possibile utilizzare la finestra di origine per impostare i punti di interruzione ed eseguire altre operazioni in questa posizione. Per impostare un punto di interruzione, utilizzare invece la finestra **Disassembly**.

 Nelle pagine delle proprietà della soluzione è possibile modificare le directory in cui il debugger cerca i file di origine e indicare al debugger di ignorare determinati file di origine. Vedere [eseguire il debug di file di origine, proprietà comuni, finestra di dialogo Pagine delle proprietà della soluzione](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Sfoglia per trovare il codice sorgente** Fare clic su questo collegamento per aprire una finestra di dialogo in cui è possibile cercare il codice sorgente.

 **Mostra disassembly** Avvia la **finestra Disassembly**.

 **Mostra sempre Disassembly per i file di origine mancanti** Selezionare questa opzione per visualizzare automaticamente la **finestra Disassembly** quando non è disponibile alcuna origine. È anche possibile modificare questa impostazione nella finestra di dialogo **Opzioni**, categoria **Debug**, pagina **Generale**, selezionando o deselezionando **Mostra disassembly se l'origine non è disponibile**.

## <a name="see-also"></a>Vedi anche
- [File di origine di debug, proprietà comuni, finestra di dialogo Pagine delle proprietà della soluzione](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (estensione del debugger SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)