---
title: Esplorazione di connessioni di SharePoint tramite Esplora Server | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5ea474f2439b6da519563f08ffe4ddc2f6dcef30
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="browsing-sharepoint-connections-using-server-explorer"></a>Esplorazione di connessioni di SharePoint tramite Esplora server
  È ora possibile esplorare le connessioni di SharePoint locali in **Esplora Server**. Utilizzando questa tecnica, è possibile navigare attraverso i componenti di un sito di SharePoint nel sistema. Componenti del sito di SharePoint, ad esempio le definizioni di elenco e tipi di contenuto, vengono visualizzati in un nodo denominato **connessioni di SharePoint** nella visualizzazione struttura ad albero del **Esplora Server**. Per visualizzare **Esplora Server**, sulla barra dei menu, scegliere **vista**, **Esplora Server**. Oltre a visualizzare i componenti del sito di SharePoint, è possibile rimuovere gli elementi, visualizzare le relative proprietà o aggiornare la visualizzazione albero usando i comandi del menu di scelta rapida.  
  
> [!IMPORTANT]  
>  Per esplorare un sito di SharePoint, è necessario essere un amministratore della raccolta siti di SharePoint ed eseguire Visual Studio come amministratore del computer locale. In caso contrario, il sito verrà visualizzato **Esplora Server**, ma non è possibile espandere il nodo. Per verificare se si è un amministratore della raccolta siti, aprire il sito in un web browser, aprire il **Azioni sito** menu, scegliere **autorizzazioni sito**e quindi scegliere il **autorizzazioni: Team Sito** pagina, scegliere il **Amministratori raccolta siti** comando il **Gestisci** gruppo sulla barra multifunzione. Il nome verrà visualizzato nella casella di testo se sei un amministratore della raccolta siti. Se il **Amministratori raccolta siti** comando non viene visualizzato nel gruppo di gestione sulla barra multifunzione e non si è un amministratore per la raccolta siti, è necessario ottenere le autorizzazioni appropriate dall'amministratore del sito.  
  
## <a name="server-explorer-nodes"></a>Nodi di Esplora server  
 Ogni componente di un sito di SharePoint è rappresentato da un nodo di **Esplora Server** visualizzazione nella struttura ad albero **connessioni di SharePoint**. Ad esempio, siti di SharePoint predefiniti includono un tipo di contenuto definito discussione che rappresenta un tipo di discussione che visualizza il **discussioni** pagina del sito di SharePoint. Il tipo di contenuto discussione contiene diversi campi. Per visualizzare questi campi in **Esplora Server**, espandere il **tipi contenuto** nodo, quindi il **discussione** nodo. In sono diversi nodi campo, ad esempio titolo, descrizione soggetto e corpo.  
  
## <a name="node-shortcut-menu-commands"></a>Comandi di Menu di scelta rapida nodo  
 Ogni nodo dispone di un menu di scelta rapida a cui è possibile accedere facendo clic con il pulsante destro del mouse sul nodo o scegliendolo e quindi premendo i tasti MAIUSC+F10. Comandi dei nodi possono includere quanto segue:  
  
|Nome comando|Descrizione|  
|------------------|-----------------|  
|Aggiorna|Aggiorna la visualizzazione albero per visualizzare eventuali modifiche che possono essersi verificati dall'ultima volta che è stato visualizzato il nodo.|  
|Eliminare|Rimuove il nodo selezionato nella visualizzazione ad albero. **Nota:** questo comando è abilitato solo per connessioni di SharePoint elencate sotto la **connessioni di SharePoint** nodo.|  
|Proprietà|Visualizza le proprietà disponibili per il nodo selezionato nel **proprietà** finestra. Le proprietà sono di sola lettura e non a ogni nodo dispone di proprietà associate.|  
|Aggiungi connessione|Consente di specificare un sito di SharePoint che si desidera visualizzare. Disponibile nel **connessioni di SharePoint** nodo e nodi di sito secondario.|  
|Visualizza nel browser|Visualizza l'elenco selezionato nel Web browser. Questo comando è disponibile in alcuni elenchi in corrispondenza di **Elenca** nodo contenute in **elenchi e raccolte**.|  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Aggiungere o rimuovere connessioni di SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Vengono descritti i passaggi necessari per l'aggiunta di un nuovo sito di SharePoint per il **connessioni di SharePoint** nodo **Esplora Server**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  