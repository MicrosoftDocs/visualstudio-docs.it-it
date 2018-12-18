---
title: "Pagine delle proprietà delle impostazioni per i progetti Web | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4e58541c5ab0c7a38773740343349880aa5297e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="property-pages-settings-for-web-projects"></a>Impostazioni delle pagine delle proprietà per i progetti Web
È possibile modificare le impostazioni delle proprietà per una configurazione di debug nel sito web di **pagine delle proprietà** la finestra di dialogo, come descritto in [configurazioni Debug e Release](../debugger/how-to-set-debug-and-release-configurations.md). Le tabelle seguenti illustrano la posizione in cui sono disponibili le impostazioni correlate al debugger il **pagine delle proprietà** la finestra di dialogo.  
  
### <a name="configuration-properties-folder-start-options-category"></a>Cartella Proprietà di configurazione (categoria Opzioni di avvio)  
  
|**Impostazione**|**Descrizione**|  
|-----------------|---------------------|  
|**Azione di avvio**|Intestazione sotto la quale sono raggruppate le opzioni correlate all'avvio dell'applicazione.|  
|**Utilizzare la pagina corrente**|Specifica la pagina corrente come punto di avvio per il debug.|  
|**Pagina specifica:**|Specifica la pagina Web da cui iniziare la procedura di debug.|  
|**Avvia programma esterno:**|Specifica il comando per l'avvio del programma da sottoporre a debug.|  
|**Argomenti della riga di comando:**|Specifica gli argomenti relativi al comando riportato sopra.|  
|**Directory di lavoro:**|Specifica la cartella di lavoro del programma sottoposto a debug. In [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] la cartella di lavoro è la cartella dalla quale viene avviata l'applicazione, che per impostazione predefinita è \bin\debug.|  
|**Avvia URL**|Specifica la posizione dell'applicazione Web da sottoporre a debug.|  
|**Non aprire una pagina. Attendi una richiesta da un'applicazione esterna**|Specifica di attendere una richiesta da un'applicazione esterna. Questa opzione non avvia Internet Explorer né altre applicazioni. Esegue semplicemente le operazioni di preparazione necessarie per eseguire il debug su richiesta di un'applicazione.|  
|**Server**|Intestazione sotto la quale sono raggruppate le opzioni correlate al server da utilizzare.|  
|**Usa server Web predefinito**|Specifica di utilizzare il server Web predefinito.|  
|**Usa server personalizzato**|Consente di immettere l'URL di base da utilizzare come server.|  
|**Debugger**|Intestazione sotto la quale sono raggruppate le opzioni correlate al tipo di debug da eseguire.|  
|**Il debug di ASP.NET**|Attiva il debug di pagine ASP scritte per la piattaforma di sviluppo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. È necessario specificare un URL in **Avvia URL**.|  
|**Debug del codice nativo**|Consente di eseguire il debug delle chiamate al codice Win32 nativo (non gestito) dall'applicazione gestita in uso.|  
|**Debug di SQL Server**|Consente di eseguire il debug di oggetti di database di SQL Server.|  
|**Debug di Silverlight**|Consente di eseguire il debug dei componenti di Silverlight.|  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)