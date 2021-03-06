---
description: Questa finestra di dialogo di avviso viene visualizzata quando si usa il server di origine.
title: 'Avviso di sicurezza: il debugger deve eseguire un comando non attendibile | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1ca71db31fc976a2bc3c652929fd9215f2f3123f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166658"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Avviso di sicurezza: il debugger deve eseguire un comando non attendibile
Questa finestra di dialogo di avviso viene visualizzata quando si usa il server di origine. Indica che il comando che deve essere eseguito dal debugger per ottenere il codice sorgente non è incluso nell'elenco dei comandi attendibili per il server di origine contenuto nel file srcsvr.ini. Se il comando è valido, è possibile aggiungerlo al file srcsvr.ini. In caso contrario, è opportuno non eseguirlo. Per altre informazioni, vedere [specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Testo del messaggio
 **Il debugger deve eseguire il seguente comando non attendibile per ottenere il codice sorgente dal server di origine.**

 **Se il file del simbolo di debug (\*.pdb) non proviene da un'origine conosciuta e attendibile, questo comando potrebbe essere non valido o pericoloso da eseguire.**

 **Eseguire il comando?**

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 Comando della casella di testo dal file con estensione PDB da eseguire.

 Eseguire Consenti l'esecuzione del comando.

 Non eseguire l'arresto dell'esecuzione del comando e il download del file dal server di origine.

## <a name="see-also"></a>Vedi anche
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Server di origine](/windows/desktop/Debug/source-server-and-source-indexing)
