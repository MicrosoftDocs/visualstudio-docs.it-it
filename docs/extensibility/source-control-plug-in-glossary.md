---
title: Glossario di plug-in controllo dell'origine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b77cc0ea260ae86460de3c7a7752277a99291778
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-in-glossary"></a>Glossario di plug-in controllo di origine
I seguenti termini utili e le definizioni relative alla documentazione di SDK di plug-in controllo di origine.  
  
## <a name="definitions"></a>Definizioni  
 Archiviazione  
 Quando un utente apporta modifiche a una copia di lavoro, un utente deve inviare le modifiche dalla copia di lavoro nel repository del controllo del codice sorgente centrale. Crea una nuova revisione del file che è disponibile ad altri utenti. Questo processo viene chiamato un'archiviazione.  
  
 Estrazione  
 L'azione di richiesta di una copia di lavoro dal repository, indicante il repository dell'intenzione di modificarlo. Una copia di lavoro riflette lo stato del progetto al momento che è estratto.  
  
 Client  
 Un programma che utilizza il sistema di controllo del codice sorgente. Ai fini di questa documentazione, è l'IDE di Visual Studio.  
  
 Commento  
 Un messaggio che descrive le modifiche che è possibile collegare a una revisione quando viene eseguita un'operazione di controllo del codice sorgente.  
  
 Conflitto  
 Una situazione in cui due utenti tentano di verificare le modifiche apportate alla stessa area dello stesso file. In genere, è necessario eseguire un'operazione di unione.  
  
 Directory  
 Una cartella locale del client viene considerata come una directory. Questa è la copia in cui viene effettivamente modificato. Possono esistere molte copie di lavoro di un progetto specificato. in genere, ogni sviluppatore ha la propria copia.  
  
 Ottieni  
 Un'operazione get attiva la copia lavoro dell'utente aggiornata con la copia del repository. A differenza di estrazione, viene eseguito un'operazione get, quando l'utente richiede la copia più recente semplicemente ma intende non apportare alcuna modifica.  
  
 Cronologia  
 In genere è un riepilogo di tutte le estrazioni, archiviazioni, gli aggiornamenti, tag e le versioni eseguite nel repository del controllo del codice sorgente.  
  
 IDE  
 In genere si intende l'ambiente di sviluppo integrato di Visual Studio. Tuttavia, potrebbe anche fare riferimento ad altri ambienti di client che riconoscono l'API plug-in controllo di origine.  
  
 Merge  
 Processo durante l'origine di due o più file di codice vengono combinati per formare un nuovo file che include tutte le funzionalità del file precedente. Questo concetto è fondamentale nel controllo della versione in cui due o più sviluppatori lavorano file contemporaneamente.  
  
 Progetto  
 Una cartella di controllo del codice sorgente è noto anche come un progetto. Ciò non ha alcuna relazione con i progetti o soluzioni in Visual Studio.  
  
 Plug-in  
 Una DLL che fornisce controllo del codice sorgente implementando l'API plug-in controllo di origine.  
  
 Repository  
 La copia master in un controllo origine sistema archivia la cronologia delle revisioni completo del progetto. Ogni progetto dispone di esattamente un repository.  
  
 Revisione  
 Una modifica eseguito il commit nella cronologia di un file o set di file. Una revisione è uno snapshot in un progetto in continua evoluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)