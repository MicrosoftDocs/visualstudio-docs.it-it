---
title: Trovare codice con i comandi Vai a | Microsoft Docs
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9309a143760aab5b59355b4cea6cd214aaa49812
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="find-code-using-go-to-commands"></a>Trovare codice con i comandi Vai a  
I comandi **Vai a** di Visual Studio consentono di eseguire una ricerca mirata nel codice allo scopo di individuare rapidamente elementi specifici. Da una semplice interfaccia unificata è possibile passare a una riga, a un tipo, a un simbolo o a un file specifico e ad altro ancora. Questa funzionalità esiste in Visual Studio 2017 e versioni successive.  

### <a name="how-to-use-it"></a>Come usare la funzionalità  

Input        | Funzione 
------------ | ---
**Tastiera** | Premere **Ctrl + t** o **Ctrl +,**     
**Mouse**    | Selezionare **Modifica**, **Vai a**, **Vai a tutti**  

Per impostazione predefinita, nell'editor di codice verrà visualizzata una piccola finestra in alto a destra.  

![Vai a tutti](media/gotoall.png)

Durante la digitazione nella casella di testo i risultati vengono visualizzati in un elenco a discesa sotto la casella di testo stessa. Per passare a un elemento, selezionarlo nell'elenco.    

![Finestra Passa a](../ide/media/vside_navigatetowindow.png "Finestra Passa a")  

È anche possibile immettere un punto interrogativo (?) per ottenere informazioni aggiuntive.  

  ![Guida di Vai a tutti](media/gotoall_help.png)

### <a name="filtered-searches"></a>Ricerche con filtri  
Per impostazione predefinita, l'elemento specificato viene cercato in tutti gli elementi della soluzione. È però possibile limitare la ricerca nel codice a tipi di elementi specifici anteponendo determinati caratteri di prefisso ai termini di ricerca. È anche possibile modificare rapidamente il filtro di ricerca scegliendo i pulsanti sulla barra degli strumenti della finestra di dialogo Vai a. I pulsanti per la modifica dei filtri relativi al tipo si trovano sul lato sinistro, mentre quelli per la modifica dell'ambito della ricerca sono sul lato destro.  

![Passare a membri](../ide/media/vside_navigation_toolbar.png)

#### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrare in base a un tipo specifico di elemento di codice  
Per limitare la ricerca a un tipo specifico di elemento di codice, è possibile specificare un prefisso nella casella di ricerca o selezionare una delle cinque icone di filtro:  

Prefisso | Icona | Metodo rapido | Descrizione
:----: | ---- | -------- | ---
\#      | ![Icona Simbolo](media/gotoall_symbolicon.png) | CTRL+1, CTRL+S | Consente di passare al simbolo specificato
f      | ![Icona File](media/gotoall_fileicon.png)     | CTRL+1, CTRL+F | Consente di passare al file specificato
m      | ![Icona del membro](media/gotoall_membericon.png) | CTRL+1, CTRL+M | Consente di passare al membro specificato
t      | ![Icona Tipo](media/gotoall_typeicon.png)     | CTRL+1, CTRL+T | Consente di passare al tipo specificato
:      | ![Icona Riga](media/gotoall_lineicon.png)     | CTRL+G         | Consente di passare al numero di riga specificato

#### <a name="filter-to-a-specific-location"></a>Filtrare in base a una posizione specifica    
Per limitare la ricerca a una posizione specifica, selezionare una delle due icone documento:  

Icona | Descrizione
---- | ---
![Documento corrente](media/gotoall_currentdocument.png) | Cerca solo il documento corrente
![Documenti esterni](media/gotoall_external.png) | Cerca i documenti esterni oltre a quelli presenti nel progetto e/o nella soluzione  

### <a name="camel-casing"></a>Notazione Camel  
Se si usa la [notazione Camel](https://en.wikipedia.org/wiki/Camel_case) nel codice, è possibile trovare gli elementi di codice più rapidamente immettendo solo le lettere maiuscole dei nomi degli elementi di codice. Ad esempio, se nel codice è presente un tipo denominato `CredentialViewModel`, è possibile restringere la ricerca scegliendo il filtro Tipo ("t") e quindi immettendo solo le lettere maiuscole del nome (`CVM`) nella finestra di dialogo Vai a. Questa funzionalità può essere utile se il codice contiene nomi lunghi.  

![Finestra Passa a - ricerca con lettere maiuscole](../ide/media/vside_capitalsearch.png)

### <a name="settings"></a>Impostazioni  
Se si seleziona l'icona a forma di ingranaggio ![Icona Ingranaggio](media/gotoall_gear.png) è possibile modificare il comportamento di questa funzionalità:  

Impostazione | Descrizione
------- | ---
Utilizza scheda anteprima | Visualizza immediatamente l'elemento selezionato nella scheda anteprima dell'IDE
Mostra dettagli    | Visualizza informazioni relative a progetto, file, riga e riepilogo recuperando i commenti della documentazione nella finestra
Centra la finestra   | Sposta la finestra al centro della parte superiore dell'editor di codice anziché in alto a destra   

## <a name="see-also"></a>Vedere anche  
[Esplorazione del codice](../ide/navigating-code.md)  
[Vai a definizione e Visualizza definizione](../ide/go-to-and-peek-definition.md)  