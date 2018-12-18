---
title: MSSCCPRJ. File SCC | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef076a93d27cc2c133404d6fe6463d32cb449956
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. File SCC
Quando una soluzione di Visual Studio o il progetto viene inserito nel controllo del codice sorgente utilizzando l'IDE, l'IDE riceve due tipi principali di informazioni dal plug-in sotto forma di stringhe di controllo del codice sorgente. Queste stringhe "AuxPath" e "ProjName", sono opache all'IDE, ma il plug-in vengono utilizzati per individuare la soluzione o il progetto nel controllo della versione. L'IDE in genere Ottiene queste stringhe la prima volta, chiamando il [SccGetProjPath](../extensibility/sccgetprojpath-function.md), e quindi li salva nel file di soluzione o il progetto per le future chiamate per il [SccOpenProject](../extensibility/sccopenproject-function.md). Quando incorporati nei file di soluzione e progetto, le stringhe "AuxPath" e "ProjName" non vengono aggiornate automaticamente quando un utente con diramazioni fork, o copia i file di soluzione e progetto presenti nel controllo della versione. Per assicurarsi che i file di soluzione e progetto puntino nella posizione corretta nel controllo della versione, gli utenti devono aggiornare manualmente le stringhe. Poiché le stringhe devono essere opaca, potrebbe non sempre essere chiaro come devono essere aggiornati.  
  
 Il plug-in controllo del codice sorgente è possibile evitare questo problema archiviando le stringhe "AuxPath" e "ProjName" in un file speciale denominato il MSSCCPRJ. File SCC. È un file locale e sul lato client che è di proprietà e mediante il plug-in. Questo file non viene mai inserito nel controllo del codice sorgente, ma non viene generato il plug-in per ogni directory che contiene i file di controllo del codice sorgente. Per determinare quali file sono file di soluzione e progetto di Visual Studio, un plug-in controllo del codice sorgente possibile confrontare le estensioni di file in un elenco standard o fornito dall'utente. Una volta l'IDE rileva che un plug-in supporta il MSSCCPRJ. File SCC, cessa di incorporare "AuxPath" e "ProjName" stringhe nella soluzione e file di progetto, quindi legge tali stringhe dal MSSCCPRJ. File SCC.  
  
 Un controllo del codice sorgente plug-in che supporta il MSSCCPRJ. File SCC deve rispettare le linee guida seguenti:  
  
-   Può esistere solo un MSSCCPRJ. File di controllo del codice sorgente per ogni directory.  
  
-   Un MSSCCPRJ. File SCC può contenere il "AuxPath" e "ProjName" per più file sottoposti al controllo del codice sorgente all'interno di una determinata directory.  
  
-   La stringa "AuxPath" non deve disporre delle virgolette all'interno. È consentito avere virgolette come delimitatori (ad esempio, una coppia di virgolette doppie consente di indicare una stringa vuota). Quando viene letto dal MSSCCPRJ, l'IDE rimuoverà tutte le offerte dalla stringa "AuxPath". File SCC.  
  
-   La stringa "ProjName" nel MSSCCPRJ. File SCC deve corrispondere esattamente alla stringa restituita dal `SccGetProjPath` (funzione). Se la stringa restituita dalla funzione dispone di virgolette, la stringa di MSSCCPRJ. File SCC deve disporre delle virgolette intorno a esso e viceversa.  
  
-   Un MSSCCPRJ. File SCC viene creata o aggiornata ogni volta che un file viene inserito nel controllo del codice sorgente.  
  
-   Se un MSSCCPRJ. File SCC eliminato, un provider deve rigenerare, la volta successiva che viene eseguita un'operazione di controllo di origine relativi a tale directory.  
  
-   Un MSSCCPRJ. File SCC deve seguire il formato definito.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Un'illustrazione del MSSCCPRJ. Formato di File di controllo del codice sorgente  
 Di seguito è un esempio di MSSCCPRJ. Formato di file di controllo del codice sorgente (i numeri di riga vengono forniti solo come guida e non devono essere incluso nel corpo del file):  
  
 [Riga 1] `SCC = This is a Source Code Control file`  
  
 [Riga 2]  
  
 [Riga 3] `[TestApp.sln]`  
  
 [Riga 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Riga 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Riga 6]  
  
 [Riga 7] `[TestApp.csproj]`  
  
 [Riga 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Riga 9] `SCC_Project_Name = "$/TestApp"`  
  
 La prima riga indica lo scopo del file e viene utilizzato come la firma per tutti i file di questo tipo. Questa riga dovrebbe essere visualizzato esattamente come in MSSCCPRJ tutti. File SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Di seguito è disponibile una sezione di impostazioni per ogni file, contrassegnati con il nome del file tra parentesi quadre. In questa sezione viene ripetuta per ogni file monitorati. Questa riga è riportato un esempio di un nome di file, vale a dire, `[TestApp.csproj]`. L'IDE prevede che le due righe seguenti. Non, tuttavia, definisce lo stile dei valori definiti. Le variabili sono `SCC_Aux_Path` e `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Non è disponibile alcun delimitatore di fine di questa sezione. Il nome del file, nonché tutti i valori letterali che vengono visualizzati nel file sono definiti nel file di intestazione scc.h. Per ulteriori informazioni, vedere [stringhe utilizzate come chiavi per la ricerca di un plug-in controllo origine](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)